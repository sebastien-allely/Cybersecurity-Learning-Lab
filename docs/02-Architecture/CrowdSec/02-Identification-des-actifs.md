# 02 - Identification des actifs

| Élément | Valeur |
| **Nom du document** | `02-Identification-des-actifs.md` |
| **Technologie** | CrowdSec |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les actifs du laboratoire sur lesquels CrowdSec intervient ainsi que les composants nécessaires à son fonctionnement. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Actifs concernés

CrowdSec est utilisé sur plusieurs composants du laboratoire afin d'apporter une capacité de détection et de réaction adaptée à leur rôle.

| Actif      | Rôle de CrowdSec                                                          |
| ---------- | ------------------------------------------------------------------------- |
| `AD01`     | Analyse des événements de sécurité et détection de comportements suspects |
| `ZABBIX01` | Protection du serveur de supervision et analyse des événements pertinents |
| `GLPI01`   | Analyse des événements liés aux services exposés                          |
| `PVE1`     | Analyse des événements du nœud Proxmox                                    |
| `PVE2`     | Analyse des événements du nœud Proxmox                                    |

Les noms utilisés ici respectent l'anonymisation définie pour le laboratoire.

---

# Composants CrowdSec

Le fonctionnement repose principalement sur plusieurs composants :

* le moteur CrowdSec ;
* les parsers ;
* les scénarios ;
* la Local API (LAPI) ;
* les décisions ;
* les mécanismes de remédiation.

Les composants doivent être considérés comme interdépendants.

---

# Journaux exploités

CrowdSec dépend des événements produits par les services surveillés.

Les sources de journaux doivent donc être identifiées pour chaque système.

Exemples :

* journaux système ;
* journaux SSH ;
* journaux des services web ;
* journaux d'authentification ;
* événements liés aux services exposés.

La liste exacte des sources dépend du système et des services effectivement installés.

---

# Dépendances

Le dispositif CrowdSec dépend notamment :

* du fonctionnement du service CrowdSec ;
* de l'accès aux journaux ;
* des parsers ;
* des scénarios ;
* de la LAPI ;
* du mécanisme de remédiation utilisé.

Une défaillance d'un de ces composants peut réduire ou supprimer la capacité de détection ou de réaction.
