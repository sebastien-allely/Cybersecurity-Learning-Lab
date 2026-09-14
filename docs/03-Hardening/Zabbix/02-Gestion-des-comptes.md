# 02 - Gestion des comptes


| Élément | Valeur |
| **Nom du document** | `02-Gestion-des-comptes.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


La protection de ces fichiers contribue à garantir la confidentialité des informations sensibles, tandis que leur sauvegarde permet une restauration rapide en cas d'incident ou d'erreur de configuration.

---

# Mise en œuvre dans le laboratoire

Le laboratoire applique les principes suivants :

- comptes administrateurs distincts des comptes utilisateurs ;
- limitation du nombre de comptes disposant de privilèges élevés ;
- utilisation de ZABBIX01 Agent 2 sur les machines Linux ;
- utilisation de règles `sudo` limitées aux commandes strictement nécessaires pour les UserParameters ;
- séparation des UserParameters par technologie dans le répertoire `/etc/zabbix/zabbix_agent2.d/`.

---

# Vérification

Il convient de vérifier régulièrement :

- les comptes actifs ;
- les rôles attribués ;
- les droits des comptes administrateurs ;
- les autorisations du compte système `zabbix` ;
- le contenu du fichier `/etc/sudoers.d/zabbix`.

---

# Supervision

Les événements suivants présentent un intérêt particulier :

- création d'un compte ;
- suppression d'un compte ;
- modification d'un rôle ;
- échec répété d'authentification ;
- création d'une clé API.

---

# Bonnes pratiques

Le référentiel recommande également de :

- documenter chaque compte privilégié ;
- utiliser des mots de passe robustes ou une authentification fédérée lorsqu'elle est disponible ;
- supprimer les comptes de test ;
- limiter l'utilisation du compte Super Admin ;
- contrôler périodiquement les privilèges.

---

# Dépendances

Ce document est lié aux référentiels suivants :

- Active Directory ;
- Apache HTTP Server ;
- MariaDB ;
- Ubuntu Server.

---

# Conclusion

Une gestion rigoureuse des comptes constitue l'un des fondements de la sécurité de la plateforme ZABBIX01. Elle limite les risques d'accès non autorisés et améliore la traçabilité des actions d'administration.

---

# Références

- Documentation officielle ZABBIX01.
- Guide d'hygiène informatique – ANSSI.
- NIST Cybersecurity Framework.
- SOCLE de Stéphane Robert (principes applicables au système Linux hôte).
