# 09 - Justifier une décision de sécurité


| Élément | Valeur |
| **Nom du document** | `09-Justifier-une-decision-de-securite.md` |
| **Technologie** | Référentiel du laboratoire |
| **Catégorie** | Méthode de conception |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


|

---

# Objectif

Une décision de sécurité ne doit jamais être prise parce qu'elle est considérée comme une bonne pratique.

Elle doit répondre à un besoin clairement identifié, réduire un risque documenté et pouvoir être justifiée dans le temps.

Cette méthode constitue le fil conducteur de l'ensemble du référentiel.

---

# Pourquoi justifier une décision ?

Une mesure de sécurité possède toujours un coût.

Ce coût peut être :

- technique ;
- humain ;
- financier ;
- opérationnel ;
- organisationnel.

Ajouter une mesure sans justification peut :

- augmenter la complexité ;
- créer de la dette technique ;
- générer des faux positifs ;
- compliquer la maintenance ;
- dégrader l'exploitation.

L'objectif n'est donc pas d'ajouter le plus de sécurité possible, mais d'ajouter la sécurité nécessaire.

---

# Les dix questions de conception

Toute décision doit répondre aux questions suivantes.

## 1. Quel est l'actif concerné ?

Avant de protéger un système, il faut savoir ce qui possède réellement de la valeur.

Exemples :

- un hyperviseur ;
- une base de données ;
- un contrôleur Active Directory ;
- un serveur Web ;
- des sauvegardes.

Sans actif identifié, aucune décision ne peut être justifiée.

---

## 2. Pourquoi cet actif existe-t-il ?

Chaque actif possède une mission.

Comprendre son utilité permet d'évaluer les conséquences de sa compromission.

---

## 3. Quelle est sa criticité ?

La criticité dépend notamment :

- de son rôle ;
- de sa disponibilité ;
- des données hébergées ;
- de son impact sur les autres composants.

Tous les actifs ne nécessitent pas le même niveau de protection.

---

## 4. Quels risques doivent être réduits ?

La cybersécurité répond à des risques, pas à des fonctionnalités.

Chaque mesure doit être reliée à un ou plusieurs risques clairement identifiés.

---

## 5. Quelle est la surface d'attaque ?

Identifier :

- les interfaces exposées ;
- les services actifs ;
- les utilisateurs ;
- les flux réseau ;
- les dépendances.

La réduction de cette surface constitue souvent la première mesure de sécurité.

---

## 6. Quels événements sont observables ?

Une mesure qui ne produit aucun événement exploitable est difficile à vérifier.

Il convient d'identifier :

- les journaux ;
- les métriques ;
- les événements système ;
- les traces réseau.

Ces informations permettront ensuite la supervision.

---

## 7. Quelle décision réduit réellement le risque ?

La mesure retenue doit :

- répondre au risque identifié ;
- être proportionnée ;
- être compatible avec les besoins d'exploitation.

Une décision ne doit jamais être prise uniquement parce qu'elle est populaire ou recommandée.

---

## 8. Comment vérifier son efficacité ?

Toute décision doit pouvoir être contrôlée.

La vérification peut reposer sur :

- une commande ;
- un audit ;
- un test ;
- une revue documentaire ;
- une restauration ;
- un exercice.

Une mesure impossible à vérifier ne peut pas être considérée comme maîtrisée.

---

## 9. Comment superviser cette décision ?

Lorsqu'elle produit des événements exploitables, une décision doit pouvoir être supervisée.

La supervision permet notamment :

- de détecter une dérive ;
- d'identifier une compromission ;
- de contrôler le maintien de la configuration.

Toutes les mesures n'ont cependant pas vocation à produire une alerte.

---

## 10. Cette décision restera-t-elle pertinente dans cinq ans ?

Une bonne décision limite la dette technique.

Avant toute implémentation, il convient de se demander :

- dépend-elle d'une version précise ?
- dépend-elle d'un outil particulier ?
- est-elle facilement maintenable ?
- restera-t-elle compréhensible par un autre administrateur ?

La méthode doit rester stable même si les technologies évoluent.

---

# Principe de conception

Le référentiel repose sur la chaîne logique suivante :

Identification des actifs

↓

Analyse des risques

↓

Réduction de la surface d'attaque

↓

Identification des événements observables

↓

Choix des mesures de sécurité

↓

Vérification

↓

Supervision

↓

Maintenance

Cette séquence est volontairement immuable.

Modifier son ordre conduit généralement à des décisions moins pertinentes et augmente le risque de dette technique.

---

# Ce que le référentiel ne fait pas

Le référentiel n'impose pas une configuration unique.

Il fournit une méthode permettant d'adapter les décisions :

- au contexte ;
- à l'infrastructure ;
- aux contraintes ;
- aux ressources disponibles.

Deux infrastructures différentes pourront ainsi appliquer des mesures différentes tout en suivant exactement la même démarche de conception.

---

# Conclusion

La valeur d'une décision de sécurité ne se mesure pas au nombre de paramètres modifiés.

Elle se mesure à sa capacité à réduire durablement un risque, à rester compréhensible et à demeurer pertinente malgré les évolutions technologiques.

Cette méthode constitue le socle de l'ensemble des documents de ce référentiel.
