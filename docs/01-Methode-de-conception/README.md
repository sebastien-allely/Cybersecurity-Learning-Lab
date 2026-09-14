Nom du document : Méthode de conception — Introduction
Technologie : Méthodologie
Catégorie : Méthode de conception
Objectif : Présenter la démarche utilisée pour concevoir, sécuriser et faire évoluer les composants du laboratoire
Auteur : Sébastien ALLELY
Version : 1.0
Date de dernière modification : 2026-09-13

# Méthode de conception

## 1. Objectif

Cette section présente la méthodologie utilisée pour concevoir et faire évoluer le laboratoire.

L'objectif n'est pas uniquement de décrire une configuration technique, mais de formaliser le raisonnement qui conduit à une décision.

Chaque composant doit ainsi être étudié selon son rôle, ses dépendances, ses menaces, ses risques et ses exigences de sécurité.

Cette démarche permet de construire une architecture cohérente et de justifier les choix réalisés.

## 2. Principe général

La conception repose sur une approche progressive :

1. identifier les actifs ;
2. comprendre leur rôle et leurs dépendances ;
3. identifier les menaces ;
4. analyser les risques ;
5. déterminer la criticité ;
6. définir les mesures de sécurité adaptées ;
7. valider techniquement les choix ;
8. documenter les décisions ;
9. identifier la dette technique ;
10. réévaluer régulièrement l'architecture.

Cette démarche permet de passer d'une approche centrée sur la technologie à une approche centrée sur les **besoins, les risques et les objectifs de sécurité**.

## 3. Identification des actifs

Un actif est un élément ayant une valeur ou jouant un rôle dans le fonctionnement du système d'information.

Il peut notamment s'agir :

* d'un serveur ;
* d'une machine virtuelle ;
* d'un service ;
* d'une donnée ;
* d'un compte ;
* d'un équipement réseau ;
* d'un mécanisme de sécurité ;
* d'un élément nécessaire à la disponibilité du laboratoire.

L'identification des actifs constitue le point de départ de l'analyse.

## 4. Analyse des menaces

Une menace représente un événement ou un acteur susceptible de compromettre un actif ou de perturber son fonctionnement.

L'analyse prend notamment en compte :

* les compromissions de comptes ;
* l'exploitation de vulnérabilités ;
* les mouvements latéraux ;
* les élévations de privilèges ;
* les indisponibilités ;
* les pertes ou altérations de données ;
* les erreurs de configuration ;
* les défaillances techniques.

Les scénarios d'attaque peuvent être étudiés à partir d'une approche défensive et, lorsque cela est pertinent, rapprochés des techniques décrites par **MITRE ATT&CK**.

## 5. Analyse des risques

Le risque résulte de la combinaison entre une menace, une vulnérabilité et les conséquences potentielles sur l'actif concerné.

L'analyse permet notamment de déterminer :

* les scénarios prioritaires ;
* les impacts potentiels ;
* les mesures de réduction du risque ;
* les risques résiduels.

Une mesure de sécurité doit donc répondre à un risque identifié ou à une exigence clairement définie.

## 6. Criticité

La criticité permet de hiérarchiser les actifs selon leur importance pour le fonctionnement du laboratoire.

Elle prend notamment en compte :

* la disponibilité ;
* l'intégrité ;
* la confidentialité ;
* les dépendances ;
* les conséquences d'une défaillance ou d'une compromission.

Cette classification permet de concentrer les efforts de sécurité sur les composants dont l'indisponibilité ou la compromission aurait les conséquences les plus importantes.

## 7. Validation technique

Une décision de conception ne doit pas être considérée comme validée uniquement parce qu'elle est théoriquement pertinente.

Lorsque cela est possible, elle doit être confrontée à l'environnement réel par :

* des tests ;
* des vérifications de configuration ;
* des scénarios de panne ;
* des contrôles de sécurité ;
* des observations issues de la supervision.

La validation permet de vérifier l'écart entre le comportement attendu et le comportement réellement observé.

## 8. Justification des décisions

Une décision technique importante doit pouvoir répondre à trois questions :

> Quel problème cherche-t-on à résoudre ?

> Pourquoi cette solution a-t-elle été retenue ?

> Quelles sont ses limites ?

Cette logique permet d'éviter les choix basés uniquement sur les habitudes, la popularité d'une technologie ou la simple possibilité technique.

## 9. Dette technique

La dette technique désigne les compromis ou limitations connus qui devront éventuellement être corrigés ou améliorés.

Elle peut résulter notamment :

* de contraintes budgétaires ;
* de limitations matérielles ;
* de choix temporaires ;
* d'une architecture héritée ;
* d'une fonctionnalité volontairement reportée.

Une dette technique identifiée n'est pas nécessairement une erreur. Elle doit cependant être documentée, évaluée et réévaluée.

## 10. Références méthodologiques

La méthodologie s'appuie notamment sur :

* les recommandations et publications de l'**ANSSI** ;
* les publications du **NIST** ;
* les principes de sécurité de l'**OWASP** lorsque le périmètre le justifie ;
* **MITRE ATT&CK** pour l'analyse des techniques d'attaque ;
* le **SOCLE de Stéphane Robert** lorsqu'il est utilisé comme référence technique pour l'implémentation de mesures de sécurité ou de durcissement ;
* le principe d'amélioration continue **PDCA** (*Plan, Do, Check, Act*).

Ces sources sont utilisées selon leur rôle respectif et ne sont pas considérées comme équivalentes.

Les référentiels normatifs, les guides méthodologiques et les guides techniques d'implémentation doivent être distingués dans la documentation.

## 11. Organisation de la section

Les documents suivants détaillent chaque étape de la démarche :

* `01-Manifeste.md` — principes directeurs de la démarche ;
* `02-Principes-de-conception.md` — principes appliqués à l'architecture ;
* `03-Charte-de-redaction.md` — règles spécifiques à la documentation du projet ;
* `04-Identification-des-actifs.md` — identification et caractérisation des actifs ;
* `05-Analyse-des-menaces.md` — identification des menaces et scénarios ;
* `06-Analyse-des-risques.md` — évaluation et traitement des risques ;
* `07-Criticite.md` — détermination de la criticité ;
* `08-Validation-technique.md` — validation des décisions et configurations ;
* `09-Justifier-une-decision-de-securite.md` — formalisation des décisions ;
* `10-Gestion-de-la-dette-technique.md` — identification et suivi des limitations.

L'ensemble constitue une démarche cohérente : **comprendre → analyser → décider → valider → documenter → améliorer**.
