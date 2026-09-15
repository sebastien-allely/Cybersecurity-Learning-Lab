# Diagnostic d'un bannissement Fail2ban

**Nom du document** : Diagnostic d'un bannissement Fail2ban
**Technologie** : Fail2ban
**Catégorie** : Lab pratique
**Objectif** : Diagnostiquer un bannissement Fail2ban, déterminer son origine et vérifier son caractère légitime ou erroné.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Analyser un bannissement et déterminer :

* pourquoi il a été déclenché ;
* quelle jail est responsable ;
* quel événement l'a provoqué ;
* quelle action a été appliquée ;
* s'il s'agit d'un comportement légitime ou malveillant.

---

## 2. Analyse

Vérifier :

* état de Fail2ban ;
* jail concernée ;
* IP bannie ;
* compteur d'échecs ;
* journal source ;
* filtre utilisé ;
* durée du bannissement.

---

## 3. Faux positif

Déterminer si l'événement peut correspondre à un utilisateur ou service légitime.

Dans ce cas, identifier le mécanisme permettant de réduire les faux positifs sans désactiver inutilement la protection.

---

## 4. Validation

Après correction éventuelle, reproduire le scénario et vérifier le comportement de Fail2ban.

---

## 5. Critères de réussite

L'apprenant doit être capable de retrouver l'origine d'un bannissement et de justifier la décision de maintien, d'adaptation ou de suppression du mécanisme.

---

## 6. Références

* Documentation officielle Fail2ban
* ANSSI
* MITRE ATT&CK
