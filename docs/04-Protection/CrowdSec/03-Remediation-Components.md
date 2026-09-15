# 03 - Composants de remédiation CrowdSec

| Élément                           | Valeur                                                                                                                                              |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `03-Remediation-Components.md`                                                                                                                      |
| **Technologie**                   | CrowdSec                                                                                                                                            |
| **Catégorie**                     | Protection / Remédiation                                                                                                                            |
| **Objectif**                      | Documenter les composants de remédiation CrowdSec déployés dans le laboratoire, leur rôle et leur association avec les différents Security Engines. |
| **Auteur**                        | Sébastien Allely                                                                                                                                    |
| **Version**                       | 1.0                                                                                                                                                 |
| **Date de dernière modification** | 08/08/2026                                                                                                                                          |

---

## 1. Objectif

CrowdSec sépare la détection des comportements malveillants de l'application des décisions de sécurité.

Le **Security Engine** analyse les journaux, applique les scénarios de détection et produit des décisions.

Les **Remediation Components**, historiquement appelés *bouncers*, récupèrent ces décisions auprès de la Local API (LAPI) et les appliquent sur le système protégé.

Dans le laboratoire, plusieurs types de composants de remédiation sont utilisés selon le système concerné.

---

## 2. Composants déployés

L'état du laboratoire au 08/08/2026 est le suivant :

| Système  | Security Engine | Composant de remédiation   | Fonction                                         |
| -------- | --------------- | -------------------------- | ------------------------------------------------ |
| Zabbix   | Oui             | `cs-firewall-bouncer`      | Blocage au niveau du pare-feu                    |
| PVE1 | Oui             | `cs-firewall-bouncer`      | Blocage au niveau du pare-feu                    |
| PVE1 | Oui             | `cs-blocklist-mirror`      | Exposition des décisions sous forme de blocklist |
| PVE2 | Oui             | `cs-firewall-bouncer`      | Blocage au niveau du pare-feu                    |
| AD       | Oui             | `windows-firewall-bouncer` | Blocage au niveau du pare-feu Windows            |
| GLPI     | Oui             | Aucun actuellement         | Détection sans composant de remédiation local    |

Cette distinction est volontaire.

La présence de CrowdSec sur une machine ne signifie pas nécessairement qu'un composant de remédiation doit également y être installé.

---

## 3. Firewall Bouncer Linux

Le composant `crowdsec-firewall-bouncer` est utilisé sur :

* Zabbix ;
* PVE1 ;
* PVE2.

Son rôle est d'appliquer au niveau du pare-feu local les décisions produites par CrowdSec.

Il récupère les décisions auprès de la LAPI et maintient les mécanismes de filtrage nécessaires au blocage des adresses concernées.

Dans le laboratoire, ce composant constitue donc la chaîne :

```text
Journaux
   │
   ▼
CrowdSec Security Engine
   │
   ▼
Scénario de détection
   │
   ▼
Décision
   │
   ▼
LAPI
   │
   ▼
Firewall Bouncer
   │
   ▼
Pare-feu du système
   │
   ▼
Trafic bloqué
```

---

## 4. Blocklist Mirror

PVE1 possède également un composant :

```text
cs-blocklist-mirror
```

Ce composant n'a pas le même rôle que le firewall bouncer.

Le **Firewall Bouncer** applique directement les décisions au pare-feu du système.

Le **Blocklist Mirror** expose les décisions CrowdSec sous forme de listes accessibles par HTTP(S), afin de permettre à un équipement compatible de récupérer ces adresses.

Dans le laboratoire, il est donc considéré comme un composant d'intégration et non comme le mécanisme principal de blocage local de PVE1.

---

## 5. Windows Firewall Bouncer

La VM Active Directory possède :

```text
windows-firewall-bouncer
```

Ce composant permet d'appliquer les décisions CrowdSec au niveau du pare-feu Windows.

La chaîne de traitement devient :

```text
Journaux Windows
       │
       ▼
CrowdSec
       │
       ▼
Scénario
       │
       ▼
Décision
       │
       ▼
LAPI
       │
       ▼
Windows Firewall Bouncer
       │
       ▼
Windows Firewall
       │
       ▼
Blocage
```

Le composant est donc adapté à l'environnement Windows contrairement au firewall bouncer utilisé sur les systèmes Linux.

---

## 6. GLPI

CrowdSec est également installé sur la VM GLPI.

Aucun Remediation Component n'est actuellement enregistré sur cette machine.

