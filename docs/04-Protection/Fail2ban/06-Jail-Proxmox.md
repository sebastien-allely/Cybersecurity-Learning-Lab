# Jail Proxmox VE


| Élément | Valeur |
| **Nom du document** | `06-Jail-Proxmox.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Protection |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |




## Objectif

Cette documentation décrit la mise en œuvre d'une jail Fail2ban dédiée à Proxmox VE.

L'objectif est de détecter les tentatives répétées d'authentification sur l'interface d'administration et l'API Proxmox, puis de bannir automatiquement les adresses IP malveillantes.

Cette protection vient compléter les mesures de durcissement déjà mises en œuvre sur les nœuds Proxmox VE et permet de limiter les attaques par force brute ciblant les comptes d'administration.

> 🛡️ **Sécurité**
>
> Une jail Fail2ban ne remplace jamais une authentification forte ni une politique de mots de passe robuste. Elle constitue une couche de protection supplémentaire.


## Principe de fonctionnement

Contrairement à SSH, Proxmox VE s'appuie sur plusieurs services internes pour gérer les authentifications.

Lors d'une tentative de connexion, les événements sont enregistrés dans les journaux système par le service `pvedaemon`.

Fail2ban analyse ces journaux via le backend `systemd`. Lorsqu'un nombre défini d'échecs est détecté pour une même adresse IP, cette dernière est automatiquement bannie pendant la durée configurée.

Le fonctionnement repose sur trois éléments :

* un filtre (`filter.d/proxmox.conf`) chargé de reconnaître les événements d'authentification ;
* une jail (`jail.local`) qui applique la politique de bannissement ;
* le pare-feu (`nftables`) qui bloque effectivement les connexions de l'adresse IP concernée.


## Identification des journaux

Avant de créer un filtre Fail2ban, il est indispensable d'identifier précisément les journaux produits par le service à protéger.

Dans le cas de Proxmox VE, les événements d'authentification sont consultables avec :

```bash
journalctl -u pvedaemon
```

ou plus généralement :

```bash
journalctl | grep "authentication failure"
```

Ces commandes permettent d'observer le format exact des messages générés par Proxmox VE.

Le filtre Fail2ban sera construit à partir de ces événements réels, et non à partir d'exemples théoriques.

> 💬 **Retour d'expérience**
>
> Les expressions régulières utilisées dans cette documentation ont été élaborées à partir des journaux réellement observés sur le Cybersecurity Learning Lab puis validées avec `fail2ban-regex`.


## Création du filtre Proxmox

Avant de créer la jail, il est nécessaire de créer le filtre qui permettra à Fail2ban d'identifier précisément les tentatives d'authentification échouées.

Les filtres Fail2ban sont stockés dans :

```bash
/etc/fail2ban/filter.d/
```

Le filtre Proxmox sera créé dans :

```bash
/etc/fail2ban/filter.d/proxmox.conf
```

Création du fichier :

```bash
sudo vim /etc/fail2ban/filter.d/proxmox.conf
```

Contenu du filtre :

```ini
[Definition]

failregex = ^.*authentication failure;.*rhost=<HOST>.*$

ignoreregex =
```

---

## Explication du filtre

Le filtre repose sur l'analyse des messages générés par Proxmox lors d'un échec d'authentification.

Exemple d'événement détecté :

```text
pvedaemon[1208]: authentication failure; rhost=::ffff:192.168.1.8 user=user@pam msg=no such user ('user@pam')
```

L'expression :

```regex
authentication failure;.*rhost=<HOST>
```

permet de récupérer :

* l'événement d'échec d'authentification ;
* l'adresse IP distante ;
* l'adresse IP à transmettre au mécanisme de bannissement.

La variable :

```text
<HOST>
```

est automatiquement remplacée par Fail2ban afin d'identifier l'adresse IP source.

> 💡 **Bonne pratique**
>
> Un filtre Fail2ban doit être construit à partir des journaux réellement générés par le système cible. Une expression trop large peut provoquer des faux positifs, tandis qu'une expression trop restrictive peut laisser passer des attaques.

> ⚠️ **Point d'attention**
>
> Les journaux Proxmox peuvent contenir des adresses IPv4 encapsulées dans IPv6 (`::ffff:x.x.x.x`). Le filtre doit donc être testé avec des événements réels avant mise en production.


## Création de la jail Proxmox

Une fois le filtre créé et validé, il faut déclarer une jail qui utilisera ce filtre.

La configuration des jails est réalisée dans :

```bash
/etc/fail2ban/jail.local
```

Ajouter la section suivante :

```ini
[proxmox]

