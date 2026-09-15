# 04 - Surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | GLPI |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La surface d'attaque regroupe l'ensemble des composants accessibles pouvant être utilisés pour compromettre GLPI01.

Son identification permet de justifier les mesures de durcissement qui seront appliquées.

---

# 2. Interfaces exposées

Les principales interfaces sont :

- interface Web HTTPS ;
- interface d'administration ;
- authentification LDAP ;
- API REST (si activée) ;
- accès SSH au serveur ;
- accès à la base MariaDB (localement).

Chaque interface supplémentaire augmente potentiellement la surface d'attaque.

---

# 3. Services dépendants

GLPI01 repose sur plusieurs composants :

- Apache HTTP Server ;
- PHP ;
- MariaDB ;
- Active Directory ;
- Ubuntu Server.

Une vulnérabilité sur l'un de ces composants peut affecter GLPI01.

---

# 4. Comptes exposés

Les comptes suivants présentent une importance particulière :

- administrateurs GLPI01 ;
- comptes techniques ;
- comptes LDAP ;
- comptes locaux du système.

Leur protection constitue un enjeu majeur.

---

# 5. Données exposées

GLPI01 centralise notamment :

- inventaire matériel ;
- inventaire logiciel ;
- utilisateurs ;
- tickets ;
- contrats ;
- licences ;
- documents ;
- historique des interventions.

Ces informations présentent une forte valeur métier.

---

# 6. Conclusion

La réduction de la surface d'attaque repose principalement sur la limitation des services exposés, le contrôle des comptes privilégiés et la sécurisation des composants support.
