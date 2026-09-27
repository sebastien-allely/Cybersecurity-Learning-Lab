| **Nom du document**               | `README.md`                                                                                  |
| --------------------------------- | -------------------------------------------------------------------------------------------- |
| **Technologie**                   | Fail2ban                                                                                     |
| **Catégorie**                     | Architecture                                                                                 |
| **Objectif**                      | Présenter l'organisation de la documentation d'architecture de Fail2ban dans le laboratoire. |
| **Auteur**                        | Sebastien Allely                                                                             |
| **Version**                       | 1.0                                                                                          |
| **Date de dernière modification** | 27/09/2026                                                                                   |

# Fail2ban

Cette section présente l'intégration de Fail2ban dans le laboratoire et les éléments nécessaires à la compréhension de son rôle dans l'architecture de sécurité.

## Documents

| Document                                                                | Contenu                                    |
| ----------------------------------------------------------------------- | ------------------------------------------ |
| [01 - Justification de l'outil](./01-Justification-de-l-outil.md)       | Justification de l'utilisation de Fail2ban |
| [02 - Identification des actifs](./02-Identification-des-actifs.md)     | Identification des composants concernés    |
| [03 - Analyse des risques](./03-Analyse-des-risques.md)                 | Risques pris en compte                     |
| [04 - Surface d'attaque](./04-Surface-d-attaque.md)                     | Surface d'attaque associée                 |
| [05 - Événements observables](./05-Evenements-observables.md)           | Événements pouvant être observés           |
| [06 - Justification des décisions](./06-Justification-des-decisions.md) | Décisions d'architecture retenues          |
| [07 - Références](./07-References.md)                                   | Sources utilisées                          |

## Positionnement

Fail2ban constitue un mécanisme de protection complémentaire fondé sur l'observation des événements générés par les services protégés.

La configuration et l'exploitation de Fail2ban sont documentées séparément dans [`docs/04-Protection/Fail2ban/`](../../04-Protection/Fail2ban/).
