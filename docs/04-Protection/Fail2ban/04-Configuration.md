# Configuration de Fail2ban


| Élément | Valeur |
| **Nom du document** | `04-Configuration.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Protection |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |





## Objectif

L'installation de Fail2ban fournit une configuration fonctionnelle, mais celle-ci est volontairement générique afin de convenir au plus grand nombre d'environnements.

Dans un contexte de production, il est recommandé de personnaliser cette configuration afin de l'adapter aux services réellement exposés, au niveau de risque accepté et aux contraintes d'exploitation.

L'objectif de ce chapitre est de présenter une configuration reproductible, documentée et facilement maintenable. Chaque paramètre retenu est justifié afin de permettre au lecteur de comprendre les choix réalisés et de les adapter à son propre environnement.

La configuration proposée dans ce document est utilisée au sein du **Cybersecurity Learning Lab** et privilégie les principes suivants :

* limiter la surface d'attaque ;
* protéger en priorité les services exposés ;
* conserver une configuration simple et lisible ;
* faciliter la maintenance et les mises à jour ;
* pouvoir valider rapidement le bon fonctionnement de chaque modification.

## Philosophie de configuration

La configuration de Fail2ban ne consiste pas à activer un maximum de règles, mais à répondre à un besoin de sécurité clairement identifié.

Chaque directive ajoutée doit répondre à une question simple :

> Quel risque cette configuration permet-elle de réduire ?

À l'inverse, toute directive dont l'utilité n'est pas démontrée augmente inutilement la complexité de l'outil et rend sa maintenance plus difficile.

Dans le Cybersecurity Learning Lab, les choix de configuration reposent sur les principes suivants :

* utiliser uniquement les fonctionnalités réellement nécessaires ;
* privilégier les mécanismes natifs du système d'exploitation ;
* documenter chaque décision technique ;
* vérifier systématiquement les configurations avant leur mise en production ;
* être capable de revenir rapidement à un état fonctionnel en cas d'erreur.

Cette approche permet de produire une configuration cohérente, reproductible et adaptée à une utilisation professionnelle.


## Le fichier `jail.local`


Fail2ban est fourni avec un fichier de configuration par défaut nommé `jail.conf`.

Ce fichier est installé par le paquet logiciel et sert de référence. Il ne doit pas être modifié directement, car une mise à jour de Fail2ban peut le remplacer et entraîner la perte des personnalisations réalisées.

La méthode retenue dans le Cybersecurity Learning Lab consiste à créer un fichier `jail.local`, qui surcharge uniquement les paramètres nécessaires tout en conservant intacte la configuration d'origine.

Cette approche présente plusieurs avantages :

* elle facilite les mises à jour de Fail2ban ;
* elle simplifie les opérations de maintenance ;
* elle distingue clairement la configuration d'origine des personnalisations locales ;
* elle facilite les audits de configuration ;
* elle réduit le risque de perte de configuration lors des évolutions du logiciel.

Si le fichier `jail.local` n'existe pas, il peut être créé à partir de la configuration par défaut :

```bash
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

Une fois ce fichier créé, seules les directives nécessaires au contexte de déploiement sont conservées. Cette démarche permet d'obtenir une configuration plus lisible, plus simple à maintenir et plus facile à auditer.


## Paramètres globaux

Les paramètres globaux définissent le comportement général de Fail2ban. Ils sont appliqués par défaut à l'ensemble des jails, sauf si une jail les surcharge explicitement.

Dans le Cybersecurity Learning Lab, seuls les paramètres nécessaires au fonctionnement de l'infrastructure sont modifiés. Les autres conservent leur valeur par défaut.

Les principaux paramètres retenus sont les suivants :

