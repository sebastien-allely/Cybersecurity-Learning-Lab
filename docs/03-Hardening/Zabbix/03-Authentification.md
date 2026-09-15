# 03 - Authentification


| Élément | Valeur |
| **Nom du document** | `03-Authentification.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


La protection de ces fichiers contribue à préserver la confidentialité des informations de configuration et à garantir une restauration rapide en cas d'incident.

---

# Mise en œuvre dans le laboratoire

Le laboratoire applique actuellement les principes suivants :

- authentification locale pour les administrateurs ;
- comptes nominatifs ;
- séparation des comptes administrateurs et des comptes utilisateurs ;
- utilisation de rôles pour limiter les privilèges ;
- aucune utilisation de comptes partagés.

L'intégration à un annuaire Active Directory pourra être envisagée lorsque le laboratoire évoluera vers une gestion centralisée des identités.

---

# Vérification

Les contrôles suivants doivent être réalisés régulièrement :

- identification des comptes inactifs ;
- vérification des rôles attribués ;
- contrôle des privilèges administrateurs ;
- revue des comptes de service ;
- contrôle des paramètres d'authentification après chaque mise à jour majeure.

---

# Supervision

Les événements suivants présentent un intérêt particulier :

- connexion réussie d'un administrateur ;
- échec d'authentification ;
- création d'un compte ;
- suppression d'un compte ;
- modification d'un rôle ;
- création ou suppression d'une clé API.

---

# Bonnes pratiques

Le laboratoire impose :

- un compte nominatif par administrateur ;
- l'interdiction des comptes partagés ;
- la documentation des comptes de service ;
- une revue périodique des comptes privilégiés.

---

# Dépendances

L'authentification dépend notamment des technologies suivantes :

- Apache HTTP Server ;
- MariaDB ;
- Active Directory (lorsqu'il est utilisé comme fournisseur d'identité) ;
- Ubuntu Server.

---

# Conclusion

La sécurisation de l'authentification constitue un prérequis indispensable à la protection de la plateforme ZABBIX01. Elle réduit les risques d'accès non autorisés tout en garantissant la traçabilité des opérations d'administration.

---

# Références

- Documentation officielle ZABBIX01.
- Guide d'hygiène informatique – ANSSI.
- NIST Cybersecurity Framework.
- SOCLE de Stéphane Robert (mesures applicables au système Linux hôte).
