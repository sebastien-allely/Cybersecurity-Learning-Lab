# 01 - Justification de l'outil


| Élément | Valeur |
| **Nom du document** | `01-Justification-de-l-outil.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

ZABBIX01 assure la supervision technique et opérationnelle de l'ensemble du laboratoire.

Il permet la collecte des métriques, la surveillance des services, le déclenchement d'alertes et la centralisation des événements.

---

# 2. Pourquoi ZABBIX01 ?

Le choix repose notamment sur :

- logiciel Open Source ;
- supervision distribuée ;
- supervision agent et agentless ;
- extensibilité grâce aux UserParameters ;
- API REST ;
- forte capacité de personnalisation.

---

# 3. Services assurés

La plateforme supervise notamment :

- Proxmox VE ;
- Active Directory ;
- GLPI01 ;
- Apache ;
- MariaDB ;
- Linux ;
- Windows ;
- CrowdSec ;
- ClamAV ;
- Fail2ban.

---

# 4. Justification de sécurité

ZABBIX01 améliore :

- la détection précoce des incidents ;
- la disponibilité des services ;
- la visibilité sur l'état du laboratoire ;
- la capacité d'investigation.

---

# 5. Conclusion

La supervision constitue une mesure de sécurité transverse indispensable au fonctionnement du laboratoire.
