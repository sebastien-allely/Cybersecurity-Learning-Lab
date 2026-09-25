| Nom du document | README.md |
| Technologie | Zabbix |
| Catégorie | Hardening |
| Objectif | Présenter et organiser les mesures de durcissement appliquées à la plateforme de supervision Zabbix. |
| Auteur | Sébastien Allely |
| Version | 1.0 |
| Date de dernière modification | 22/09/2026 |

# Durcissement de Zabbix

## 1. Objectif

Cette documentation présente les mesures de durcissement appliquées à la plateforme Zabbix afin de protéger le serveur de supervision, ses accès d'administration, ses composants techniques et les données de supervision.

L'objectif est de limiter les risques liés à l'administration de la plateforme et de préserver la disponibilité, l'intégrité et la confidentialité des informations collectées.

## 2. Documentation

| Document                                                                           | Description                                              |
| ---------------------------------------------------------------------------------- | -------------------------------------------------------- |
| [01-Objectif-du-durcissement.md](01-Objectif-du-durcissement.md)                   | Définition des objectifs et du périmètre du durcissement |
| [02-Reduction-de-la-surface-d-attaque.md](02-Reduction-de-la-surface-d-attaque.md) | Réduction de la surface d'exposition                     |
| [03-Gestion-des-comptes.md](03-Gestion-des-comptes.md)                             | Gestion des comptes et des privilèges                    |
| [04-Durcissement-SSH.md](04-Durcissement-SSH.md)                                   | Sécurisation des accès SSH                               |
| [05-Mises-a-jour.md](05-Mises-a-jour.md)                                           | Gestion des mises à jour                                 |
| [06-Configuration-systeme.md](06-Configuration-systeme.md)                         | Sécurisation de la configuration du serveur              |
| [07-Stockage.md](07-Stockage.md)                                                   | Protection du stockage et des données                    |
| [08-Reseau.md](08-Reseau.md)                                                       | Sécurisation de la configuration réseau                  |
| [09-Sauvegardes.md](09-Sauvegardes.md)                                             | Protection et vérification des sauvegardes               |
| [10-Supervision.md](10-Supervision.md)                                             | Supervision de la plateforme Zabbix                      |
| [11-Maintenance.md](11-Maintenance.md)                                             | Maintien en condition de sécurité                        |
| [12-Checklist.md](12-Checklist.md)                                                 | Contrôle pédagogique du durcissement                     |

## 3. Méthode

Le durcissement de la plateforme Zabbix repose sur plusieurs axes :

1. identifier les composants et flux nécessaires ;
2. réduire les services et accès inutiles ;
3. protéger les comptes d'administration ;
4. sécuriser les accès au système ;
5. maintenir les composants à jour ;
6. protéger les données de supervision ;
7. sécuriser les communications ;
8. superviser le fonctionnement de la plateforme ;
9. vérifier les changements ;
10. assurer la maintenance dans le temps.

## 4. Validation

Les mesures documentées doivent être vérifiées sur l'environnement concerné avant d'être considérées comme effectivement appliquées.

La checklist constitue un support de contrôle permettant de vérifier les principaux points de sécurité et de formaliser la réalisation des contrôles.

## 5. Périmètre

Cette documentation concerne le serveur et les composants nécessaires au fonctionnement de la plateforme Zabbix.

Le durcissement des systèmes supervisés est traité dans les documentations de hardening correspondant à chaque technologie.
