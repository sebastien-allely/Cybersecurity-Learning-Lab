# 04 - Réduction de la surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Reduction-de-la-surface-d-attaque.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


Une sauvegarde régulière de ces fichiers permet de restaurer rapidement une configuration conforme en cas d'erreur ou de compromission.

---

# Mise en œuvre dans le laboratoire

Le laboratoire applique les principes suivants :

- accès à l'interface Web limité au réseau d'administration ;
- utilisation de **ZABBIX01 Agent 2** sur les systèmes Linux supervisés ;
- séparation des UserParameters par technologie dans `/etc/zabbix/zabbix_agent2.d/` ;
- limitation des privilèges `sudo` aux seules commandes nécessaires ;
- développement de UserParameters uniquement lorsque les métriques natives de ZABBIX01 ne répondent pas au besoin.

---

# Vérification

Les contrôles suivants doivent être réalisés périodiquement :

- liste des services exposés ;
- état des ports ouverts ;
- composants activés ;
- droits des fichiers de configuration ;
- privilèges accordés au compte `zabbix`.

---

# Supervision

Les événements suivants doivent être surveillés :

- arrêt du serveur ZABBIX01 ;
- arrêt de MariaDB ;
- arrêt d'Apache HTTP Server ;
- indisponibilité de ZABBIX01 Agent 2 ;
- modification des fichiers de configuration ;
- modification des UserParameters.

---

# Bonnes pratiques

Le laboratoire impose :

- un UserParameter par besoin identifié ;
- un fichier de configuration par technologie ;
- la documentation systématique de chaque personnalisation ;
- la suppression des composants devenus inutiles.

---

# Dépendances

Ce document est lié aux référentiels suivants :

- Apache HTTP Server ;
- MariaDB ;
- Ubuntu Server ;
- Proxmox VE ;
- Active Directory.

---

# Conclusion

La réduction de la surface d'attaque constitue l'une des mesures les plus efficaces pour limiter les possibilités de compromission de la plateforme ZABBIX01. Elle repose autant sur la désactivation des composants inutiles que sur une gestion rigoureuse des privilèges et des accès.

---

# Références

- Documentation officielle ZABBIX01.
- Guide d'hygiène informatique – ANSSI.
- NIST Cybersecurity Framework.
- SOCLE de Stéphane Robert (mesures de sécurisation du système Linux hôte).
