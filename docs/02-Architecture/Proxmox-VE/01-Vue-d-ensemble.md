# 01 - Vue d'ensemble


| Élément | Valeur |
| **Nom du document** | `01-Vue-d-ensemble.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Présenter une vue d'ensemble de l'architecture Proxmox VE et de son rôle dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


Cette répartition correspond à l'état documenté du laboratoire et doit être actualisée en cas de modification de l'infrastructure.

---

## Fonctions assurées

Proxmox assure notamment :

* la virtualisation des systèmes ;
* l'administration des machines virtuelles ;
* la gestion du cluster ;
* la gestion des ressources ;
* la gestion des stockages ;
* la gestion du réseau virtuel ;
* l'exécution des sauvegardes ;
* l'intégration avec la supervision.

---

## Criticité

Proxmox doit être considéré comme un actif critique du laboratoire.

Son rôle de couche de virtualisation crée une dépendance entre l'hyperviseur et les services qu'il héberge.

Une compromission de l'hyperviseur présente également un impact potentiel supérieur à celui d'une compromission limitée à une seule machine virtuelle.

---

## Architecture actuelle et architecture cible

La documentation distingue :

* **l'architecture actuelle**, correspondant aux composants réellement déployés ;
* **l'architecture cible**, correspondant aux évolutions envisagées.

Cette distinction évite de présenter une évolution future comme une fonctionnalité déjà disponible.

---

## Périmètre documentaire

Ce document présente l'architecture générale.

Les aspects suivants disposent de documents dédiés :

* nœuds et cluster ;
* réseau ;
* stockage ;
* machines virtuelles ;
* sauvegardes ;
* supervision ;
* criticité ;
* évolutions ;
* exploitation ;
* validation.

Les mesures de durcissement sont documentées séparément dans `Hardening\Proxmox`.

---

## Références

* Documentation officielle Proxmox VE
* Documentation Debian
* Référentiel Architecture du Cybersecurity-Learning-Lab