| Paramètre   | Valeur retenue                    | Description                                                                                                                                         |
| ----------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ignoreip`  | `127.0.0.1/8 ::1 192.168.1.0/24` | Exclut les adresses de confiance afin d'éviter un auto-bannissement des administrateurs.                                                            |
| `maxretry`  | `3`                               | Nombre maximal d'échecs d'authentification autorisés avant le déclenchement d'un bannissement.                                                      |
| `findtime`  | `2d`                              | Fenêtre temporelle durant laquelle les échecs sont comptabilisés. Cette valeur permet également de détecter les attaques lentes (« low and slow »). |
| `bantime`   | `1h`                              | Durée du bannissement appliqué lorsqu'un seuil est atteint.                                                                                         |
| `backend`   | `systemd`                         | Utilise le journal Systemd comme source d'événements, ce qui est recommandé sur Debian, Ubuntu et Proxmox VE.                                       |
| `banaction` | `nftables`                        | Met en œuvre le bannissement à l'aide de `nftables`, pare-feu natif des distributions Linux récentes.                                               |

Les valeurs présentées correspondent aux choix retenus pour ce projet. Elles peuvent être adaptées selon le contexte de déploiement, le niveau d'exposition des services et la politique de sécurité de l'organisation.


### Paramètre `ignoreip`

#### Définition

Le paramètre `ignoreip` définit les adresses IP ou les réseaux qui ne doivent jamais être bannis par Fail2ban, même si plusieurs tentatives d'authentification échouent.

Cette liste constitue une exception au mécanisme de bannissement et doit être limitée aux hôtes de confiance.

#### Configuration retenue

```ini
ignoreip = 127.0.0.1/8 ::1 192.168.1.0/24
```

#### Justification

Dans le Cybersecurity Learning Lab, le réseau d'administration est considéré comme un réseau de confiance. Cette configuration évite qu'un administrateur soit accidentellement bloqué à la suite d'erreurs de saisie répétées.

Les adresses de boucle locale (`127.0.0.1/8` et `::1`) sont également exclues afin de préserver le fonctionnement des services locaux.

#### Risques si la configuration est modifiée

Une liste `ignoreip` trop restrictive augmente le risque d'auto-bannissement des administrateurs, ce qui peut compliquer les opérations de maintenance.

À l'inverse, une liste trop permissive réduit l'efficacité de Fail2ban en excluant des plages d'adresses qui devraient être surveillées.

#### Validation

Après modification du fichier `jail.local`, vérifier que la configuration est correctement prise en compte :

```bash
fail2ban-client -d
```

Puis contrôler que le service démarre correctement :

```bash
systemctl status fail2ban
```

### Paramètre `maxretry`

#### Définition

Le paramètre `maxretry` définit le nombre maximal de tentatives d'authentification échouées autorisées avant que Fail2ban ne déclenche un bannissement.

Ce seuil est évalué pendant la période définie par le paramètre `findtime`.

#### Configuration retenue

```ini
maxretry = 3
```

#### Justification

Le Cybersecurity Learning Lab retient une valeur de trois tentatives, qui constitue un compromis entre sécurité et exploitation.

Cette valeur permet de bloquer rapidement les attaques automatisées tout en laissant une faible marge d'erreur à un administrateur ou à un utilisateur légitime.

#### Cas d'usage

Un attaquant lance une attaque par force brute sur un service SSH exposé à Internet.

Après trois échecs consécutifs dans la fenêtre d'observation définie par `findtime`, Fail2ban applique automatiquement la durée de bannissement configurée par `bantime`, interrompant ainsi l'attaque.

#### ⚠️ Point d'attention

Une valeur trop faible peut provoquer des bannissements involontaires lors d'erreurs de saisie.

À l'inverse, une valeur trop élevée laisse davantage de temps à un attaquant pour tester des identifiants avant que le mécanisme de protection ne s'active.

Le choix de cette valeur doit donc être cohérent avec la politique de sécurité de l'organisation, le niveau d'exposition du service et les besoins opérationnels.

#### Validation

Après modification de la configuration, vérifier que la syntaxe est correcte :

```bash
fail2ban-client -d
```

Puis confirmer que la jail concernée est active :

```bash
fail2ban-client status
```

### Paramètre `findtime`

#### Définition

Le paramètre `findtime` définit la fenêtre temporelle pendant laquelle Fail2ban comptabilise les tentatives d'authentification échouées.

Si le nombre d'échecs atteint la valeur définie par `maxretry` au cours de cette période, l'adresse IP concernée est bannie pendant la durée spécifiée par `bantime`.

#### Configuration retenue

```ini
findtime = 2d
```

#### Justification

Le Cybersecurity Learning Lab retient une fenêtre d'observation de deux jours afin de détecter non seulement les attaques rapides, mais également les attaques dites *low and slow*.

Ce type d'attaque consiste à espacer volontairement les tentatives d'authentification afin de contourner des mécanismes de protection configurés avec une fenêtre d'observation trop courte.

#### Cas d'usage

Un attaquant tente une authentification toutes les quelques heures afin de passer sous le seuil de détection.

Avec une fenêtre de deux jours, ces tentatives restent corrélées et peuvent conduire au bannissement dès que le seuil de `maxretry` est atteint.

#### ⚠️ Point d'attention

Une valeur trop courte peut laisser passer des attaques lentes.

À l'inverse, une valeur très longue augmente la probabilité qu'un utilisateur légitime atteigne le seuil de bannissement après plusieurs erreurs espacées dans le temps.

Le choix de cette valeur doit donc être adapté au niveau d'exposition du service, aux habitudes des utilisateurs et au niveau de risque accepté.

#### Validation

Contrôler que la configuration est correctement prise en compte :

```bash
fail2ban-client -d
```

Puis vérifier les paramètres de la jail :

```bash
fail2ban-client get sshd findtime
```


### Paramètre `bantime`

#### Définition

Le paramètre `bantime` définit la durée pendant laquelle une adresse IP reste bannie après avoir atteint le seuil défini par `maxretry` dans la période `findtime`.

Pendant cette durée, toute nouvelle tentative de connexion depuis cette adresse IP est rejetée.

#### Configuration retenue

```ini
bantime = 1h
```

#### Justification

Une durée d'une heure constitue un compromis entre efficacité et continuité des opérations.

Elle interrompt une attaque automatisée suffisamment longtemps pour casser son cycle d'exécution tout en limitant les conséquences d'un bannissement accidentel d'un administrateur.

#### Cas d'usage

Une attaque par force brute est détectée sur un service SSH exposé.

Après trois tentatives échouées dans la période définie par `findtime`, l'adresse IP est automatiquement bannie pendant une heure, interrompant l'attaque sans intervention manuelle.

#### ⚠️ Point d'attention

Une durée de bannissement trop courte permet à un attaquant de reprendre rapidement son attaque.

À l'inverse, une durée excessive peut pénaliser les utilisateurs légitimes ou les administrateurs ayant commis plusieurs erreurs de saisie.

Pour des services particulièrement exposés, des mécanismes de bannissement progressif (*incremental banning*) peuvent constituer une alternative intéressante, en augmentant automatiquement la durée des bannissements en cas de récidive.

#### Validation

Vérifier la valeur appliquée :

```bash
fail2ban-client get sshd bantime
```

Afficher les adresses actuellement bannies :

```bash
fail2ban-client status sshd
```

### Paramètre `backend`

#### Définition

Le paramètre `backend` indique à Fail2ban où et comment récupérer les événements de sécurité qu'il doit analyser.

Selon le système d'exploitation et les services surveillés, Fail2ban peut lire directement des fichiers de journalisation (*log files*) ou interroger le journal Systemd.

#### Configuration retenue

```ini
backend = systemd
```

#### Justification

Le Cybersecurity Learning Lab utilise Debian, Ubuntu et Proxmox VE, qui s'appuient nativement sur Systemd et son service de journalisation `systemd-journald`.

L'utilisation du backend `systemd` présente plusieurs avantages :

* accès direct aux journaux sans dépendre de fichiers texte ;
* meilleure compatibilité avec les distributions Linux récentes ;
* réduction des problèmes liés à la rotation des journaux (*log rotation*) ;
* meilleures performances lors de la recherche d'événements.

Cette configuration est aujourd'hui recommandée sur les systèmes modernes utilisant Systemd.

#### Cas d'usage

Une tentative d'authentification échoue sur un serveur Proxmox.

Le service `pvedaemon` enregistre immédiatement l'événement dans le journal Systemd.

Fail2ban interroge directement ce journal, détecte l'échec et incrémente le compteur associé à l'adresse IP concernée, sans avoir à analyser un fichier de logs.

#### ⚠️ Point d'attention

Le backend `systemd` nécessite que le service `systemd-journald` soit actif.

Si celui-ci est arrêté ou mal configuré, Fail2ban ne pourra plus recevoir les événements nécessaires au fonctionnement de ses jails.

Sur des systèmes ne reposant pas sur Systemd ou utilisant exclusivement des fichiers de journalisation, un autre backend devra être choisi.

#### Validation

Vérifier que le journal Systemd est actif :

```bash
systemctl status systemd-journald
```

Contrôler que Fail2ban reçoit correctement les événements :

```bash
journalctl -u fail2ban -f
```

### Paramètre `banaction`

#### Définition

Le paramètre `banaction` définit la méthode utilisée par Fail2ban pour appliquer un bannissement.

Lorsqu'une adresse IP dépasse le seuil autorisé, Fail2ban exécute automatiquement l'action configurée afin de bloquer les connexions provenant de cette adresse.

#### Configuration retenue

```ini
banaction = nftables
```

#### Justification

Le Cybersecurity Learning Lab utilise `nftables`, successeur d'iptables et pare-feu natif des distributions Linux modernes.

Cette solution présente plusieurs avantages :

* meilleure intégration avec les noyaux Linux récents ;
* performances améliorées ;
* règles plus simples à maintenir ;
* compatibilité avec Debian 12+, Ubuntu 24.04 LTS et Proxmox VE.

L'utilisation de `nftables` garantit également une cohérence avec les recommandations actuelles des principales distributions Linux.

#### Cas d'usage

Une adresse IP dépasse le seuil de trois tentatives d'authentification autorisées.

Fail2ban ajoute automatiquement cette adresse dans un ensemble (`set`) géré par `nftables`.

Toutes les nouvelles connexions provenant de cette adresse sont alors rejetées jusqu'à la fin de la durée de bannissement.

#### ⚠️ Point d'attention

Le mécanisme de bannissement repose sur le bon fonctionnement de `nftables`.

Une modification manuelle des règles du pare-feu ou la désactivation de `nftables` peut empêcher Fail2ban d'appliquer correctement les bannissements.

Il est recommandé de vérifier régulièrement que les règles générées par Fail2ban sont toujours présentes après une mise à jour du système ou une modification de la configuration réseau.

#### Validation

Afficher les règles actuellement chargées :

```bash
nft list ruleset
```

Lister les jails actives :

```bash
fail2ban-client status
```

Afficher les informations détaillées d'une jail :

```bash
fail2ban-client status sshd
```

## Construction progressive du fichier `jail.local`

### Pourquoi utiliser `jail.local` ?

Fail2ban fournit un fichier de configuration principal nommé `jail.conf`.

Ce fichier est installé par le paquet logiciel et peut être remplacé lors d'une mise à jour du système.

Modifier directement ce fichier est donc déconseillé, car les personnalisations risquent d'être perdues.

La bonne pratique consiste à créer un fichier `jail.local`, qui surcharge uniquement les paramètres nécessaires tout en conservant le fichier d'origine intact.

Cette approche présente plusieurs avantages :

* meilleure compatibilité avec les mises à jour du système ;
* séparation claire entre la configuration d'origine et les personnalisations ;
* maintenance simplifiée ;
* facilité de comparaison avec la configuration par défaut.

Cette méthode est recommandée par la documentation officielle de Fail2ban et s'inscrit dans les bonnes pratiques d'administration des systèmes Linux.


## Création du fichier `jail.local`

Par défaut, Fail2ban fournit un fichier de configuration principal nommé `jail.conf`.

Afin de préserver cette configuration d'origine et de garantir la compatibilité avec les futures mises à jour du système, il est recommandé de créer un fichier `jail.local`.

Le fichier peut être créé à l'aide de la commande suivante :

```bash
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

