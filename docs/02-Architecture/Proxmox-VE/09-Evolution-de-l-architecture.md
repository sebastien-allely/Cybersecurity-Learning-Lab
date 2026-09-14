# 09 - Évolution de l'architecture


| Élément | Valeur |
| **Nom du document** | `09-Evolution-de-l-architecture.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Décrire les évolutions prévues de l'architecture Proxmox VE et leurs objectifs. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Objectif

Ce document décrit les évolutions possibles de l'architecture Proxmox.

Une évolution présentée ici ne doit pas être considérée comme déployée tant qu'elle n'a pas été effectivement mise en œuvre.

---

## État actuel

L'architecture repose actuellement sur :

* deux nœuds Proxmox ;
* un cluster `Lab` ;
* la box internet comme équipement réseau principal ;
* plusieurs machines virtuelles ;
* un stockage SMB pour les sauvegardes ;
* ZABBIX01 pour la supervision.

---

## Évolution réseau

La principale évolution identifiée concerne la segmentation réseau.

La box internet limite actuellement la possibilité de mettre en œuvre les VLAN nécessaires à une segmentation fine.

L'évolution envisagée consiste donc à introduire un équipement réseau adapté.

---

## Segmentation cible

Une organisation possible serait :

```text
VLAN Administration
        │
VLAN Infrastructure
        │
VLAN Machines virtuelles
        │
VLAN Sauvegardes
        │
VLAN Tests
```

La définition finale des réseaux et des règles de filtrage devra être réalisée lors de la mise en œuvre effective.

---

## Évolution des sauvegardes

Une solution de sauvegarde dédiée pourra être étudiée.

Proxmox Backup Server constitue notamment une option possible.

L'objectif est de réduire la dépendance actuelle à la box internet et d'améliorer les capacités de restauration.

---

## Évolution du cluster

L'ajout d'un troisième nœud pourrait améliorer certains aspects liés au quorum et à la résilience.

Cette évolution doit cependant être évaluée selon :

* le besoin réel ;
* les ressources ;
* la complexité ;
* le coût ;
* la valeur pédagogique.

---

## Principe d'évolution

Les évolutions doivent être guidées par :

* les risques identifiés ;
* les besoins du laboratoire ;
* les limitations actuelles ;
* les objectifs pédagogiques ;
* la capacité de maintenance ;
* le rapport bénéfice / complexité.

Le laboratoire n'a pas vocation à reproduire artificiellement une infrastructure d'entreprise complète.

---

## Mise à jour documentaire

Après chaque évolution importante :

1. l'architecture réelle doit être vérifiée ;
2. les documents concernés doivent être mis à jour ;
3. les informations obsolètes doivent être supprimées ou corrigées ;
4. la checklist doit être réévaluée ;
5. les dépendances doivent être réexaminées.

---

## Références

* Documentation officielle Proxmox VE
* Référentiel Architecture du laboratoire
* Référentiel Réseau
* Référentiel Sauvegardes
