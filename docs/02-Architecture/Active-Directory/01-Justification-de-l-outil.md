# 01 - Justification de l'outil


| Élément | Valeur |
| **Nom du document** | `01-Justification-de-l-outil.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Active Directory Domain Services (AD01 DS) est le service d'identité retenu pour le laboratoire.

Il centralise les comptes, les groupes, les ordinateurs et les politiques de sécurité.

---

# 2. Pourquoi Active Directory ?

Le choix repose sur plusieurs critères :

- standard de fait dans les environnements Microsoft ;
- authentification centralisée ;
- gestion centralisée des autorisations ;
- administration des stratégies de groupe (GPO) ;
- intégration native avec Windows ;
- compatibilité LDAP avec GLPI01.

---

# 3. Services assurés

Le contrôleur de domaine fournit les services suivants :

- Active Directory Domain Services ;
- LDAP ;
- Kerberos ;
- DNS intégré ;
- stratégies de groupe (GPO).

---

# 4. Justification de sécurité

Active Directory permet :

- une authentification centralisée ;
- une gestion cohérente des droits ;
- une application homogène des politiques de sécurité ;
- une traçabilité des actions d'administration.

---

# 5. Conclusion

Active Directory constitue le socle de confiance du laboratoire. Toute compromission du contrôleur de domaine aurait un impact majeur sur l'ensemble de l'infrastructure.