Le fichier est ensuite modifié avec l'éditeur de texte de votre choix.

Dans le Cybersecurity Learning Lab, l'éditeur **Vim** est utilisé :

```bash
sudo vim /etc/fail2ban/jail.local
```

> 💡 **Bonne pratique**
>
> Le projet utilise Vim pour l'ensemble des manipulations réalisées sur les systèmes Linux. Les commandes présentées dans cette documentation sont donc rédigées en conséquence afin de conserver une cohérence sur l'ensemble du dépôt.


## Le bloc `[DEFAULT]`

Le bloc `[DEFAULT]` contient les paramètres communs appliqués à l'ensemble des jails.

Toute configuration définie dans cette section est automatiquement héritée par les jails, sauf si une valeur spécifique est redéfinie localement.

Cette approche présente plusieurs avantages :

* réduction des duplications de configuration ;
* simplification de la maintenance ;
* homogénéité des paramètres entre les différents services protégés.

Le Cybersecurity Learning Lab privilégie cette approche afin de centraliser les paramètres communs dans une seule section.


## Configuration du bloc `[DEFAULT]`

Le bloc `[DEFAULT]` centralise les paramètres communs à l'ensemble des jails du Cybersecurity Learning Lab.

```ini
[DEFAULT]

# Réseau de confiance
ignoreip = 127.0.0.1/8 ::1 192.168.1.0/24

# Détection
maxretry = 3
findtime = 2d

# Bannissement
bantime = 1h
banaction = nftables

# Source des journaux
backend = systemd
```

