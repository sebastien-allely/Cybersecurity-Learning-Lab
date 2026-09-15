# 09 - Maintenance


| Élément | Valeur |
| **Nom du document** | `09-Maintenance.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Objectif

Maintenir la plateforme dans un état conforme aux exigences de sécurité et de disponibilité du laboratoire.

---

# Référentiel

Le référentiel recommande :

- documenter chaque modification ;
- tester les sauvegardes ;
- supprimer les éléments obsolètes ;
- contrôler les performances ;
- vérifier les journaux ;
- contrôler les droits des comptes ;
- tester les procédures de restauration.

## Risques couverts

- dérive de configuration ;
- perte des connaissances ;
- augmentation de la dette technique.

## Bénéfices

- amélioration de la maintenabilité ;
- réduction du temps d'intervention ;
- amélioration de la disponibilité.

---

# Mise en œuvre dans le laboratoire

Le laboratoire :

- documente les évolutions dans GitHub ;
- conserve l'historique des modifications ;
- met à jour les Templates personnalisés ;
- contrôle régulièrement les UserParameters ;
- vérifie les sauvegardes Proxmox ;
- met à jour la documentation après chaque évolution importante.

---

# Vérification

Contrôler périodiquement :

- cohérence des Templates ;
- éléments obsolètes ;
- scripts personnalisés ;
- documentation ;
- sauvegardes.

---

# Conclusion

La maintenance garantit que le niveau de sécurité obtenu lors du déploiement est conservé dans le temps.

---

# Références

- Documentation ZABBIX01
- ANSSI
- SOCLE Stéphane Robert
