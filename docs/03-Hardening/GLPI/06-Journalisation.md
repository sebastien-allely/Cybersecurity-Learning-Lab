# 06 - Journalisation


| Élément | Valeur |
| **Nom du document** | `06-Journalisation.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La journalisation permet de conserver une trace des actions importantes réalisées dans GLPI01 afin de faciliter les investigations, les audits et la détection d'incidents.

---

# 2. Risques identifiés

Une journalisation insuffisante peut entraîner :

- une perte de traçabilité ;
- une détection tardive d'un incident ;
- une difficulté à établir une chronologie des événements ;
- une impossibilité de réaliser un audit fiable.

---

# 3. Décisions retenues

Le référentiel recommande :

- conserver les journaux applicatifs ;
- journaliser les connexions administratives ;
- tracer les modifications des droits ;
- journaliser les opérations sensibles ;
- protéger les journaux contre toute altération.

---

# 4. Vérification

Une revue régulière doit vérifier :

- la présence des journaux ;
- leur intégrité ;
- leur rotation ;
- leur durée de conservation.

---

# 5. Supervision

Les événements suivants présentent une valeur opérationnelle :

- arrêt de la journalisation ;
- erreur critique de GLPI01 ;
- modification des privilèges ;
- suppression d'un journal.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Apache HTTP Server
- MariaDB

## Dépendances de sécurité

- ZABBIX01
- AIDE

---

# 7. Conclusion

Une journalisation pertinente améliore la capacité à détecter, comprendre et traiter les incidents de sécurité.

---

# Références

- ANSSI – Guide d'hygiène informatique.
- Documentation GLPI01.
- Documentation Apache HTTP Server.
- Documentation MariaDB.
