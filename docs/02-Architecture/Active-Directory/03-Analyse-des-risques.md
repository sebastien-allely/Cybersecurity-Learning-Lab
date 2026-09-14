# 03 - Analyse des risques


| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Architecture |
| **Objectif** | Analyser les risques associés à Active Directory et déterminer les mesures permettant de les réduire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

L'analyse des risques permet d'identifier les menaces pesant sur le référentiel d'identité et de justifier les mesures de sécurité retenues.

---

# 2. Risques liés à la disponibilité

Les principaux risques sont :

- arrêt du contrôleur de domaine ;
- panne du service DNS ;
- corruption de SYSVOL ;
- perte de la base NTDS.dit ;
- indisponibilité du réseau.

---

# 3. Risques liés à l'intégrité

Une altération des données peut entraîner :

- modification des GPO ;
- corruption de l'annuaire ;
- modification des groupes de sécurité ;
- élévation de privilèges.

---

# 4. Risques liés à la confidentialité

Une compromission peut conduire à la divulgation :

- des identités ;
- des groupes ;
- des secrets d'authentification ;
- des informations sur l'infrastructure.

---

# 5. Risques liés aux comptes privilégiés

Les risques majeurs concernent :

- compromission d'un Domain Admin ;
- création d'un compte privilégié non autorisé ;
- délégation excessive de droits ;
- comptes de service mal sécurisés.

---

# 6. Conséquences

Une compromission d'Active Directory peut entraîner :

- la compromission de l'ensemble du domaine ;
- la perte de confiance dans les identités ;
- l'accès aux ressources protégées ;
- la propagation d'une attaque vers les autres systèmes.

---

# 7. Conclusion

Active Directory constitue l'un des actifs les plus critiques du laboratoire. Les décisions de sécurité qui lui sont appliquées visent à limiter les risques de compromission des identités et des privilèges.