### Explication

Cette configuration constitue le socle commun appliqué à toutes les jails.

Chaque service hérite automatiquement de ces paramètres, ce qui garantit une politique de sécurité homogène sur l'ensemble des serveurs.

Les paramètres spécifiques à un service (SSH, Proxmox VE, Apache, etc.) seront définis uniquement lorsque cela sera nécessaire.

> 💡 **Bonne pratique**
>
> Éviter de dupliquer les mêmes paramètres dans chaque jail. Les placer dans le bloc `[DEFAULT]` facilite la maintenance et réduit les risques d'incohérence.

> 🛡️ **Sécurité**
>
> Les paramètres présentés correspondent à une configuration adaptée à un environnement de laboratoire. Avant un déploiement en production, ils doivent être revus en fonction de l'exposition des services, de la politique de sécurité de l'organisation et des contraintes d'exploitation.


## Méthodologie de développement des filtres personnalisés

### Objectif

Le Cybersecurity Learning Lab privilégie systématiquement les filtres officiels fournis par Fail2ban lorsqu'ils répondent au besoin.

Les filtres personnalisés ne sont développés que lorsqu'aucun filtre officiel n'existe ou lorsqu'une application nécessite une logique de détection spécifique (par exemple GLPI01 ou Proxmox VE).

Cette approche permet de bénéficier des mises à jour de la communauté Fail2ban tout en limitant la maintenance des développements spécifiques.

