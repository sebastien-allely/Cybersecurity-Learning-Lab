# 03 - Authentification


| Élément | Valeur |
| **Nom du document** | `03-Authentification.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

L'authentification garantit que seuls les utilisateurs autorisés peuvent accéder aux ressources du domaine.

---

# 2. Risques identifiés

Les principaux risques sont :

- vol d'identifiants ;
- attaques par force brute ;
- Kerberoasting ;
- Pass-the-Hash ;
- Pass-the-Ticket.

---

# 3. Décisions retenues

Le référentiel recommande :

- utiliser Kerberos comme protocole principal ;
- limiter NTLM lorsque cela est compatible avec l'infrastructure ;
- appliquer une politique de mots de passe robuste ;
- verrouiller les comptes après plusieurs échecs ;
- protéger les comptes privilégiés.

---

# 4. Vérification

Une revue régulière doit vérifier :

- les stratégies de mot de passe ;
- les protocoles utilisés ;
- les comptes protégés ;
- les journaux d'authentification.

---

# 5. Supervision

Les événements suivants doivent être détectés :

- échecs d'authentification ;
- verrouillage de compte ;
- authentifications privilégiées ;
- utilisation anormale de NTLM.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- DNS
- Kerberos

## Dépendances fonctionnelles

- GLPI01
- ZABBIX01

## Dépendances de sécurité

- Supervision
- Journalisation

---

# 7. Conclusion

Une authentification robuste protège le référentiel d'identité contre les attaques les plus courantes.

---

# Références

- Microsoft Learn.
- Microsoft Security Baselines.
- ANSSI.
