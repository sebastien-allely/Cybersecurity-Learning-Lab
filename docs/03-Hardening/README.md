| **Nom du document**               | `README.md`                                                                                                     |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Technologie**                   | Systèmes et services                                                                                            |
| **Catégorie**                     | Hardening                                                                                                       |
| **Objectif**                      | Présenter l'organisation de la documentation consacrée au durcissement des systèmes et services du laboratoire. |
| **Auteur**                        | Sebastien Allely                                                                                                |
| **Version**                       | 1.0                                                                                                             |
| **Date de dernière modification** | 27/09/2026                                                                                                      |

# Hardening

Cette section documente les mesures de durcissement appliquées aux systèmes et services du laboratoire.

Le durcissement consiste à réduire l'exposition et les possibilités d'exploitation d'un système tout en conservant les fonctionnalités nécessaires à son fonctionnement.

## Composants documentés

| Composant        | Documentation                                        |
| ---------------- | ---------------------------------------------------- |
| Active Directory | [Durcissement Active Directory](./Active-Directory/) |
| Apache           | [Durcissement Apache](./Apache/)                     |
| Debian           | [Durcissement Debian](./Debian/)                     |
| GLPI             | [Durcissement GLPI](./GLPI/)                         |
| MariaDB          | [Durcissement MariaDB](./MariaDB/)                   |
| Proxmox VE       | [Durcissement Proxmox VE](./Proxmox-VE/)             |
| Ubuntu           | [Durcissement Ubuntu](./Ubuntu/)                     |
| Zabbix           | [Durcissement Zabbix](./Zabbix/)                     |

## Approche

Les mesures sont documentées en reliant :

1. le besoin de sécurité ;
2. le risque considéré ;
3. la décision retenue ;
4. sa mise en œuvre ;
5. sa validation ;
6. sa maintenance.

Les mesures de protection complémentaires sont documentées dans [`docs/04-Protection/`](../04-Protection/), tandis que la supervision est traitée dans [`docs/05-Monitoring/`](../05-Monitoring/).
