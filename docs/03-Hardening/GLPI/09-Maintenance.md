# 09 - Maintenance


| Élément | Valeur |
| **Nom du document** | `09-Maintenance.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La maintenance garantit la pérennité des décisions de sécurité et assure la disponibilité durable de GLPI01.

---

# 2. Principes de conception

Le référentiel retient les principes suivants :

- documenter chaque intervention ;
- limiter les changements simultanés ;
- vérifier les sauvegardes avant toute opération ;
- conserver une configuration cohérente ;
- maintenir la documentation à jour.

---

# 3. Décisions retenues

Le référentiel recommande :

- contrôler régulièrement les comptes ;
- revoir les plugins installés ;
- vérifier les journaux ;
- tester les restaurations ;
- réévaluer périodiquement les droits d'accès ;
- maintenir les référentiels documentaires synchronisés avec l'infrastructure.

---

# 4. Vérification

Une revue périodique doit permettre de contrôler :

- les comptes ;
- les profils ;
- les sauvegardes ;
- les journaux ;
- les plugins ;
- la configuration générale.

---

# 5. Supervision

Les événements suivants présentent une valeur opérationnelle :

- échec d'une sauvegarde ;
- arrêt du service ;
- modification importante de configuration ;
- détection d'une dérive par AIDE.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Apache HTTP Server
- MariaDB
- Ubuntu Server

## Dépendances de sécurité

- ZABBIX01
- AIDE
- CrowdSec
- Fail2ban

---

# 7. Conclusion

Une maintenance régulière permet de conserver un niveau de sécurité cohérent tout au long du cycle de vie de GLPI01.

---

# Références

- Documentation GLPI01.
- Documentation Apache HTTP Server.
- Documentation MariaDB.
- SOCLE – Stéphane Robert.
