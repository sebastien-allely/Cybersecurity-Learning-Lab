# 11 - Checklist


| Élément | Valeur |
| **Nom du document** | `11-Checklist.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Vérifier que les principaux éléments de l'architecture Proxmox VE sont documentés et validés. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Cluster

* [ ] Le cluster est identifié.
* [ ] Le nom du cluster est documenté.
* [ ] Les nœuds sont identifiés.
* [ ] Le quorum est documenté.
* [ ] L'état du cluster peut être vérifié.

---

## Nœuds

* [ ] `PVE1` est documenté.
* [ ] `PVE2` est documenté.
* [ ] Les caractéristiques matérielles sont documentées.
* [ ] Les versions Proxmox sont documentées.
* [ ] Le socle Debian est identifié.

---

## Réseau

* [ ] L'équipement réseau principal est identifié.
* [ ] Les interfaces réseau Proxmox sont identifiées.
* [ ] Les bridges sont documentés.
* [ ] Les flux d'administration sont identifiés.
* [ ] Les flux des VM sont identifiés.
* [ ] Les flux de sauvegarde sont identifiés.
* [ ] Les limitations actuelles sont documentées.
* [ ] Les évolutions réseau sont documentées.

---

## Stockage

* [ ] Les stockages locaux sont identifiés.
* [ ] Les stockages utilisés par les VM sont identifiés.
* [ ] Le stockage de sauvegarde est identifié.
* [ ] Les dépendances du stockage sont documentées.
* [ ] La supervision du stockage est prévue.

---

## Machines virtuelles

* [ ] Les VM sont inventoriées.
* [ ] Les VMID sont documentés.
* [ ] La fonction de chaque VM est documentée.
* [ ] Le nœud hébergeant chaque VM est documenté.
* [ ] Les VM critiques sont identifiées.
* [ ] Les dépendances sont documentées.

---

## Sauvegardes

* [ ] La fréquence est documentée.
* [ ] La rétention est documentée.
* [ ] La destination est documentée.
* [ ] La compression est documentée.
* [ ] Les scripts sont documentés.
* [ ] Les sauvegardes sont supervisées.
* [ ] La restauration est testée périodiquement.

---

## Supervision

* [ ] ZABBIX01 est identifié comme outil de supervision.
* [ ] ZABBIX01 Agent 2 est identifié.
* [ ] Les nœuds Proxmox sont supervisés.
* [ ] Le cluster est supervisé.
* [ ] Le stockage est supervisé.
* [ ] Les sauvegardes sont supervisées.
* [ ] Les VM critiques sont supervisées.

---

## Criticité et dépendances

* [ ] Proxmox est identifié comme actif critique.
* [ ] Les dépendances sont identifiées.
* [ ] Les impacts d'une panne sont documentés.
* [ ] Les impacts d'une compromission sont documentés.
* [ ] Les mesures de résilience sont identifiées.

---

## Documentation

* [ ] Chaque document possède l'en-tête standard.
* [ ] La numérotation des documents est unique.
* [ ] L'architecture actuelle est distinguée de l'architecture cible.
* [ ] Les informations correspondent à l'infrastructure réellement déployée.
* [ ] Les doublons documentaires ont été supprimés.
* [ ] Les références sont indiquées.
* [ ] Le contenu de Hardening n'est pas dupliqué dans Architecture.

---

## Validation finale

L'architecture Proxmox est considérée comme correctement documentée lorsque :

* les nœuds sont identifiés ;
* le cluster est décrit ;
* le réseau est documenté ;
* le stockage est documenté ;
* les VM sont inventoriées ;
* les sauvegardes sont documentées ;
* la supervision est documentée ;
* les dépendances sont identifiées ;
* les évolutions sont distinguées de l'existant ;
* les méthodes de diagnostic sont disponibles.

---

## Périmètre de cette checklist

Cette checklist valide la **documentation et l'architecture Proxmox**.

Elle ne remplace pas la checklist de durcissement présente dans :

```text
docs/03-Hardening/Proxmox/
```
