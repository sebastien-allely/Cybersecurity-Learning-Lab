# 05 - Protection des données


| Élément | Valeur |
| **Nom du document** | `05-Protection-des-donnees.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les données stockées par Active Directory constituent le cœur du référentiel d'identité.

Leur protection garantit la disponibilité, l'intégrité et la confidentialité des identités du laboratoire.

---

# 2. Actifs concernés

Les principaux actifs sont :

- base NTDS.dit ;
- SYSVOL ;
- objets Active Directory ;
- comptes utilisateurs ;
- groupes ;
- GPO ;
- enregistrements DNS intégrés ;
- sauvegardes de l'état système.

---

# 3. Risques identifiés

Les principaux risques sont :

- extraction de NTDS.dit ;
- altération des GPO ;
- suppression d'objets Active Directory ;
- compromission des sauvegardes ;
- chiffrement malveillant des données.

---

# 4. Décisions retenues

Le référentiel recommande :

- protéger les sauvegardes ;
- limiter les accès administratifs ;
- contrôler les permissions NTFS ;
- restreindre l'accès physique au contrôleur de domaine ;
- vérifier régulièrement l'intégrité des sauvegardes.

---

# 5. Vérification

Une revue régulière doit contrôler :

- les sauvegardes ;
- les permissions ;
- les groupes privilégiés ;
- les objets critiques.

---

# 6. Supervision

Les événements suivants doivent être détectés :

- suppression d'une GPO ;
- modification d'un groupe privilégié ;
- suppression d'une OU ;
- échec d'une sauvegarde.

---

# 7. Dépendances avec les autres référentiels

## Dépendances techniques

- Windows Server

## Dépendances fonctionnelles

- GLPI01

## Dépendances de sécurité

- Sauvegardes
- Journalisation
- ZABBIX01

---

# 8. Conclusion

La protection des données d'Active Directory conditionne directement la confiance accordée aux identités du domaine.

---

# Références

- Microsoft Learn.
- ANSSI.
