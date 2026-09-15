# 01 - Justification de l'outil


| Élément | Valeur |
| **Nom du document** | `01-Justification-de-l-outil.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Objectif

MariaDB est le système de gestion de bases de données relationnelles retenu pour le laboratoire.

Ce choix repose sur des critères techniques, opérationnels et de sécurité.

---

# Pourquoi MariaDB ?

MariaDB est :

- Open Source ;
- mature ;
- largement déployé ;
- compatible avec de nombreuses applications (notamment GLPI01) ;
- maintenu activement ;
- disponible dans les dépôts Debian et Ubuntu.

---

# Pourquoi pas un autre SGBD ?

Le choix d'un SGBD dépend des besoins.

Dans le cadre du laboratoire :

- PostgreSQL apporte des fonctionnalités avancées mais non nécessaires aux objectifs pédagogiques.
- SQLite est destiné aux applications embarquées.
- Oracle Database introduit une complexité et un coût injustifiés.

MariaDB représente donc le meilleur compromis entre simplicité, sécurité et maintenabilité.

---

# Justification de sécurité

MariaDB permet notamment :

- une gestion fine des privilèges ;
- une authentification robuste ;
- une journalisation des événements ;
- le chiffrement des communications ;
- une intégration simple avec les mécanismes de sauvegarde ;
- une supervision efficace.

Ces capacités répondent aux objectifs du laboratoire.

---

# Conclusion

MariaDB est retenu car il répond aux besoins fonctionnels tout en permettant une conception cohérente de la sécurité.

Il constitue une brique essentielle de l'infrastructure.
