# 02 - Gestion des comptes


| Élément | Valeur |
| **Nom du document** | `02-Gestion-des-comptes.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les comptes représentent le principal vecteur d'accès aux ressources du domaine.

Leur gestion doit garantir une authentification fiable et une attribution rigoureuse des privilèges.

---

# 2. Risques identifiés

Les principaux risques sont :

- comptes administrateurs compromis ;
- comptes inactifs ;
- comptes partagés ;
- privilèges excessifs ;
- comptes de service mal configurés.

---

# 3. Décisions retenues

Le référentiel recommande :

- utiliser des comptes nominatifs ;
- disposer de comptes d'administration dédiés ;
- interdire les comptes partagés ;
- supprimer les comptes inutilisés ;
- documenter les comptes de service ;
- appliquer le principe du moindre privilège.

---

# 4. Vérification

Une revue régulière doit contrôler :

- les groupes privilégiés ;
- les comptes désactivés ;
- les comptes expirés ;
- les comptes de service.

---

# 5. Supervision

Les événements suivants présentent une valeur opérationnelle :

- création d'un compte ;
- suppression d'un compte ;
- ajout à Domain Admins ;
- modification d'un groupe privilégié.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Windows Server

## Dépendances fonctionnelles

- GLPI01

## Dépendances de sécurité

- ZABBIX01

---

# 7. Conclusion

Une gestion rigoureuse des comptes constitue le premier rempart contre la compromission du domaine.

---

# Références

- ANSSI – Active Directory.
- Microsoft Learn.
