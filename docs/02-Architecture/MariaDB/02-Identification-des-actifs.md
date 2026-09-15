# 02 - Identification des actifs


| Élément | Valeur |
| **Nom du document** | `02-Identification-des-actifs.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les actifs MariaDB concernés par les mesures de sécurité. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Objectif

Identifier les actifs que MariaDB héberge ou protège afin de déterminer les besoins de sécurité.

---

# Actifs techniques

- Service MariaDB
- Processus mysqld
- Port TCP 3306
- Socket UNIX
- Configuration (my.cnf)
- Journaux
- Binlogs
- Plugins
- Moteur InnoDB
- Fichiers de données
- Sauvegardes
- Certificats TLS (si utilisés)

---

# Actifs métier

Les actifs métier dépendent des applications utilisant MariaDB.

Dans le laboratoire, ils comprennent notamment :

- utilisateurs GLPI01 ;
- inventaire ;
- tickets ;
- historiques ;
- équipements ;
- configurations ;
- informations d'authentification.

---

# Disponibilité

La disponibilité de MariaDB conditionne directement :

- GLPI01 ;
- les sauvegardes cohérentes ;
- les applications utilisant la base.

Une indisponibilité peut entraîner une interruption de service.

---

# Confidentialité

Les données hébergées peuvent contenir :

- des comptes utilisateurs ;
- des informations techniques ;
- des données d'administration.

Leur divulgation constitue un risque majeur.

---

# Intégrité

Une altération des données peut provoquer :

- une perte d'informations ;
- des incohérences applicatives ;
- des erreurs de fonctionnement.

---

# Conclusion

Les actifs protégés ne se limitent pas au serveur MariaDB lui-même.

La véritable valeur réside dans les données hébergées et les services qui en dépendent.
