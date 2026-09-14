# Création d'une supervision Zabbix

**Nom du document** : Création d'une supervision Zabbix
**Technologie** : Zabbix
**Catégorie** : Lab pratique
**Objectif** : Concevoir une supervision Zabbix complète à partir d'un besoin technique en définissant les éléments supervisés, les seuils et les alertes.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Construire une supervision à partir d'un besoin réel plutôt que d'ajouter des métriques sans objectif.

---

## 2. Méthode

Définir :

* actif ;
* métrique ;
* item ;
* intervalle ;
* seuil ;
* trigger ;
* gravité ;
* dépendance ;
* action.

Un **item** collecte une donnée. Un **trigger** évalue une condition et permet de déclencher une alerte.

---

## 3. Conception

Pour chaque métrique, documenter :

| Élément    | Valeur |
| ---------- | ------ |
| Actif      |        |
| Item       |        |
| Clé        |        |
| Type       |        |
| Intervalle |        |
| Trigger    |        |
| Gravité    |        |
| Dépendance |        |

---

## 4. Validation

Provoquer un événement contrôlé et vérifier :

* collecte ;
* détection ;
* génération du problème ;
* gravité ;
* dépendances ;
* résolution.

---

## 5. Critères de réussite

La supervision doit détecter l'événement attendu sans générer d'alerte inutile.

---

## 6. Références

* Documentation officielle Zabbix
* ANSSI
* NIST
