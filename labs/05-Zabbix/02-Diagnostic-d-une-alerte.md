# Diagnostic d'une alerte Zabbix

**Nom du document** : Diagnostic d'une alerte Zabbix
**Technologie** : Zabbix
**Catégorie** : Lab pratique
**Objectif** : Analyser une alerte Zabbix, déterminer sa cause et distinguer le symptôme de l'origine réelle du problème.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

À partir d'une alerte, déterminer :

* ce qui est réellement défaillant ;
* pourquoi Zabbix l'a détecté ;
* si l'alerte est pertinente ;
* quelles dépendances doivent être prises en compte.

---

## 2. Méthode

Analyser :

1. problème ;
2. item ;
3. valeur collectée ;
4. trigger ;
5. dépendances ;
6. hôte ;
7. événement source.

---

## 3. Validation

Comparer l'état observé dans Zabbix avec l'état réel du système supervisé.

---

## 4. Critères de réussite

L'apprenant doit expliquer l'origine de l'alerte et proposer une action corrective adaptée.

---

## 5. Références

* Documentation officielle Zabbix
* ANSSI
