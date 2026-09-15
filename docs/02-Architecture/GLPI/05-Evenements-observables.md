# 05 - Événements observables


| Élément | Valeur |
| **Nom du document** | `05-Evenements-observables.md` |
| **Technologie** | GLPI |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les événements observables permettent de détecter une dégradation du service ou une activité anormale.

Ils constituent les indicateurs qui seront supervisés par ZABBIX01.

---

# 2. Disponibilité

Les événements suivants doivent être surveillés :

- arrêt d'Apache ;
- indisponibilité de GLPI01 ;
- indisponibilité de MariaDB ;
- saturation du serveur.

---

# 3. Authentification

Les événements suivants présentent une valeur opérationnelle :

- échecs d'authentification ;
- connexion administrateur ;
- verrouillage d'un compte ;
- création d'un nouveau compte.

---

# 4. Activité applicative

Les événements importants sont notamment :

- création d'un ticket ;
- suppression d'un équipement ;
- modification des droits ;
- import massif ;
- erreurs PHP.

---

# 5. Sécurité

Les événements suivants doivent être détectés :

- modification de la configuration ;
- changement des privilèges ;
- modification des plugins ;
- arrêt des journaux ;
- échec des sauvegardes.

---

# 6. Conclusion

Un événement n'est retenu que s'il permet une décision opérationnelle ou une investigation.
