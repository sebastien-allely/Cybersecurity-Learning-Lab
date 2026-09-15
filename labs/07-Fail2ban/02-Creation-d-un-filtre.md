# Création d'un filtre Fail2ban

**Nom du document** : Création d'un filtre Fail2ban
**Technologie** : Fail2ban
**Catégorie** : Lab pratique
**Objectif** : Concevoir et valider un filtre Fail2ban permettant d'identifier un événement de sécurité dans un journal.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Créer un filtre adapté à un format de journal identifié et vérifier qu'il détecte uniquement les événements attendus.

---

## 2. Analyse préalable

Identifier :

* format du journal ;
* événement recherché ;
* éléments invariants ;
* éléments variables ;
* faux positifs possibles.

---

## 3. Création

Le filtre doit être conçu à partir d'un événement réel du laboratoire.

Tester séparément :

* correspondance positive ;
* événement non pertinent ;
* événement similaire mais ne devant pas être détecté.

---

## 4. Intégration dans une jail

Associer le filtre à une jail puis définir :

* journal surveillé ;
* seuil ;
* fenêtre temporelle ;
* durée du bannissement ;
* action.

---

## 5. Validation

Provoquer le scénario prévu et vérifier :

* détection ;
* bannissement ;
* journalisation ;
* retour à l'état normal.

---

## 6. Critères de réussite

Le filtre doit détecter l'événement prévu sans générer de faux positifs évidents.

---

## 7. Références

* Documentation officielle Fail2ban
* ANSSI
