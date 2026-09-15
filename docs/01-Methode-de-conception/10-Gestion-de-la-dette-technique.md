# 10 - Gestion de la dette technique

| Élément                           | Valeur                                                                                                                |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `10-Gestion-de-la-dette-technique.md`                                                                                 |
| **Technologie**                   | Méthode de conception                                                                                                 |
| **Catégorie**                     | Méthodologie                                                                                                          |
| **Objectif**                      | Définir la méthode permettant d'identifier, d'évaluer, de documenter et de réduire la dette technique du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                      |
| **Version**                       | 1.0                                                                                                                   |
| **Date de dernière modification** | 04/08/2026                                                                                                            |

---

# Objectif

Toute infrastructure accumule au cours de son évolution des choix techniques qui deviennent progressivement plus difficiles à maintenir.

Cette accumulation constitue une forme de **dette technique**.

Dans le laboratoire, cette dette peut notamment provenir :

* d'une configuration temporaire conservée ;
* d'une version ancienne ;
* d'une dépendance devenue obsolète ;
* d'une configuration complexe ;
* d'une absence de documentation ;
* d'un contournement technique ;
* d'une mesure de sécurité devenue insuffisante ;
* d'une supervision incomplète.

L'objectif n'est pas de supprimer toute dette technique.

Il est de **la rendre visible, maîtrisée et compatible avec les objectifs du laboratoire**.

---

# Principe

Une dette technique n'est pas nécessairement une erreur.

Elle peut être un choix volontaire lorsque :

* le coût immédiat d'une correction est supérieur au bénéfice ;
* une solution temporaire permet de poursuivre une expérimentation ;
* une dépendance impose temporairement une contrainte ;
* une évolution doit être planifiée ultérieurement.

Le problème apparaît lorsque la dette devient :

* invisible ;
* non documentée ;
* oubliée ;
* difficile à corriger ;
* source de risque de sécurité.

---

# Sources de dette technique

La dette technique peut notamment provenir de :

## Configuration

* paramètres historiques ;
* exceptions ;
* configurations complexes ;
* règles devenues inutiles.

## Logiciels

* versions obsolètes ;
* dépendances non maintenues ;
* logiciels abandonnés ;
* incompatibilités entre versions.

## Architecture

* dépendances excessives ;
* composants trop fortement couplés ;
* absence de séparation ;
* architecture devenue inadaptée.

## Sécurité

* contrôle insuffisant ;
* mécanisme de protection devenu obsolète ;
* absence de supervision ;
* exceptions de sécurité non réévaluées.

## Documentation

* configuration non documentée ;
* procédure absente ;
* décision impossible à expliquer ;
* documentation différente de l'état réel du laboratoire.

---

# Identification

Lorsqu'une dette technique est découverte, elle doit être caractérisée.

Les informations pertinentes comprennent notamment :

| Élément        | Description                       |
| -------------- | --------------------------------- |
| Origine        | Pourquoi la dette existe          |
| Actif concerné | Système ou composant concerné     |
| Description    | Nature du problème                |
| Impact         | Conséquences potentielles         |
| Risque         | Risque associé                    |
| Priorité       | Niveau de traitement              |
| Action         | Correction envisagée              |
| Échéance       | Date ou condition de réévaluation |

Cette identification permet d'éviter que les problèmes connus disparaissent de la documentation.

---

# Évaluation

La dette technique doit être évaluée selon son impact.

Les critères peuvent notamment comprendre :

* impact sur la sécurité ;
* impact sur la disponibilité ;
* impact sur la maintenance ;
* impact sur les performances ;
* difficulté de correction ;
* dépendances concernées ;
* risque de propagation.

Une dette technique présentant un risque de sécurité important doit être traitée prioritairement.

---

# Acceptation temporaire

Certaines dettes peuvent être conservées temporairement.

Cette situation doit être explicite.

Une dette acceptée doit notamment préciser :

* pourquoi elle est conservée ;
* quel risque elle introduit ;
* quelles mesures compensatoires existent ;
* dans quelles conditions elle devra être corrigée.

L'absence de correction immédiate ne doit pas conduire à l'oubli du problème.

---

# Réduction

La réduction de la dette peut prendre plusieurs formes :

* simplification de configuration ;
* suppression d'une dépendance ;
* mise à niveau logicielle ;
* remplacement d'un composant ;
* amélioration de la documentation ;
* ajout d'une supervision ;
* automatisation ;
* modification de l'architecture.

La solution retenue doit être proportionnée au risque et au coût de correction.

---

# Dette documentaire

La documentation constitue elle-même une partie de la dette technique.

Un système correctement configuré mais mal documenté présente un risque opérationnel.

La documentation doit donc rester alignée avec :

```text
Architecture
   ↓
Configuration
   ↓
Supervision
   ↓
Documentation
```

Lorsqu'une modification importante intervient dans le laboratoire, les documents concernés doivent être réévalués.

---

# Dette de sécurité

Une dette technique devient particulièrement importante lorsqu'elle affecte la sécurité.

Exemples :

* version vulnérable conservée ;
* service inutile toujours actif ;
* règle de pare-feu trop permissive ;
* compte privilégié non maîtrisé ;
* absence de journalisation ;
* absence de supervision ;
* mécanisme de protection non testé.

Ces situations doivent être reliées à l'analyse des risques du laboratoire.

---

# Suivi

La dette technique doit être suivie dans le temps.

La démarche retenue est :

```text
Identification
     ↓
Évaluation
     ↓
Décision
     ↓
Acceptation ou correction
     ↓
Validation
     ↓
Réévaluation
```

Une dette ne doit donc pas être considérée comme définitivement résolue tant que la correction n'a pas été vérifiée.

---

# Critères de traitement

La priorité de traitement doit notamment tenir compte :

1. du risque de sécurité ;
2. de la criticité de l'actif ;
3. de la possibilité de propagation ;
4. de l'exposition ;
5. de la difficulté de correction ;
6. du coût de maintien de la dette.

Une dette faible sur un système isolé peut être conservée.

Une dette présentant un risque important sur un composant central doit être traitée en priorité.

---

# Principe de conception

Le laboratoire applique le principe suivant :

> Une dette technique connue doit être visible, justifiée et réévaluée.

La dette technique ne doit pas être considérée comme un échec de conception.

Elle devient un problème lorsqu'elle n'est plus maîtrisée.

---

# Conclusion

La gestion de la dette technique permet de maintenir la cohérence du laboratoire malgré son évolution.

Elle permet notamment de :

* conserver une vision des compromis réalisés ;
* éviter l'accumulation de configurations historiques ;
* prioriser les corrections ;
* limiter les risques de sécurité ;
* préserver la maintenabilité ;
* maintenir la documentation en cohérence avec l'infrastructure.

La dette technique doit donc être considérée comme un élément normal du cycle de vie du laboratoire, mais jamais comme un élément invisible ou définitivement accepté.