enabled  = true
filter   = proxmox
backend  = systemd

port     = https,http,8006

maxretry = 3
findtime = 2d
bantime  = 1h
```

---

## Explication de la configuration

### Activation de la jail

```ini
enabled = true
```

Active la protection Proxmox.

Une jail présente dans `jail.local` mais désactivée ne sera pas chargée par Fail2ban.

---

### Association du filtre

```ini
filter = proxmox
```

Cette directive indique à Fail2ban d'utiliser le fichier :

```text
/etc/fail2ban/filter.d/proxmox.conf
```

Le nom du filtre correspond au nom du fichier sans l'extension `.conf`.

---

### Backend de journalisation

```ini
backend = systemd
```

Le backend `systemd` permet à Fail2ban d'utiliser directement les journaux gérés par `systemd-journald`.

Cette méthode est adaptée aux versions modernes de Proxmox VE.

Avantages :

* pas de dépendance à un chemin de fichier de log ;
* meilleure compatibilité avec les distributions récentes ;
* prise en compte des rotations de journaux.

---

### Ports protégés

```ini
port = https,http,8006
```

Le port principal d'administration Proxmox est :

```text
8006/TCP
```

Les ports HTTP et HTTPS sont également indiqués afin de couvrir les services web associés.

> 🛡️ **Sécurité**
>
> Dans un environnement exposé sur Internet, la priorité est de protéger les services accessibles depuis l'extérieur. Une interface Proxmox directement exposée doit rester une exception et être accompagnée de mesures complémentaires : filtrage réseau, VPN, authentification forte et restrictions d'accès.

---

### Nombre de tentatives

```ini
maxretry = 3
```

Après trois échecs d'authentification dans la fenêtre définie par `findtime`, l'adresse IP est bannie.

Le choix de trois tentatives permet de bloquer rapidement une attaque automatisée tout en limitant le risque de bloquer un administrateur ayant commis une erreur ponctuelle.

---

### Fenêtre d'analyse

```ini
findtime = 2d
```

Cette valeur définit la période pendant laquelle les échecs sont comptabilisés.

Une attaque lente utilisant des tentatives espacées reste donc détectable.

> ⚠️ **Point d'attention**
>
> Une fenêtre trop courte peut laisser passer des attaques automatisées lentes. Une fenêtre trop longue augmente le risque de faux positifs selon le contexte d'exploitation.

---

### Durée du bannissement

```ini
bantime = 1h
```

L'adresse IP est bloquée pendant une heure.

Ce choix représente un compromis :

* suffisamment long pour interrompre une attaque automatisée ;
* suffisamment court pour permettre à un administrateur légitime de reprendre la main rapidement.

Un bannissement permanent peut sembler plus sécurisé, mais présente un risque opérationnel important en cas d'erreur d'un administrateur.

---

> 💬 **Retour d'expérience**
>
> Dans un environnement d'administration interne, un bannissement temporaire est généralement préférable à un bannissement définitif. L'objectif de Fail2ban est de ralentir et interrompre une attaque, pas de créer une situation où l'exploitation devient impossible.


## Validation de la jail Proxmox

Après modification du fichier `jail.local`, il est nécessaire de redémarrer Fail2ban afin de prendre en compte la nouvelle configuration.

---

## Vérification de la configuration

Avant tout redémarrage, il est recommandé de vérifier la configuration générée par Fail2ban :

```bash
fail2ban-client -d
```

Cette commande affiche la configuration chargée par Fail2ban.

Elle permet notamment de vérifier :

* que la jail `proxmox` est bien déclarée ;
* que le filtre utilisé est correct ;
* que le backend `systemd` est pris en compte ;
* qu'aucune erreur de syntaxe n'empêche le chargement.

> 💡 **Bonne pratique**
>
> Toujours vérifier la configuration avant un redémarrage d'un service de sécurité. Une erreur de syntaxe peut empêcher le chargement complet des protections existantes.

---

## Redémarrage du service

Appliquer la nouvelle configuration :

```bash
sudo systemctl restart fail2ban
```

Vérifier l'état du service :

```bash
sudo systemctl status fail2ban
```

Le service doit apparaître comme actif :

```text
Active: active (running)
```

---

## Vérification des jails chargées

Afficher la liste des protections actives :

```bash
fail2ban-client status
```

La jail Proxmox doit apparaître dans la liste :

```text
Jail list:
sshd, proxmox
```

Afficher les informations détaillées :

```bash
fail2ban-client status proxmox
```

Exemple attendu :

```text
Status for the jail: proxmox

