# 05 - Protection des données


| Élément | Valeur |
| **Nom du document** | `05-Protection-des-donnees.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les données constituent l'actif le plus important de GLPI01.

Le durcissement vise à garantir leur disponibilité, leur intégrité et leur confidentialité.

---

# 2. Actifs concernés

Les mesures concernent notamment :

- inventaire informatique ;
- tickets ;
- utilisateurs ;
- contrats ;
- licences ;
- documents ;
- base de connaissances ;
- historiques.

---

# 3. Risques identifiés

Les principaux risques sont :

- suppression accidentelle ;
- corruption de la base ;
- fuite d'informations ;
- ransomware ;
- accès non autorisé.

---

# 4. Décisions retenues

Le référentiel recommande :

- protéger les sauvegardes ;
- limiter les accès aux données ;
- sécuriser les fichiers de configuration ;
- utiliser HTTPS ;
- appliquer le principe du moindre privilège ;
- contrôler les accès administratifs.

---

# 5. Vérification

Une revue régulière doit vérifier :

- les sauvegardes ;
- les droits d'accès ;
- les permissions des fichiers ;
- la cohérence des rôles.

---

# 6. Supervision

Les événements suivants doivent être détectés :

- échec d'une sauvegarde ;
- modification des permissions ;
- restauration d'une sauvegarde ;
- accès administrateur inhabituel.

---

# 7. Dépendances avec les autres référentiels

## Dépendances techniques

- MariaDB
- Apache HTTP Server

## Dépendances de sécurité

- ZABBIX01
- AIDE

---

# 8. Conclusion

La protection des données constitue la finalité principale du durcissement de GLPI01.

---

# Références

- ANSSI – Guide d'hygiène informatique.
- Documentation GLPI01.
- Documentation MariaDB.
