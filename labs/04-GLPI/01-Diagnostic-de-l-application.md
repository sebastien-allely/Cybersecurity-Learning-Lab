# Diagnostic de l'application GLPI

**Nom du document** : Diagnostic de l'application GLPI
**Technologie** : GLPI / Apache / MariaDB
**Catégorie** : Lab pratique
**Objectif** : Diagnostiquer un dysfonctionnement de GLPI en analysant les différentes couches de l'application.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Identifier la couche responsable d'un dysfonctionnement GLPI.

L'analyse doit distinguer :

* système ;
* réseau ;
* Apache ;
* PHP ;
* MariaDB ;
* GLPI.

---

## 2. Méthode

Partir du symptôme puis remonter les différentes couches.

Vérifier notamment :

* disponibilité du serveur ;
* service Apache ;
* configuration PHP ;
* disponibilité MariaDB ;
* connectivité à la base ;
* journaux ;
* état de GLPI.

---

## 3. Critères de réussite

L'apprenant doit identifier la cause du dysfonctionnement et justifier son diagnostic.

---

## 4. Références

* Documentation officielle GLPI
* Apache
* MariaDB
* ANSSI