|- Filter
|  |- Currently failed: 0
|  |- Total failed: 0
|
|- Actions
   |- Currently banned: 0
   |- Total banned: 0
```

---

## Validation du filtre

Avant de réaliser un test réel, vérifier que le filtre détecte correctement les événements :

```bash
fail2ban-regex /tmp/proxmox-auth.log /etc/fail2ban/filter.d/proxmox.conf
```

Résultat attendu :

```text
Failregex: 3 total

3 matched
0 missed
```

Cette étape confirme que l'expression régulière correspond bien aux événements produits par Proxmox.

> 🧪 **Test**
>
> Un filtre Fail2ban doit toujours être validé avec `fail2ban-regex` avant son activation. Cela évite de déployer une protection qui ne détecterait aucun événement réel.


## Simulation d'une tentative d'authentification échouée

La validation finale consiste à générer volontairement plusieurs échecs d'authentification afin de vérifier que Fail2ban détecte l'événement et applique le bannissement.

Dans un environnement de laboratoire, cette étape permet de valider l'ensemble de la chaîne :

```text
Tentative de connexion Proxmox
            ↓
Journal système pvedaemon
            ↓
Filtre Fail2ban proxmox.conf
            ↓
Détection du seuil maxretry
            ↓
Ajout de l'adresse IP dans nftables
            ↓
Blocage de la source
```

---

## Génération des événements de test

Depuis une machine cliente autorisée à réaliser le test, effectuer plusieurs tentatives de connexion avec un identifiant volontairement incorrect sur l'interface Proxmox.

Exemple :

```text
Utilisateur :
user@pam

Mot de passe :
motdepasse_incorrect
```

Répéter l'opération jusqu'au dépassement du seuil configuré :

```ini
maxretry = 3
```

---

## Vérification des journaux Proxmox

Vérifier que les événements sont bien générés :

```bash
journalctl -u pvedaemon --since "5 minutes ago"
```

Un événement similaire doit apparaître :

```text
pvedaemon[xxxx]: authentication failure; rhost=::ffff:192.168.1.xxx user=user@pam msg=no such user
```

L'adresse IP source doit correspondre à la machine ayant réalisé le test.

---

## Vérification du bannissement

Consulter l'état de la jail :

```bash
fail2ban-client status proxmox
```

Résultat attendu :

```text
|- Currently banned: 1
|- Total banned: 1

