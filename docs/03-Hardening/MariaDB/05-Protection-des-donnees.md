# 05 - Protection des données


| Élément | Valeur |
| **Nom du document** | `05-Protection-des-donnees.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les données représentent l'actif principal protégé par MariaDB.

Leur protection constitue l'objectif prioritaire du durcissement.

---

# 2. Risques identifiés

Les principaux risques sont :

- fuite de données ;
- corruption ;
- suppression accidentelle ;
- ransomware ;
- accès non autorisé.

---

# 3. Décisions retenues

Le référentiel recommande :

- protéger les fichiers de données ;
- protéger les sauvegardes ;
- sécuriser les fichiers de configuration ;
- utiliser TLS lorsque des connexions réseau sont nécessaires ;
- limiter les accès aux seuls comptes autorisés.

---

# 4. Vérification

Une revue régulière doit vérifier :

- les permissions des fichiers ;
- les droits d'accès ;
- la protection des sauvegardes ;
- la cohérence des privilèges SQL.

---

# 5. Supervision

Les événements suivants doivent être détectés :

- modification inattendue des fichiers de données ;
- échec d'une sauvegarde ;
- restauration d'une sauvegarde ;
- modification des privilèges sur les bases.

---

# 6. Conclusion

La protection des données constitue la finalité première de la sécurisation de MariaDB.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ISO/IEC 27002.

## Documentation officielle

- MariaDB Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (protection des données et sauvegardes).
