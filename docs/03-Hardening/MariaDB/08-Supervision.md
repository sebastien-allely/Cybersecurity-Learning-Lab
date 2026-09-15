# 08 - Supervision


| Élément | Valeur |
| **Nom du document** | `08-Supervision.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La supervision permet de vérifier que les décisions de sécurité restent efficaces dans le temps et de détecter rapidement toute anomalie.

Le référentiel privilégie une supervision orientée risque.

---

# 2. Actifs concernés

La supervision porte notamment sur :

- le service MariaDB ;
- les bases de données ;
- les comptes SQL ;
- les sauvegardes ;
- les journaux ;
- les ressources système.

---

# 3. Risques identifiés

Une supervision inadaptée peut entraîner :

- une détection tardive d'une indisponibilité ;
- une perte de visibilité sur les événements de sécurité ;
- des faux positifs ;
- une incapacité à réagir rapidement.

---

# 4. Décisions retenues

Le référentiel recommande de superviser :

- la disponibilité du service ;
- les erreurs critiques ;
- les échecs d'authentification ;
- les connexions privilégiées ;
- les sauvegardes ;
- l'espace disque ;
- les performances essentielles ;
- l'intégrité des fichiers de configuration (AIDE).

Chaque indicateur doit être associé à un risque identifié.

---

# 5. Vérification

Une revue régulière doit vérifier :

- la pertinence des indicateurs ;
- les seuils d'alerte ;
- les dépendances entre alertes ;
- le niveau de faux positifs.

---

# 6. Supervision de la supervision

Le référentiel recommande également de superviser :

- l'agent ZABBIX01 ;
- la remontée des données ;
- les contrôles planifiés.

---

# 7. Conclusion

Une supervision pertinente ne mesure pas tout. Elle mesure ce qui permet une décision opérationnelle.

---

# Références

- ANSSI – Guide d'hygiène informatique.
- Documentation ZABBIX01.
- Documentation MariaDB.
- SOCLE – Stéphane Robert.
