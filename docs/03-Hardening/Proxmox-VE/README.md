| Nom du document | README.md |
| Technologie | Proxmox VE |
| Catégorie | Hardening |
| Objectif | Présenter et organiser les mesures de durcissement appliquées à l'infrastructure de virtualisation Proxmox VE. |
| Auteur | Sébastien Allely |
| Version | 1.0 |
| Date de dernière modification | 22/09/2026 |

# Durcissement de Proxmox VE

## 1. Objectif

Cette documentation présente les mesures de durcissement appliquées à Proxmox VE afin de réduire la surface d'attaque, protéger les accès d'administration, sécuriser la configuration du système et de l'infrastructure de virtualisation, et maintenir un niveau de sécurité cohérent dans le temps.

Les contrôles sont organisés selon une démarche de réduction des risques, de validation technique et de maintien en condition de sécurité.

## 2. Documentation

| Document                                                                           | Description                                              |
| ---------------------------------------------------------------------------------- | -------------------------------------------------------- |
| [01-Objectif-du-durcissement.md](01-Objectif-du-durcissement.md)                   | Définition des objectifs et du périmètre du durcissement |
| [02-Reduction-de-la-surface-d-attaque.md](02-Reduction-de-la-surface-d-attaque.md) | Réduction des services et fonctionnalités exposés        |
| [03-Gestion-des-comptes.md](03-Gestion-des-comptes.md)                             | Gestion des comptes et des privilèges                    |
| [04-Durcissement-SSH.md](04-Durcissement-SSH.md)                                   | Sécurisation des accès SSH                               |
| [05-Mises-a-jour.md](05-Mises-a-jour.md)                                           | Gestion des mises à jour du système et de Proxmox VE     |
| [06-Configuration-systeme.md](06-Configuration-systeme.md)                         | Mesures de sécurisation de la configuration système      |
| [07-Stockage.md](07-Stockage.md)                                                   | Sécurisation et gestion du stockage                      |
| [08-Reseau.md](08-Reseau.md)                                                       | Sécurisation de la configuration réseau                  |
| [09-Sauvegardes.md](09-Sauvegardes.md)                                             | Protection et vérification des sauvegardes               |
| [10-Supervision.md](10-Supervision.md)                                             | Supervision et détection des événements importants       |
| [11-Maintenance.md](11-Maintenance.md)                                             | Maintien en condition de sécurité                        |
| [12-Checklist.md](12-Checklist.md)                                                 | Contrôle pédagogique du durcissement                     |

## 3. Méthode

Le durcissement repose sur une approche progressive :

1. identifier les composants et services concernés ;
2. réduire la surface d'attaque ;
3. sécuriser les comptes et les accès d'administration ;
4. renforcer la configuration système et réseau ;
5. protéger les données et les sauvegardes ;
6. superviser les composants critiques ;
7. vérifier les changements ;
8. maintenir la configuration dans le temps.

## 4. Validation

Les mesures documentées doivent être vérifiées sur l'infrastructure avant d'être considérées comme effectivement appliquées.

La checklist constitue un support de contrôle permettant de vérifier les principaux points de sécurité et de conserver une trace de la réalisation des contrôles.

## 5. Périmètre

Cette documentation concerne le durcissement de l'hôte Proxmox VE et de l'infrastructure de virtualisation.

La sécurisation des systèmes invités est traitée dans les documentations de hardening correspondant à leurs technologies respectives.
