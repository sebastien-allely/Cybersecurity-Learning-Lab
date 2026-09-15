# Détection d'une attaque avec Fail2ban

**Nom du document** : Détection d'une attaque avec Fail2ban
**Technologie** : Fail2ban
**Catégorie** : Lab pratique
**Objectif** : Vérifier la capacité de Fail2ban à détecter des échecs d'authentification et à appliquer une mesure de blocage.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Comprendre la chaîne :

**journal → filtre → échec détecté → jail → bannissement**.

---

## 2. Préparation

Vérifier :

* service Fail2ban ;
* jails actives ;
* filtres utilisés ;
* fichiers journaux surveillés ;
* paramètres de bannissement.

---

## 3. Test contrôlé

Dans le laboratoire, provoquer des échecs d'authentification contrôlés.

Observer :

* apparition des événements ;
* détection par le filtre ;
* compteur d'échecs ;
* bannissement ;
* expiration du bannissement.

---

## 4. Analyse

Identifier :

* le journal source ;
* le filtre utilisé ;
* la jail ;
* le seuil ;
* la durée ;
* l'action de bannissement.

---

## 5. Critères de réussite

Fail2ban doit détecter le comportement prévu et appliquer le bannissement correspondant.

---

## 6. Références

* Documentation officielle Fail2ban
* ANSSI
* MITRE ATT&CK
