# 03 - Analyse des risques


| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Architecture |
| **Objectif** | Analyser les risques associés à Zabbix et déterminer les mesures permettant de les réduire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

L'analyse des risques permet d'identifier les menaces susceptibles de compromettre la supervision du laboratoire.

---

# 2. Risques liés à la disponibilité

Les principaux risques sont :

- indisponibilité du serveur ZABBIX01 ;
- arrêt de la base de données ;
- panne de l'interface Web ;
- perte des communications avec les agents.

---

# 3. Risques liés à l'intégrité

Les principaux risques sont :

- modification non autorisée d'un Template ;
- suppression d'un Trigger ;
- altération des UserParameters ;
- modification des seuils d'alerte.

---

# 4. Risques liés à la confidentialité

Les principaux risques sont :

- divulgation des identifiants ;
- fuite des clés API ;
- exposition des informations d'infrastructure ;
- accès non autorisé aux tableaux de bord.

---

# 5. Conséquences

Une compromission de ZABBIX01 peut entraîner :

- une perte de visibilité sur l'état du laboratoire ;
- un retard dans la détection d'incidents ;
- une dégradation de la capacité d'investigation ;
- des alertes erronées ou absentes.

---

# 6. Conclusion

La disponibilité et l'intégrité de ZABBIX01 sont essentielles au maintien en condition opérationnelle et à la détection des incidents de sécurité.
