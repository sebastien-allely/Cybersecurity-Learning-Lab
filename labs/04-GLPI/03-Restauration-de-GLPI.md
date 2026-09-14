# Restauration de GLPI

**Nom du document** : Restauration de GLPI
**Technologie** : GLPI / MariaDB
**Catégorie** : Lab pratique
**Objectif** : Restaurer GLPI et ses données à partir d'une sauvegarde contrôlée et vérifier le fonctionnement du service.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Mettre en œuvre une procédure de restauration après perte ou corruption de l'application ou de ses données.

---

## 2. Éléments à restaurer

Identifier les éléments nécessaires :

* application GLPI ;
* configuration ;
* base MariaDB ;
* fichiers nécessaires au fonctionnement de l'application.

---

## 3. Procédure

Documenter :

* sauvegarde utilisée ;
* date ;
* restauration de la base ;
* restauration des fichiers ;
* configuration ;
* redémarrage des services.

---

## 4. Validation

Vérifier :

* accès à GLPI ;
* authentification ;
* données ;
* inventaire ;
* base de données ;
* journaux ;
* supervision.

---

## 5. Critères de réussite

Le service doit être restauré et fonctionnel, avec une vérification des données restaurées.

---

## 6. Références

* Documentation officielle GLPI
* MariaDB
* ANSSI
