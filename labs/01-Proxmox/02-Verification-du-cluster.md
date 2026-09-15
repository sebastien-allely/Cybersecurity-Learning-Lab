---
Nom du document: Vérification du cluster Proxmox
Technologie: Proxmox VE
Catégorie: Lab
Objectif: Vérifier l'état du cluster, du quorum, des nœuds et des services critiques
Auteur: Sébastien ALLELY
Version: 1.0
Date de dernière modification: 2026-09-13
---

# Vérification du cluster Proxmox

## 1. Objectif

Ce laboratoire a pour objectif de vérifier l'état opérationnel d'un cluster Proxmox VE.

La vérification porte principalement sur :

- l'état du cluster ;
- le quorum ;
- le nombre de nœuds ;
- l'état des nœuds ;
- les services critiques ;
- la cohérence de la configuration ;
- les éventuels symptômes de perte de disponibilité.

L'objectif n'est pas uniquement de constater qu'un nœud est accessible, mais de déterminer si le cluster est réellement opérationnel.

## 2. Prérequis

Le laboratoire nécessite :

- un cluster Proxmox VE fonctionnel ;
- un accès administrateur à un nœud ;
- un accès SSH ;
- les commandes `pvecm` et `systemctl`.

## 3. Vérification de l'état du cluster

La commande suivante permet d'afficher l'état du cluster et de vérifier notamment le quorum et le nombre de votes :

```bash
pvecm status