Ce choix n'est pas considéré comme une anomalie.

Le moteur CrowdSec peut assurer une fonction de détection sans qu'un bouncer local soit nécessaire.

Le laboratoire permet ainsi de comparer :

* un système disposant uniquement de détection ;
* un système disposant de détection et de remédiation ;
* un système disposant de détection, de remédiation et d'un mécanisme de diffusion de blocklists.

Cette différence présente un intérêt pédagogique pour comprendre la séparation entre **détection**, **décision** et **application de la réponse**.

---

## 7. Vérification locale

La présence des composants peut être vérifiée avec :

```bash
sudo cscli bouncers list
```

Cette commande permet notamment de vérifier :

* le nom du composant ;
* son type ;
* sa validité ;
* sa dernière communication avec la LAPI ;
* son mode d'authentification.

Exemple :

```text
Name                            Valid  Last API pull
cs-firewall-bouncer-...         ✔️     2026-08-08T20:29:33Z
```

Une date récente dans `Last API pull` indique que le composant communique avec la LAPI.

Elle ne signifie cependant pas qu'une attaque ou qu'une décision de blocage récente a été observée.

---

## 8. Vérification des décisions

La communication d'un bouncer ne doit pas être confondue avec l'existence de décisions.

Les décisions peuvent être examinées avec les outils CrowdSec appropriés, notamment :

```bash
sudo cscli metrics
```

et, selon le besoin :

```bash
sudo cscli metrics show decisions
```

L'analyse doit permettre de distinguer :

1. l'activité du Security Engine ;
2. les scénarios ayant produit des événements ;
3. les décisions générées ;
4. les décisions récupérées par les composants de remédiation ;
5. les blocages effectivement appliqués.

---

## 9. Interprétation de la console CrowdSec

La console CrowdSec présente séparément plusieurs indicateurs :

* Security Engines ;
* Scenarios ;
* Remediation Components ;
* Blocklists ;
* Alerts.

Ces indicateurs ne doivent pas être interprétés comme une seule métrique d'activité.

Un système peut donc avoir :

* un Security Engine fonctionnel ;
* un bouncer valide et connecté ;
* aucune alerte récente ;
* aucune décision locale récente.

Cette situation n'est pas contradictoire.

Elle signifie simplement qu'aucun événement correspondant aux scénarios configurés n'a nécessairement produit de nouvelle décision pendant la période observée.

---

## 10. État du laboratoire

Au 08/08/2026, les composants suivants sont observés dans le laboratoire :

### Zabbix

```text
cs-firewall-bouncer
Type : crowdsec-firewall-bouncer
Valid : oui
```

### PVE1

```text
cs-blocklist-mirror
Type : crowdsec-blocklist-mirror
Valid : oui

cs-firewall-bouncer
Type : crowdsec-firewall-bouncer
Valid : oui
```

### PVE2

```text
cs-firewall-bouncer
Type : crowdsec-firewall-bouncer
Valid : oui
```

### Active Directory

```text
windows-firewall-bouncer
Type : cs-windows-fw-bouncer
Valid : oui
```

### GLPI

```text
Aucun Remediation Component enregistré.
```

Cet état constitue la référence documentaire du laboratoire à la date de rédaction du présent document.

---

## 11. Liens avec les autres documents

Ce document doit être lu conjointement avec :

* `01-Scenarios-de-detection.md` pour les mécanismes de détection ;
* `02-Remediation.md` pour le principe général de réponse ;
* `README.md` pour la présentation de CrowdSec.

Les configurations propres aux systèmes sont documentées dans les répertoires correspondants du dépôt.

Les éléments liés à la supervision Zabbix sont documentés dans :

```text
zabbix/
```

Les fichiers de configuration nécessaires à la reproduction de l'environnement sont regroupés dans :

```text
automation/
```

lorsqu'ils constituent des artefacts directement réutilisables.

---

## 12. Conclusion

CrowdSec est déployé de manière différenciée dans le laboratoire.

Cette architecture permet d'illustrer que la détection, la décision et la remédiation sont des fonctions distinctes.

Le laboratoire dispose actuellement de plusieurs implémentations de remédiation :

* firewall Linux ;
* firewall Windows ;
* blocklist mirror.

Cette diversité permet d'étudier les différences entre les mécanismes de réponse selon le système protégé.

L'absence de Remediation Component sur GLPI est également conservée comme état documenté de l'architecture et ne doit pas être interprétée automatiquement comme une erreur.