Banned IP list:
192.168.1.xxx
```

L'adresse IP apparaît alors dans la liste des sources bloquées.

---

## Vérification côté pare-feu

Fail2ban utilise `nftables` pour appliquer le blocage.

Vérifier les règles créées :

```bash
sudo nft list ruleset | grep f2b
```

La présence d'un élément correspondant à Fail2ban confirme que le mécanisme de blocage réseau est actif.

---

## Consultation des logs Fail2ban

Les actions réalisées par Fail2ban sont enregistrées dans :

```bash
/var/log/fail2ban.log
```

Consultation en temps réel :

```bash
tail -f /var/log/fail2ban.log
```

Exemple :

```text
NOTICE [proxmox] Ban 192.168.1.xxx
```

---

> 🧪 **Test**
>
> La validation ne consiste pas uniquement à vérifier que Fail2ban détecte l'erreur. Il faut confirmer toute la chaîne de protection : détection, décision de bannissement et application du blocage réseau.

> 💬 **Retour d'expérience**
>
> Lors des tests réalisés dans le Cybersecurity Learning Lab, le filtre Proxmox a été validé avec `fail2ban-regex` avant d'être intégré dans la jail finale. Cette méthode réduit le risque de déployer une protection inefficace.


## Exploitation de la jail Proxmox

Une fois la jail active, l'administrateur doit être capable de consulter son état, d'identifier les blocages et d'effectuer les actions nécessaires au maintien en condition opérationnelle.

---

## Consulter l'état de la jail

Afficher les informations générales :

```bash
fail2ban-client status proxmox
```

Cette commande permet de connaître :

* le nombre d'échecs détectés ;
* le nombre total de bannissements ;
* les adresses actuellement bloquées.

Exemple :

```text
Status for the jail: proxmox

|- Filter
|  |- Currently failed: 0
|  |- Total failed: 3
|
|- Actions
   |- Currently banned: 1
   |- Total banned: 1

