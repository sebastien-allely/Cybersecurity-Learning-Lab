# 03 - Authentification


| Élément | Valeur |
| **Nom du document** | `03-Authentification.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

L'authentification constitue la première barrière de protection des bases de données.

Une authentification robuste limite le risque de compromission des comptes SQL et réduit les conséquences d'une fuite d'identifiants.

---

# 2. Risques identifiés

Une authentification insuffisamment sécurisée peut entraîner :

- l'accès non autorisé aux bases ;
- une élévation de privilèges ;
- une fuite de données ;
- une compromission de l'application utilisant MariaDB.

---

# 3. Principes de conception

## Authentifier chaque utilisateur

Chaque compte doit être nominatif ou associé à une application clairement identifiée.

Les comptes partagés doivent être évités.

---

## Renforcer les secrets

Les mots de passe doivent respecter une politique de complexité adaptée.

Les secrets applicatifs doivent être protégés et ne jamais être stockés en clair dans des dépôts Git.

---

## Limiter les méthodes d'authentification

Seules les méthodes réellement nécessaires doivent être autorisées.

---

# 4. Décisions retenues

Le référentiel recommande :

- utiliser une authentification forte ;
- interdire les comptes anonymes ;
- limiter les connexions du compte `root` ;
- utiliser des comptes dédiés aux applications ;
- protéger les secrets applicatifs.

---

# 5. Vérification

Une revue régulière doit permettre de vérifier :

- les méthodes d'authentification utilisées ;
- les comptes disposant de privilèges élevés ;
- les mots de passe par défaut ;
- les comptes inactifs.

---

# 6. Supervision

Les événements suivants présentent une valeur opérationnelle :

- échecs répétés d'authentification ;
- connexion du compte root ;
- création d'un nouveau compte ;
- modification des privilèges.

---

# 7. Conclusion

Une authentification robuste constitue l'un des piliers de la sécurité de MariaDB.

Elle doit être régulièrement réévaluée dans le cadre du maintien en condition de sécurité.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27002.

## Documentation officielle

- MariaDB Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (authentification et gestion des accès).
