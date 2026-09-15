# Diagnostic d'une authentification Active Directory

**Nom du document** : Diagnostic d'une authentification Active Directory
**Technologie** : Active Directory Domain Services
**Catégorie** : Lab pratique
**Objectif** : Analyser une anomalie d'authentification en distinguant les problèmes DNS, Kerberos, compte utilisateur et relation d'approbation.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

L'apprenant doit diagnostiquer une impossibilité ou une anomalie d'authentification sur un poste membre du domaine.

---

## 2. Méthode

Vérifier successivement :

1. résolution DNS ;
2. connectivité vers le contrôleur de domaine ;
3. synchronisation temporelle ;
4. état du compte ;
5. tickets Kerberos ;
6. relation avec le domaine ;
7. événements de sécurité.

---

## 3. Outils

Les outils utilisés peuvent notamment être :

* `nslookup`
* `nltest`
* `klist`
* `whoami`
* Observateur d'événements
* outils de diagnostic Active Directory.

---

## 4. Critères de réussite

Le diagnostic doit identifier la couche responsable de l'anomalie et être justifié par les résultats des contrôles.

---

## 5. Références

* Microsoft Learn
* ANSSI
* MITRE ATT&CK