Banned IP list:
192.168.1.xxx
```

---

## Débannir une adresse IP

Une erreur d'administration peut provoquer un bannissement légitime.

Par exemple :

* saisie répétée d'un mauvais mot de passe ;
* utilisation d'un ancien compte ;
* mauvaise configuration d'un outil d'administration.

Pour retirer une adresse IP du bannissement :

```bash
fail2ban-client set proxmox unbanip <IP_A_DEBANNIR>
```

Exemple :

```bash
fail2ban-client set proxmox unbanip 192.168.1.xxx
```

> 🔧 **Exploitation**
>
> Le débannissement doit rester une action exceptionnelle. Si une même adresse est régulièrement bannie, il faut rechercher la cause racine plutôt que multiplier les exclusions.

---

## Vérifier les événements Fail2ban

Les journaux Fail2ban permettent de comprendre pourquoi une adresse a été bannie.

Consulter les derniers événements :

```bash
journalctl -u fail2ban --since "30 minutes ago"
```

Ou suivre les événements en temps réel :

```bash
journalctl -u fail2ban -f
```

Exemples d'événements :

```text
[proxmox] Ban 192.168.1.xxx
```

ou :

```text
[proxmox] Unban 192.168.1.xxx
```

---

## Gestion des faux positifs

Un faux positif correspond à un blocage d'une source légitime.

Avant d'ajouter une adresse dans `ignoreip`, il est nécessaire d'analyser :

* pourquoi les authentifications échouent ;
* si un compte ou un service utilise de mauvais identifiants ;
* si une tentative inhabituelle est réellement légitime.

Une exclusion permanente ne doit jamais être utilisée comme première réponse.

> ⚠️ **Point d'attention**
>
> Ajouter trop d'adresses dans `ignoreip` réduit progressivement l'efficacité de Fail2ban. Une adresse autorisée par erreur pourra continuer à effectuer des tentatives sans être bloquée.

---

## Nettoyage après les tests

Les tests réalisés pendant la mise en œuvre peuvent générer des éléments temporaires.

Avant de considérer la configuration comme terminée, supprimer :

* les fichiers de filtres de test ;
* les journaux de simulation ;
* les configurations temporaires.

Exemples :

Supprimer un filtre de test :

```bash
sudo rm /etc/fail2ban/filter.d/test-proxmox.conf
```

Supprimer un journal temporaire :

```bash
rm /tmp/proxmox-auth.log
```

Vérifier ensuite que seuls les éléments nécessaires restent présents.

> 🛡️ **Sécurité**
>
> Les fichiers temporaires utilisés pour les tests peuvent contenir des informations techniques sur l'environnement. Leur suppression limite l'exposition inutile d'informations et réduit la surface de maintenance.


## Limites de la protection Fail2ban sur Proxmox VE

Fail2ban apporte une protection efficace contre les attaques automatisées par force brute, mais il ne constitue pas une solution de sécurité complète.

Il est important de comprendre ses limites afin de l'intégrer correctement dans une stratégie de défense en profondeur.

---

## Fail2ban ne protège que les événements détectables

Fail2ban fonctionne uniquement à partir des événements présents dans les journaux système.

Il est donc incapable de détecter :

* une compromission réalisée via une vulnérabilité applicative ;
* une attaque utilisant des identifiants valides compromis ;
* une action réalisée après authentification réussie ;
* une compromission interne provenant d'une machine déjà compromise.

> 🛡️ **Sécurité**
>
> Fail2ban est un mécanisme de détection et de réaction. Il ne remplace pas les mesures préventives comme le durcissement système, la gestion des comptes, la segmentation réseau ou la surveillance de sécurité.

---

## Risque de pivotement interne

Dans le cadre du Cybersecurity Learning Lab, le réseau interne est considéré comme un réseau de confiance :

```text
192.168.1.0/24
```

Cette plage est volontairement placée dans le paramètre :

```ini
ignoreip = 127.0.0.1/8 ::1 192.168.1.0/24
```

Cela évite qu'un administrateur interne soit bloqué par erreur.

Cependant, ce choix introduit une limite :

Si une machine du réseau interne est compromise, un attaquant ayant pris le contrôle de cette machine pourra tenter des connexions vers Proxmox sans être bloqué par Fail2ban.

Le mécanisme de protection est donc principalement orienté contre les sources externes.

> ⚠️ **Point d'attention**
>
> La confiance accordée au réseau interne ne doit jamais être considérée comme absolue. Une compromission d'un poste ou d'un serveur interne peut devenir un point de départ pour une attaque de type pivotement.

---

## Complémentarité avec d'autres solutions

Fail2ban doit être intégré dans une approche de défense en profondeur.

Dans le Cybersecurity Learning Lab, plusieurs couches complémentaires sont utilisées :

| Couche                    | Solution              | Objectif                                  |
| ------------------------- | --------------------- | ----------------------------------------- |
| Protection réseau         | Pare-feu / filtrage   | Réduire l'exposition                      |
| Blocage automatisé        | Fail2ban              | Bloquer les attaques répétées             |
| Détection comportementale | CrowdSec              | Identifier les comportements malveillants |
| Analyse antivirus         | ClamAV                | Détection de fichiers malveillants        |
| Surveillance              | ZABBIX01                | Supervision et alertes                    |
| Durcissement              | Configuration système | Réduction de la surface d'attaque         |

Cette approche correspond au principe de défense en profondeur.

---

## Conclusion

La jail Proxmox apporte une protection supplémentaire contre les tentatives répétées d'accès à l'administration Proxmox.

Elle permet :

* de détecter automatiquement les attaques par force brute ;
* de limiter l'efficacité des outils automatisés comme Hydra ;
* de réduire le bruit généré par les tentatives répétées ;
* d'améliorer la visibilité sur les événements de sécurité.

Cependant, elle doit rester considérée comme une couche complémentaire et non comme un mécanisme de protection unique.

La sécurité d'une plateforme Proxmox repose sur l'association de plusieurs mesures :

* authentification forte ;
* réduction des services exposés ;
* sauvegardes ;
* supervision ;
* journalisation ;
* contrôle des accès ;
* réponse aux incidents.

# Références

* Documentation officielle Fail2ban
  https://www.fail2ban.org/

* Documentation Proxmox VE
  https://pve.proxmox.com/pve-docs/

* Documentation Debian - systemd journal
  https://www.debian.org/doc/

* Recommandations ANSSI - Guide d'hygiène informatique
  https://cyber.gouv.fr/publications/guide-dhygiene-informatique
