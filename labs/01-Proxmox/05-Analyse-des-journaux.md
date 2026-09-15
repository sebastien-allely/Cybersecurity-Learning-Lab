# Analyse des journaux Proxmox

**Nom du document** : Analyse des journaux Proxmox
**Technologie** : Proxmox VE
**Catégorie** : Lab pratique
**Objectif** : Collecter, interpréter et corréler les journaux système et Proxmox afin d'identifier l'origine d'un événement ou d'un incident.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif du lab

Ce lab permet d'apprendre à exploiter les journaux disponibles sur un nœud Proxmox pour rechercher la cause d'un dysfonctionnement.

L'analyse doit partir d'un événement précis et progresser vers une corrélation des différentes sources disponibles.

---

## 2. Sources de journaux

Identifier notamment :

* journaux système ;
* journaux des services Proxmox ;
* journaux du cluster ;
* journaux liés aux machines virtuelles ;
* journaux liés au stockage ;
* journaux d'authentification.

Les journaux doivent être analysés en tenant compte de leur date et de leur contexte.

---

## 3. Analyse avec systemd-journald

Afficher les événements récents :

```bash
journalctl
```

Cette commande permet de consulter les événements enregistrés par systemd-journald.

Limiter l'analyse à une période :

```bash
journalctl --since "2026-09-13 18:00:00"
```

Cette commande permet de rechercher les événements apparus depuis une heure donnée.

Filtrer les événements d'un service :

```bash
journalctl -u pveproxy
```

Cette commande permet d'afficher les événements associés au service `pveproxy`.

---

## 4. Recherche des erreurs

Rechercher les événements présentant un niveau d'erreur :

```bash
journalctl -p err
```

Cette commande permet d'afficher les événements correspondant au niveau de priorité `err` ou supérieur.

L'apprenant doit déterminer si les erreurs sont :

* liées à l'incident ;
* antérieures ;
* consécutives à l'incident ;
* sans rapport avec celui-ci.

---

## 5. Corrélation temporelle

Construire une chronologie :

| Heure | Événement | Source | Interprétation |
| ----- | --------- | ------ | -------------- |
|       |           |        |                |
|       |           |        |                |
|       |           |        |                |

L'objectif est de déterminer la relation éventuelle entre plusieurs événements.

---

## 6. Analyse d'un incident

À partir d'un scénario fourni, rechercher :

1. le premier événement anormal ;
2. les événements précédant l'incident ;
3. les erreurs apparues au moment de l'incident ;
4. les événements consécutifs ;
5. les éventuelles traces de récupération.

L'événement le plus visible n'est pas nécessairement la cause initiale.

---

## 7. Analyse de l'authentification

Examiner les événements liés aux connexions et aux privilèges.

Rechercher notamment :

* connexions réussies ;
* échecs d'authentification ;
* utilisation de comptes privilégiés ;
* changements inattendus ;
* accès inhabituels.

---

## 8. Approche Blue Team

La Blue Team utilise les journaux pour :

* détecter les anomalies ;
* reconstruire une chronologie ;
* identifier les causes ;
* rechercher des indicateurs de compromission ;
* documenter l'incident ;
* améliorer la supervision.

---

## 9. Approche Red Team

Dans un environnement contrôlé, un événement peut être généré volontairement afin de vérifier :

* si l'événement est journalisé ;
* où il est enregistré ;
* quelles informations sont disponibles ;
* si la supervision permet de le détecter.

L'objectif est de mesurer la capacité de détection et non de supprimer ou altérer les preuves.

---

## 10. Compte rendu

Le compte rendu doit présenter :

* l'événement étudié ;
* la période analysée ;
* les sources consultées ;
* les événements significatifs ;
* la chronologie ;
* les hypothèses ;
* la cause retenue ;
* les limites de l'analyse.

---

## 11. Critères de réussite

Le lab est réussi lorsque l'apprenant est capable de :

* identifier les principales sources de journaux ;
* filtrer les événements ;
* rechercher une période donnée ;
* analyser un service précis ;
* construire une chronologie ;
* corréler plusieurs événements ;
* distinguer un symptôme d'une cause ;
* documenter ses conclusions.

---

## 12. Références

* Documentation officielle Proxmox VE
* Documentation systemd / journald
* ANSSI
* NIST
* MITRE ATT&CK
* SOCLE de Stéphane Robert lorsqu'une mesure technique d'implémentation est concernée
w
