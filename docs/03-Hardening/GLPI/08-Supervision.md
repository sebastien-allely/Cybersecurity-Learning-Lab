# 08 - Supervision


| Élément | Valeur |
| **Nom du document** | `08-Supervision.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La supervision garantit la disponibilité de GLPI01 et permet de détecter les anomalies techniques ou de sécurité.

---

# 2. Actifs supervisés

Les principaux éléments supervisés sont :

- disponibilité de GLPI01 ;
- Apache HTTP Server ;
- PHP ;
- MariaDB ;
- LDAP ;
- certificats TLS ;
- espace disque ;
- sauvegardes.

---

# 3. Risques identifiés

Une supervision insuffisante peut entraîner :

- une indisponibilité prolongée ;
- une détection tardive d'un incident ;
- une perte de visibilité sur l'état de l'application.

---

# 4. Décisions retenues

Le référentiel recommande de superviser :

- le service Web ;
- le temps de réponse ;
- les erreurs HTTP ;
- les erreurs PHP ;
- les erreurs MariaDB ;
- les sauvegardes ;
- les certificats ;
- les journaux critiques.

---

# 5. Vérification

Une revue régulière doit contrôler :

- les seuils d'alerte ;
- les dépendances ;
- les faux positifs ;
- les indicateurs inutiles.

---

# 6. Supervision de la supervision

Le référentiel recommande également de superviser :

- l'agent ZABBIX01 ;
- les UserParameters ;
- la collecte des données.

---

# 7. Dépendances avec les autres référentiels

## Dépendances techniques

- Apache HTTP Server
- MariaDB

## Dépendances de sécurité

- ZABBIX01
- CrowdSec

---

# 8. Conclusion

La supervision permet de détecter rapidement les écarts de fonctionnement et contribue directement au maintien en condition opérationnelle.

---

# Références

- Documentation ZABBIX01.
- Documentation GLPI01.
- ANSSI – Guide d'hygiène informatique.
