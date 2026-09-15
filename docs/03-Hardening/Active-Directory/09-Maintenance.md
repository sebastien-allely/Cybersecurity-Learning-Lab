# 08 - Supervision


| Élément | Valeur |
| **Nom du document** | `09-Maintenance.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La supervision garantit une détection rapide des incidents techniques et des événements de sécurité affectant Active Directory.

---

# 2. Actifs supervisés

Les principaux éléments supervisés sont :

- contrôleur de domaine ;
- services Active Directory ;
- DNS ;
- Kerberos ;
- LDAP ;
- SYSVOL ;
- espace disque ;
- sauvegardes ;
- synchronisation temporelle (NTP).

---

# 3. Risques identifiés

Une supervision insuffisante peut entraîner :

- une indisponibilité prolongée ;
- une détection tardive d'une compromission ;
- une perte de visibilité sur l'état du domaine.

---

# 4. Décisions retenues

Le référentiel recommande de superviser :

- les services Active Directory ;
- le service DNS ;
- la réplication (si plusieurs contrôleurs) ;
- l'espace disque ;
- les journaux Windows ;
- les sauvegardes ;
- les certificats si des services PKI sont ajoutés ultérieurement.

---

# 5. Vérification

Une revue régulière doit contrôler :

- les seuils d'alerte ;
- les dépendances ;
- les faux positifs ;
- les indicateurs devenus obsolètes.

---

# 6. Supervision de la supervision

Le référentiel recommande également de superviser :

- l'agent ZABBIX01 ;
- les UserParameters ;
- la collecte des journaux ;
- les tâches planifiées de supervision.

---

# 7. Dépendances avec les autres référentiels

## Dépendances techniques

- Windows Server

## Dépendances fonctionnelles

- ZABBIX01

## Dépendances de sécurité

- Journalisation
- Sauvegardes

---

# 8. Conclusion

Une supervision pertinente réduit le délai de détection des incidents et facilite leur traitement.

---

# Références

- Documentation ZABBIX01.
- Microsoft Learn.
- ANSSI.
