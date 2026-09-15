# 04 - Réduction de la surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Reduction-de-la-surface-d-attaque.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Réduire la surface d'attaque consiste à limiter les fonctionnalités, services et composants exposés aux seuls besoins du système.

---

# 2. Risques identifiés

Une surface d'attaque excessive favorise :

- l'exploitation de vulnérabilités ;
- les erreurs de configuration ;
- les accès non autorisés ;
- l'augmentation de la dette technique.

---

# 3. Décisions retenues

Le référentiel recommande :

- supprimer les comptes inutilisés ;
- supprimer les bases de test ;
- supprimer les plugins inutiles ;
- limiter les privilèges ;
- restreindre l'écoute réseau lorsque cela est possible ;
- désactiver les fonctionnalités inutilisées.

---

# 4. Vérification

Une revue régulière doit permettre de contrôler :

- les plugins installés ;
- les comptes SQL ;
- les bases présentes ;
- les interfaces réseau utilisées ;
- les services dépendants.

---

# 5. Supervision

Les éléments suivants doivent être détectés :

- apparition d'un nouveau plugin ;
- création d'une nouvelle base ;
- ouverture d'un nouveau port ;
- modification de la configuration réseau.

---

# 6. Conclusion

La réduction de la surface d'attaque constitue une mesure simple permettant de diminuer significativement le risque d'exploitation.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ISO/IEC 27002.

## Documentation officielle

- MariaDB Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (réduction de la surface d'attaque).