---

### Principes de conception

Tous les filtres personnalisés développés dans le cadre du projet respectent les règles suivantes.

| Règle | Description |
|---------|-------------|
| Un filtre = un objectif | Chaque filtre traite une seule catégorie d'événements ou de menaces. |
| Priorité aux filtres officiels | Un filtre personnalisé n'est développé qu'après vérification qu'aucun filtre officiel ne couvre le besoin. |
| Cas d'usage réel | Chaque expression régulière doit correspondre à une attaque ou à un comportement documenté. |
| Simplicité | Les expressions régulières restent lisibles, maintenables et limitées au strict nécessaire. |
| Validation systématique | Chaque filtre est testé avec `fail2ban-regex` avant son intégration. |
| Documentation | Chaque filtre est accompagné d'exemples de journaux, d'explications et de cas d'usage. |

---

### Cycle de développement

Chaque nouveau filtre suit le processus suivant :

```text
Identification du besoin
        │
        ▼
Recherche d'un filtre officiel Fail2ban
        │
        ├── Filtre disponible
        │       │
        │       └── Utilisation du filtre officiel
        │
        └── Aucun filtre adapté
                │
                ▼
Développement d'un filtre personnalisé
                │
                ▼
Tests avec fail2ban-regex
                │
                ▼
Validation fonctionnelle
                │
                ▼
Documentation
```

---

### Organisation retenue pour le projet

La stratégie retenue pour la version 1 du Cybersecurity Learning Lab est la suivante.

| Service | Stratégie retenue |
|---------|-------------------|
| SSH | Utilisation du filtre officiel `sshd.conf` |
| Apache HTTP Server | Utilisation des filtres officiels `apache-*` |
| MariaDB | Utilisation du filtre officiel `mysqld-auth.conf` |
| GLPI01 | Développement de filtres spécifiques au projet |
| Proxmox VE | Développement de filtres spécifiques au projet |

---

### Pourquoi cette approche ?

Cette méthodologie présente plusieurs avantages :

- elle privilégie les composants officiellement maintenus par la communauté Fail2ban ;
- elle réduit les développements et la maintenance des filtres personnalisés ;
- elle bénéficie des mises à jour et des corrections apportées aux filtres officiels ;
- elle concentre les développements sur les besoins réellement spécifiques du projet ;
- elle facilite la compréhension, les tests et les contributions futures.

> **Bonnes pratiques**
>
> Avant de développer un nouveau filtre, il convient toujours de vérifier si un filtre officiel Fail2ban répond déjà au besoin. Les filtres personnalisés doivent uniquement compléter les fonctionnalités existantes et non les remplacer.
