# 06 - Journalisation


| Élément | Valeur |
| **Nom du document** | `06-Journalisation.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La journalisation permet de détecter les activités anormales, de faciliter les investigations et de disposer de preuves lors d'un incident de sécurité.

---

# 2. Événements critiques

Le référentiel recommande de journaliser notamment :

- les ouvertures de session ;
- les échecs d'authentification ;
- les modifications de groupes privilégiés ;
- les créations et suppressions d'utilisateurs ;
- les modifications des GPO ;
- les changements de configuration de l'audit.

---

# 3. Décisions retenues

Le référentiel recommande :

- activer les stratégies d'audit avancées ;
- conserver les journaux suffisamment longtemps pour permettre les investigations ;
- protéger les journaux contre toute suppression ou modification ;
- synchroniser l'heure des systèmes afin de garantir la cohérence temporelle des événements.

---

# 4. Vérification

Une revue régulière doit contrôler :

- les stratégies d'audit ;
- la taille des journaux ;
- la rétention ;
- les échecs de collecte.

---

# 5. Supervision

Les alertes doivent notamment concerner :

- l'arrêt du service Journal des événements ;
- la suppression d'un journal ;
- une modification des stratégies d'audit ;
- une activité anormale sur les comptes privilégiés.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Windows Server

## Dépendances fonctionnelles

- ZABBIX01

## Dépendances de sécurité

- Supervision
- Sauvegardes

---

# 7. Conclusion

Une journalisation pertinente améliore considérablement les capacités de détection, d'investigation et de réponse aux incidents.

---

# Références

- Microsoft Learn.
- ANSSI.
- Microsoft Security Baselines.
