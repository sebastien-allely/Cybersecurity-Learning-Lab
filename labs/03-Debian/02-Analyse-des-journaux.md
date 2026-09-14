# Analyse des journaux Debian

**Nom du document** : Analyse des journaux Debian
**Technologie** : Debian GNU/Linux
**Catégorie** : Lab pratique
**Objectif** : Exploiter journald et les journaux système afin de reconstituer un événement ou un incident.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Rechercher les événements pertinents avant, pendant et après un incident.

---

## 2. Analyse

Utiliser `journalctl` pour :

* rechercher une période ;
* filtrer un service ;
* rechercher les erreurs ;
* établir une chronologie.

---

## 3. Analyse de sécurité

Rechercher également :

* connexions ;
* échecs d'authentification ;
* élévations de privilèges ;
* changements de services ;
* événements inhabituels.

---

## 4. Critères de réussite

L'apprenant doit produire une chronologie argumentée et identifier les événements pertinents pour le diagnostic.

---

## 5. Références

* Documentation Debian
* systemd
* ANSSI
* MITRE ATT&CK
