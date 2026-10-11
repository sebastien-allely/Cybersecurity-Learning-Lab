# Architecture du dépôt

| Élément | Valeur |
|---|---|
| **Nom du document** | `Architecture-du-depot.md` |
| **Technologie** | Git et documentation |
| **Catégorie** | Gestion du projet |
| **Objectif** | Décrire l'organisation fonctionnelle du dépôt et les conventions qui facilitent sa maintenance. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

Le dépôt organise la documentation, les scripts, les ressources et les exercices du projet Cybersecurity-Learning-Lab. Cette architecture vise à rendre les contenus faciles à trouver, à relire et à faire évoluer.

## 2. Organisation générale

| Chemin | Rôle |
|---|---|
| `README.md` | Présentation du projet et point d'entrée |
| `PROJECT_CHARTER.md` | Objectifs et périmètre du projet |
| `CONTRIBUTING.md` | Règles de contribution |
| `SECURITY.md` | Signalement des problèmes de sécurité |
| `docs/00-Introduction/` | Introduction et guide de rédaction |
| `docs/01-Methode-de-conception/` | Méthode de conception et règles transverses |
| `docs/02-Architecture/` | Architecture des composants |
| `docs/03-Hardening/` | Procédures de durcissement |
| `docs/04-Protection/` | Mesures de protection |
| `docs/05-Monitoring/` | Supervision et détection |
| `docs/06-Incident-Response/` | Réponse aux incidents |
| `docs/07-Maintenance/` | Maintenance opérationnelle |
| `docs/09-Learning-Path/` | Parcours pédagogique |
| `docs/10-Appendices/` | Annexes |
| `docs/98-References/` | Sources et référentiels |
| `docs/99-Project-Management/` | Gouvernance, qualité et roadmap |
| `automation/` | Scripts d'automatisation classés par langage et fonction |
| `assets/` | Ressources complémentaires non sensibles |
| `labs/` | Exercices et scénarios de laboratoire |
| `zabbix/` | Modèles, paramètres et éléments associés à Zabbix |

Cette liste décrit les principaux emplacements ; l'arborescence du dépôt fait foi si elle évolue.

## 3. Conventions

- Les documents sont rédigés en français, sauf raison technique justifiée.
- Chaque document Markdown possède les sept champs de métadonnées obligatoires définis dans le guide de rédaction.
- Les noms de fichiers doivent être explicites, stables et cohérents avec leurs titres internes.
- Les scripts sont classés par langage et par objectif.
- Les ressources doivent être nécessaires, licites et dépourvues de données confidentielles.
- Les procédures mentionnent prérequis, impact, résultats attendus, validation et retour arrière lorsque pertinent.

## 4. Gestion Git

Les changements sont réalisés sur une branche dédiée puis proposés par Pull Request vers `main`. La revue vérifie le fond technique, la qualité rédactionnelle, les liens, l'anonymisation et les tests nécessaires. Les commits doivent décrire leur intention.

## 5. Séparation entre documentation et environnement réel

Le dépôt public ne doit contenir aucune donnée permettant d'identifier l'environnement privé : adresses réelles, domaines internes, noms d'hôtes, comptes, chemins personnels, partages, secrets, clés privées ou données de supervision identifiantes. Utiliser des exemples fictifs cohérents.

## 6. Références

- [Guide de rédaction](../00-Introduction/DOC-000-Writing-Guide.md)
- [Processus de contribution et de revue](./Contribution-Review-Process.md)
- [Checklist qualité documentaire](./Documentation-Quality-Checklist.md)
- [Roadmap](./ROADMAP.md)
- [GitHub Docs — Git](https://docs.github.com/en/get-started/using-git/about-git)
