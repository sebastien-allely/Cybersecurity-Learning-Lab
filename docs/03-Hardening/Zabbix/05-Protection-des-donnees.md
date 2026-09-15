# 05 - Protection des données


| Élément | Valeur |
| **Nom du document** | `05-Protection-des-donnees.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Mise en œuvre dans le laboratoire

Le laboratoire applique les mesures suivantes :

- les fichiers de configuration sont intégrés aux sauvegardes des machines virtuelles ;
- les communications entre les composants utilisent HTTPS pour l'interface Web ;
- les UserParameters sont répartis par technologie afin d'en faciliter l'administration et l'audit ;
- les privilèges du compte `zabbix` sont limités aux commandes strictement nécessaires ;
- les sauvegardes Proxmox permettent une restauration complète de la plateforme en cas d'incident.

---

# Vérification

Les points suivants doivent être contrôlés régulièrement :

- permissions des fichiers de configuration ;
- présence des sauvegardes ;
- capacité à restaurer une sauvegarde ;
- protection des accès à MariaDB ;
- protection des accès à l'interface Web ;
- validité des certificats TLS ;
- présence des fichiers de configuration attendus.

---

# Supervision

Les éléments suivants doivent faire l'objet d'une supervision :

- disponibilité du serveur ZABBIX01 ;
- disponibilité de MariaDB ;
- disponibilité d'Apache HTTP Server ;
- état des sauvegardes ;
- intégrité des fichiers de configuration ;
- occupation de l'espace disque utilisé par les historiques et les tendances ;
- expiration des certificats TLS.

---

# Bonnes pratiques

Le laboratoire applique les principes suivants :

- limiter l'accès à la base de données aux seuls composants autorisés ;
- documenter chaque fichier de configuration personnalisé ;
- sauvegarder les données avant toute modification importante ;
- tester régulièrement la restauration des sauvegardes ;
- protéger les secrets et les identifiants d'administration.

---

# Dépendances

La protection des données dépend directement des technologies suivantes :

- Apache HTTP Server ;
- MariaDB ;
- Ubuntu Server ;
- Proxmox VE ;
- Active Directory (si utilisé pour l'authentification) ;
- Solution de sauvegarde de l'infrastructure.

---

# Conclusion

La protection des données constitue l'un des piliers de la sécurité de la plateforme ZABBIX01. Elle garantit non seulement la confidentialité des informations collectées, mais également la capacité à restaurer rapidement un environnement fonctionnel après un incident.

---

# Références

- Documentation officielle ZABBIX01.
- Documentation officielle MariaDB.
- Guide d'hygiène informatique – ANSSI.
- NIST Cybersecurity Framework.
- SOCLE de Stéphane Robert (mesures applicables au système Linux hôte).
