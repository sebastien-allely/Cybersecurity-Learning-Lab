# 06 - Journalisation


| Élément | Valeur |
| **Nom du document** | `06-Journalisation.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Mise en œuvre dans le laboratoire

Le laboratoire :

- conserve les journaux locaux ;
- supervise la disponibilité des services ;
- exploite ZABBIX01 pour détecter les anomalies ;
- documente les événements importants.

---

# Vérification

Contrôler régulièrement :

- la présence des journaux ;
- les droits d'accès ;
- l'espace disque ;
- la rotation des logs.

---

# Supervision

Surveiller :

- arrêt de la journalisation ;
- saturation disque ;
- erreurs répétées ;
- rotation anormale.

---

# Conclusion

La journalisation constitue la mémoire de la plateforme et représente un élément essentiel pour la sécurité et l'exploitation.

---

# Références

- Documentation ZABBIX01
- Documentation systemd-journald
- ANSSI
- SOCLE Stéphane Robert
