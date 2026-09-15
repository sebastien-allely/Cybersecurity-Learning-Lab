# 08 - Criticité et dépendances


| Élément | Valeur |
| **Nom du document** | `08-Criticite-et-dependances.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Identifier la criticité des composants Proxmox VE et leurs principales dépendances. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Dépendances de Proxmox

Proxmox dépend notamment :

* du matériel ;
* du réseau ;
* de Debian ;
* du stockage ;
* du DNS ;
* du stockage de sauvegarde ;
* de la supervision.

---

## Défaillance d'un nœud

La perte d'un nœud peut provoquer l'indisponibilité des VM hébergées sur celui-ci.

L'impact dépend notamment :

* de la criticité de la VM ;
* de la disponibilité d'une sauvegarde ;
* de la possibilité de restauration ;
* de l'état du second nœud.

---

## Compromission de l'hyperviseur

Une compromission de Proxmox présente un risque transversal.

Elle peut potentiellement affecter :

* les machines virtuelles ;
* les réseaux virtuels ;
* les stockages ;
* les sauvegardes accessibles ;
* les mécanismes de supervision.

Elle doit donc être considérée comme un événement critique.

---

## Résilience

La réduction du risque repose notamment sur :

* segmentation ;
* contrôle des accès ;
* supervision ;
* sauvegarde ;
* restauration testée ;
* journalisation ;
* contrôle d'intégrité ;
* durcissement.

Les mesures détaillées de sécurité sont documentées dans les référentiels spécialisés.

---

## Références

* Référentiel Architecture du laboratoire
* Référentiel Debian
* Référentiel Hardening Proxmox
* Référentiel Sauvegardes
* Référentiel ZABBIX01
