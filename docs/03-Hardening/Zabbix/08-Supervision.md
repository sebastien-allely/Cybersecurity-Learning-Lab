# 08 - Supervision


| Élément | Valeur |
| **Nom du document** | `08-Supervision.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Objectif

Garantir que la plateforme supervise en permanence ses propres composants critiques.

---

# Définition

Une plateforme de supervision doit être capable de détecter ses propres défaillances.

Cette approche est appelée « auto-supervision ».

---

# Référentiel

Le référentiel recommande de superviser :

- disponibilité du serveur ;
- disponibilité des agents ;
- disponibilité d'Apache ;
- disponibilité de MariaDB ;
- espace disque ;
- mémoire ;
- CPU ;
- certificats TLS ;
- sauvegardes ;
- intégrité des fichiers critiques.

## Risques couverts

- perte de visibilité ;
- faux sentiment de sécurité ;
- détection tardive d'une panne.

---

# Mise en œuvre dans le laboratoire

Le laboratoire supervise notamment :

- CrowdSec ;
- ClamAV ;
- sauvegardes Proxmox ;
- NVMe ;
- UserParameters ;
- quorum Proxmox ;
- AIDE ;
- Fail2ban ;
- journaux critiques.

Les développements spécifiques sont regroupés dans des Templates personnalisés afin de faciliter leur maintenance.

---

# Vérification

Contrôler :

- faux positifs ;
- faux négatifs ;
- fréquence de collecte ;
- dépendances entre Triggers.

---

# Bonnes pratiques

Le laboratoire applique :

- dépendances entre Triggers ;
- Templates spécialisés ;
- UserParameters documentés ;
- seuils adaptés au laboratoire.

---

# Conclusion

Une plateforme de supervision qui ne supervise pas son propre fonctionnement ne peut pas garantir la fiabilité des alertes qu'elle produit.

---

# Références

- Documentation ZABBIX01
- ANSSI
- SOCLE Stéphane Robert
