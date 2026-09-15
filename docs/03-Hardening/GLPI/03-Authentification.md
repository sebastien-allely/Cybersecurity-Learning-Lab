# 03 - Authentification


| Élément | Valeur |
| **Nom du document** | `03-Authentification.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

L'authentification garantit que seuls les utilisateurs autorisés peuvent accéder à GLPI01.

Elle constitue la première ligne de défense contre les accès non autorisés.

---

# 2. Risques identifiés

- usurpation d'identité ;
- mots de passe faibles ;
- compromission LDAP ;
- comptes compromis ;
- attaques par force brute.

---

# 3. Décisions retenues

Le référentiel recommande :

- privilégier l'authentification LDAP ;
- appliquer une politique de mots de passe robuste ;
- désactiver les comptes inutilisés ;
- limiter les comptes locaux ;
- utiliser HTTPS pour toutes les authentifications.

---

# 4. Vérification

Une revue régulière doit vérifier :

- le bon fonctionnement de LDAP ;
- les comptes locaux ;
- les journaux d'authentification ;
- les paramètres HTTPS.

---

# 5. Supervision

Les événements suivants doivent être surveillés :

- échecs d'authentification ;
- verrouillage d'un compte ;
- indisponibilité LDAP ;
- connexion administrateur.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Apache HTTP Server
- PHP

## Dépendances de sécurité

- Active Directory
- ZABBIX01
- CrowdSec
- Fail2ban

---

# 7. Conclusion

Une authentification robuste réduit fortement les risques de compromission des comptes GLPI01.

---

# Références

- ANSSI – Guide d'hygiène informatique.
- Documentation GLPI01.
- Documentation Active Directory.
