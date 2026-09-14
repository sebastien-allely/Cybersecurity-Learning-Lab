# 02 - Gestion des comptes


| Élément | Valeur |
| **Nom du document** | `02-Gestion-des-comptes.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les comptes utilisateurs permettent l'accès aux informations métier de GLPI01.

Leur gestion doit garantir une authentification fiable et une attribution rigoureuse des privilèges.

---

# 2. Risques identifiés

- compte administrateur compromis ;
- privilèges excessifs ;
- comptes oubliés ;
- comptes partagés ;
- comptes inactifs.

---

# 3. Décisions retenues

Le référentiel recommande :

- utiliser des comptes nominatifs ;
- limiter le nombre d'administrateurs ;
- supprimer les comptes inutilisés ;
- attribuer les rôles selon les besoins métiers ;
- documenter les comptes privilégiés.

---

# 4. Vérification

Une revue régulière doit contrôler :

- les comptes actifs ;
- les rôles attribués ;
- les comptes inactifs ;
- les comptes administrateurs.

---

# 5. Supervision

Les événements suivants présentent une valeur opérationnelle :

- création d'un compte ;
- suppression d'un compte ;
- changement de rôle ;
- connexion administrateur.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- GLPI01
- MariaDB

## Dépendances de sécurité

- Active Directory (LDAP)
- ZABBIX01

---

# 7. Conclusion

Une gestion rigoureuse des comptes constitue l'une des mesures les plus efficaces pour limiter les risques liés aux accès non autorisés.

---

# Références

- ANSSI – Guide d'hygiène informatique.
- Documentation GLPI01.
- Documentation LDAP.
