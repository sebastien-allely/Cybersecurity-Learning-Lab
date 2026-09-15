# Supervision d'un service

**Nom du document** : Supervision d'un service
**Technologie** : Zabbix
**Catégorie** : Lab pratique
**Objectif** : Concevoir une supervision permettant de détecter l'arrêt d'un service et de distinguer une indisponibilité réelle d'un problème de supervision.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Superviser un service critique et détecter son indisponibilité.

---

## 2. Conception

Définir :

* méthode de collecte ;
* fréquence ;
* valeur attendue ;
* condition de déclenchement ;
* gravité ;
* dépendance éventuelle avec la disponibilité de l'agent.

---

## 3. Test

Arrêter volontairement le service dans le laboratoire puis vérifier :

* collecte ;
* détection ;
* alerte ;
* récupération ;
* résolution automatique du problème.

---

## 4. Critères de réussite

L'arrêt du service doit être détecté et l'alerte doit disparaître après son redémarrage.

---

## 5. Références

* Documentation officielle Zabbix
* ANSSI
