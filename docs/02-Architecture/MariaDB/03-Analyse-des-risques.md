# 03 - Analyse des risques


| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Architecture |
| **Objectif** | Analyser les risques associés à MariaDB et déterminer les mesures permettant de les réduire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Objectif

Identifier les risques pesant sur MariaDB afin de justifier les décisions de sécurité.

---

# Risques liés à la disponibilité

- arrêt du service ;
- corruption InnoDB ;
- saturation des connexions ;
- panne disque ;
- restauration impossible.

---

# Risques liés à la confidentialité

- fuite de données ;
- compromission des comptes SQL ;
- interception des communications ;
- accès non autorisés.

---

# Risques liés à l'intégrité

- suppression accidentelle ;
- modification malveillante ;
- corruption logique ;
- ransomware.

---

# Risques liés à l'administration

- privilèges excessifs ;
- comptes inutilisés ;
- absence de traçabilité ;
- erreurs de configuration.

---

# Conséquences

Une compromission de MariaDB peut provoquer :

- l'indisponibilité de GLPI01 ;
- une perte de données ;
- une perte de confidentialité ;
- une compromission d'autres services.

---

# Conclusion

Les décisions de sécurité du référentiel visent à réduire ces risques tout en préservant la disponibilité de la base.
