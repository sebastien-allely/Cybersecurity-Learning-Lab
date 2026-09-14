# 03 - Analyse des risques


| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | GLPI |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

L'analyse des risques permet de justifier les décisions de sécurité appliquées à GLPI01.

---

# 2. Risques liés à la disponibilité

Les principaux risques sont :

- arrêt d'Apache ;
- indisponibilité de MariaDB ;
- panne du système d'exploitation ;
- saturation des ressources ;
- erreur de configuration.

---

# 3. Risques liés à l'intégrité

Une altération des données peut entraîner :

- un inventaire erroné ;
- des tickets modifiés ;
- une perte d'historique ;
- des erreurs de gestion.

---

# 4. Risques liés à la confidentialité

Une compromission peut conduire à la divulgation :

- des informations sur le parc informatique ;
- des comptes utilisateurs ;
- des documents internes ;
- des contrats ;
- des licences.

---

# 5. Risques liés aux comptes

Les principaux risques sont :

- élévation de privilèges ;
- mots de passe faibles ;
- comptes oubliés ;
- erreurs d'attribution des rôles.

---

# 6. Conséquences

Une compromission de GLPI01 peut affecter :

- la gestion du parc ;
- le support utilisateur ;
- la qualité des inventaires ;
- la capacité de supervision et d'administration.

---

# 7. Conclusion

Les décisions de sécurité du référentiel visent à préserver la disponibilité, l'intégrité et la confidentialité des données métier centralisées par GLPI01.
