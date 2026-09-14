# Détection et remédiation CrowdSec

**Nom du document** : Détection et remédiation CrowdSec
**Technologie** : CrowdSec
**Catégorie** : Lab pratique
**Objectif** : Vérifier la capacité de CrowdSec à détecter un comportement malveillant et à appliquer une remédiation contrôlée.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Comprendre la chaîne :

**événement → détection → scénario → décision → remédiation**.

---

## 2. Préparation

Vérifier :

* état du moteur CrowdSec ;
* scénarios actifs ;
* acquisition des journaux ;
* décisions existantes ;
* composant de remédiation.

---

## 3. Test contrôlé

Générer dans le laboratoire un comportement correspondant à un scénario de détection.

Observer :

* événement ;
* décision ;
* durée ;
* remédiation ;
* disparition de la décision.

---

## 4. Analyse

Déterminer :

* ce qui a été détecté ;
* pourquoi le scénario s'est déclenché ;
* quelle décision a été produite ;
* quel composant a appliqué la remédiation.

---

## 5. Supervision

Vérifier également que Zabbix permet de détecter l'indisponibilité du mécanisme de protection.

---

## 6. Critères de réussite

Le scénario doit être détecté, la décision doit être visible et la remédiation doit être vérifiable.

---

## 7. Références

* Documentation officielle CrowdSec
* ANSSI
* MITRE ATT&CK
