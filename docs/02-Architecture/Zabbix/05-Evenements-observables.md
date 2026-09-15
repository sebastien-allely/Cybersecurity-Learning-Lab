# 05 - Événements observables


| Élément | Valeur |
| **Nom du document** | `05-Evenements-observables.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Identifier les événements permettant une détection rapide des anomalies de fonctionnement ou de sécurité.

---

# 2. Infrastructure

Les événements suivants présentent une valeur opérationnelle :

- arrêt du serveur ZABBIX01 ;
- arrêt de la base MariaDB ;
- indisponibilité Apache ;
- perte d'un agent.

---

# 3. Configuration

Les événements critiques sont :

- modification d'un Template ;
- modification d'un Trigger ;
- suppression d'un hôte ;
- modification d'un média de notification.

---

# 4. Sécurité

Les événements présentant une forte valeur sont :

- connexion administrateur ;
- échec d'authentification ;
- création d'un utilisateur ;
- modification d'un rôle ;
- création d'une clé API.

---

# 5. Supervision

Une attention particulière est portée aux UserParameters développés pour :

- Proxmox VE ;
- CrowdSec ;
- ClamAV ;
- NVMe ;
- sauvegardes vzdump.

---

# 6. Conclusion

Seuls les événements permettant une action opérationnelle sont retenus afin de limiter les faux positifs.
