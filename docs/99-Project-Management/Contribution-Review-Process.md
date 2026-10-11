# Processus de contribution et de revue

| Élément | Valeur |
|---|---|
| **Nom du document** | `Contribution-Review-Process.md` |
| **Technologie** | Git et GitHub |
| **Catégorie** | Gestion du projet |
| **Objectif** | Définir le workflow de contribution, les contrôles et les critères de revue avant fusion. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

Ce processus garantit que les modifications sont traçables, relues et cohérentes avec le référentiel. Toute modification proposée à `main` doit passer par une Pull Request (PR).

## 2. Préparation

Avant de commencer :
- lire le manifeste, la charte de rédaction et le guide de rédaction ;
- identifier le besoin, les fichiers concernés et les dépendances ;
- rechercher les documents ou contrôles existants pour éviter les doublons ;
- vérifier qu'aucune donnée sensible ne sera publiée ;
- définir les tests et critères d'acceptation.

## 3. Workflow

1. Partir d'une branche de référence à jour.
2. Créer une branche nommée selon le sujet, par exemple `docs/correction-index-fail2ban` ou `fix/zabbix-template-validation`.
3. Réaliser une modification limitée à un objectif cohérent.
4. Relire les différences et contrôler les liens, métadonnées et références.
5. Exécuter les tests adaptés aux changements.
6. Ouvrir une PR vers `main`, en décrivant le besoin, le périmètre, les risques et les vérifications.
7. Traiter les commentaires de revue et mettre à jour la PR.
8. Fusionner uniquement après validation selon les règles du dépôt.

Ne pas pousser directement des changements de travail sur `main`.

## 4. Contrôles de revue

### Documentation
- Les sept champs de métadonnées sont présents et cohérents.
- Le titre, le nom du fichier et le contenu correspondent.
- Les liens internes et externes ont été vérifiés.
- Les affirmations techniques importantes sont sourcées.
- Les faits, choix locaux, recommandations et travaux futurs sont distingués.
- L'anonymisation est effective.

### Commandes et scripts
- Les commandes sont complètes, copiables et contextualisées.
- Chaque commande est expliquée et accompagnée du résultat attendu.
- Les opérations destructrices ou susceptibles d'interrompre un service sont signalées.
- Les scripts ont été testés dans un environnement adapté avant d'être déclarés validés.
- Les prérequis, permissions, erreurs possibles et moyens de retour arrière sont indiqués.

### Configuration et sécurité
- Les modifications répondent à un besoin et à un risque documentés.
- Les privilèges sont minimisés.
- Les contrôles de validation et de supervision sont décrits.
- Aucun secret, jeton, clé privée ou détail identifiant n'est ajouté.

## 5. Décision de revue

La PR peut être acceptée lorsque les critères sont satisfaits, retournée pour correction lorsque des points remédiables subsistent, ou refusée lorsque le changement est hors périmètre, insuffisamment justifié ou présente un risque inacceptable.

Les avis doivent être précis et liés à un problème vérifiable. Une approbation ne remplace pas les tests nécessaires.

## 6. Traçabilité

Le titre de PR et les commits doivent refléter l'objectif réel. La description inclut le périmètre, les vérifications, les impacts connus et les limites. Les changements techniques significatifs renvoient vers les documents concernés.

## 7. Références

- [GitHub — About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
- [GitHub — Reviewing proposed changes](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests)
- [Guide de rédaction](../00-Introduction/DOC-000-Writing-Guide.md)
- [Checklist qualité documentaire](./Documentation-Quality-Checklist.md)
