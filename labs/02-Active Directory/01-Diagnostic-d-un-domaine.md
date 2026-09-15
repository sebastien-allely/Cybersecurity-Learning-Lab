# Diagnostic d'un domaine Active Directory

**Nom du document** : Diagnostic d'un domaine Active Directory
**Technologie** : Active Directory Domain Services
**Catégorie** : Lab pratique
**Objectif** : Diagnostiquer l'état d'un domaine Active Directory et identifier les anomalies affectant les services d'annuaire, DNS et authentification.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif du lab

Ce lab consiste à diagnostiquer un domaine Active Directory à partir de symptômes ou d'anomalies observées.

L'apprenant doit vérifier successivement :

* la connectivité ;
* DNS ;
* l'appartenance au domaine ;
* les services Active Directory ;
* la réplication lorsqu'elle est applicable ;
* l'authentification ;
* les journaux.

---

## 2. Vérifications

Utiliser notamment :

* `ipconfig`
* `nslookup`
* `nltest`
* `dcdiag`
* `repadmin`
* `klist`

Chaque outil doit être utilisé pour répondre à une question de diagnostic précise.

---

## 3. Analyse

Construire une hypothèse à partir du symptôme observé puis la vérifier avec les outils appropriés.

Documenter les résultats et distinguer :

* cause ;
* conséquence ;
* symptôme ;
* événement sans rapport.

---

## 4. Critères de réussite

L'apprenant doit être capable de déterminer l'origine probable d'un dysfonctionnement d'authentification ou de résolution de noms et de justifier son diagnostic par des éléments techniques.

---

## 5. Références

* Microsoft Learn
* ANSSI
* NIST
* MITRE ATT&CK
