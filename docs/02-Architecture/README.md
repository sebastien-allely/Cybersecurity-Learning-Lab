| **Nom du document**               | `README.md`                                                                                                                    |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Technologie**                   | Architecture système et sécurité                                                                                               |
| **Catégorie**                     | Architecture                                                                                                                   |
| **Objectif**                      | Présenter l'organisation des documents d'architecture du laboratoire et fournir un point d'entrée vers les composants étudiés. |
| **Auteur**                        | Sebastien Allely                                                                                                               |
| **Version**                       | 1.0                                                                                                                            |
| **Date de dernière modification** | 27/09/2026                                                                                                                     |

# Architecture

Cette section décrit les composants techniques du laboratoire, leur rôle, leur organisation, leurs dépendances et les principales décisions d'architecture retenues.

L'objectif est de disposer d'une représentation suffisamment structurée de l'environnement pour comprendre les choix techniques avant d'aborder leur durcissement, leur protection et leur supervision.

## Organisation

Chaque composant dispose, lorsque cela est applicable, d'une documentation structurée autour des éléments suivants :

* justification de l'outil ;
* identification des actifs ;
* analyse des risques ;
* surface d'attaque ;
* événements observables ;
* justification des décisions ;
* références.

## Composants documentés

| Composant                               | Description                                                        |
| --------------------------------------- | ------------------------------------------------------------------ |
| [Active Directory](./Active-Directory/) | Service d'annuaire et d'authentification du laboratoire            |
| [Apache](./Apache/)                     | Serveur web utilisé dans le laboratoire                            |
| [ClamAV](./ClamAV/)                     | Antivirus et analyse des fichiers                                  |
| [CrowdSec](./CrowdSec/)                 | Détection et réponse collaborative aux comportements malveillants  |
| [Debian](./Debian/)                     | Système d'exploitation Linux utilisé pour certains services        |
| [Fail2ban](./Fail2ban/)                 | Protection contre certaines tentatives d'authentification abusives |
| [GLPI](./GLPI/)                         | Gestion de parc et d'inventaire                                    |
| [MariaDB](./MariaDB/)                   | Système de gestion de base de données                              |
| [Proxmox VE](./Proxmox-VE/)             | Plateforme de virtualisation                                       |
| [Zabbix](./Zabbix/)                     | Supervision et collecte des événements techniques                  |

## Relation avec les autres sections

L'architecture constitue une base de référence pour les autres parties du laboratoire :

```text
Architecture
    ↓
Hardening
    ↓
Protection
    ↓
Monitoring
    ↓
Incident Response
    ↓
Maintenance
```

Les décisions documentées dans cette section doivent permettre de comprendre le rôle et les dépendances des composants avant leur mise en œuvre ou leur durcissement.

## Principe de documentation

La documentation d'architecture décrit les choix retenus et leurs justifications. Elle ne constitue pas une copie exhaustive de la documentation officielle des logiciels concernés.

Lorsque des informations techniques doivent être vérifiées, les sources officielles et les références sélectionnées dans [`docs/98-References/`](../98-References/) constituent les points de référence appropriés.
