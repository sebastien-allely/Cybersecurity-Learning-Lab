# 05 - Machines virtuelles


| Élément | Valeur |
| **Nom du document** | `05-Machines-virtuelles.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les machines virtuelles hébergées par Proxmox VE et leur rôle dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## AD01

La VM `AD01` fournit les services Active Directory du laboratoire.

Elle constitue notamment une dépendance pour les systèmes Windows et certains mécanismes d'authentification et d'annuaire.

Elle doit donc être considérée comme une VM à criticité élevée.

---

## ZABBIX01

La VM `ZABBIX01` héberge le serveur de supervision.

Elle permet notamment de surveiller :

* les nœuds Proxmox ;
* les machines virtuelles ;
* les systèmes Linux ;
* les systèmes Windows ;
* certaines applications ;
* certains composants de sécurité.

ZABBIX01 constitue donc une composante transverse du laboratoire.

---

## GLPI01

La VM `GLPI01` fournit le service de gestion de parc et d'inventaire.

Elle est hébergée sur Ubuntu Server.

Son architecture applicative comprend notamment :

* Apache ;
* PHP ;
* MariaDB ;
* LDAP / Active Directory ;
* ZABBIX01 Agent 2.

Les détails de ces composants sont documentés dans leurs référentiels respectifs.

---

## DOCKER01

`DOCKER01` est destiné aux services et expérimentations nécessitant cet environnement.

Les détails de Docker ne sont pas traités dans le présent document.

---

## Répartition

```text
PVE1
 ├── ZABBIX01
 └── DOCKER01

PVE2
 ├── AD01

 └── GLPI01
```

---

## Dépendances

Chaque VM dépend notamment :

* du nœud Proxmox qui l'héberge ;
* du stockage ;
* du réseau ;
* de l'hyperviseur ;
* des sauvegardes ;
* de la supervision selon son rôle.

Certaines VM possèdent également des dépendances applicatives ou d'annuaire.

---

## Criticité

La criticité d'une VM dépend de son rôle dans l'infrastructure.

Une VM fournissant un service transverse ou une fonction d'infrastructure possède une criticité supérieure à une VM utilisée uniquement pour des expérimentations.

---

## Références

* Documentation officielle Proxmox VE
* Référentiels des technologies hébergées
* Référentiel Architecture du laboratoire
