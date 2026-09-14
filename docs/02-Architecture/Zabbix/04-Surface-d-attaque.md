# 04 - Surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les principaux éléments constituant la surface d'attaque de Zabbix. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Identifier les composants accessibles pouvant être exploités afin de réduire la surface d'attaque de la plateforme.

---

# 2. Services exposés

Les principaux services sont :

- interface Web ;
- serveur ZABBIX01 ;
- API ;
- Agent ZABBIX01 ;
- Agent ZABBIX01 2.

---

# 3. Interfaces d'administration

Les interfaces sensibles comprennent :

- console Web ;
- API REST ;
- fichiers de configuration ;
- base de données.

---

# 4. Composants critiques

Les éléments les plus sensibles sont :

- Templates ;
- Triggers ;
- Actions ;
- UserParameters ;
- Scripts ;
- Comptes administrateurs.

---

# 5. Réduction de la surface d'attaque

Le référentiel recommande :

- limiter l'accès à l'interface Web ;
- supprimer les composants inutilisés ;
- protéger les fichiers de configuration ;
- limiter les droits des utilisateurs ;
- contrôler les accès API.

---

# 6. Conclusion

La maîtrise de la surface d'attaque réduit le risque de compromission de la plateforme de supervision.
