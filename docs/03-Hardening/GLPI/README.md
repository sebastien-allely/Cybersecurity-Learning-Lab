| Nom du document | README.md |
| Technologie | GLPI |
| Catégorie | Hardening |
| Objectif | Présenter l'organisation des documents de durcissement de GLPI |
| Auteur | Sébastien Allely |
| Version | 1.0 |
| Date de dernière modification | 22/09/2026 |

# Durcissement GLPI

## 1. Objectif

Ce répertoire regroupe la documentation consacrée au durcissement de GLPI.

L'objectif est de réduire la surface d'attaque de l'application, de sécuriser ses accès, de protéger les données et de maintenir les composants nécessaires à son fonctionnement dans un état maîtrisé.

## 2. Organisation

Les documents sont organisés autour des principales dimensions du durcissement de l'application.

| Document                                           | Contenu                                          |
| -------------------------------------------------- | ------------------------------------------------ |
| `01-Justification-des-decisions.md`                | Justification des décisions de sécurité          |
| `02-Gestion-des-comptes.md`                        | Gestion des comptes et des privilèges            |
| `03-Authentification.md`                           | Sécurisation de l'authentification               |
| `04-Reduction-de-la-surface-d-attaque.md`          | Réduction de la surface d'attaque                |
| `05-Protection-des-donnees.md`                     | Protection des données                           |
| `06-Journalisation.md`                             | Journalisation et traçabilité                    |
| `07-Mises-a-jour-et-gestion-des-vulnerabilites.md` | Mises à jour et vulnérabilités                   |
| `08-Supervision.md`                                | Supervision du service                           |
| `09-Maintenance.md`                                | Maintenance et maintien en condition de sécurité |
| `10-Checklist.md`                                  | Contrôle final du durcissement                   |

## 3. Méthode

Les mesures sont documentées selon la démarche générale du projet :

**besoin → risque → décision de sécurité → mise en œuvre → validation → maintenance**

La checklist permet de réaliser le contrôle final des mesures documentées.

## 4. Périmètre

Cette documentation concerne le durcissement de GLPI dans le cadre du laboratoire.

Les mesures doivent être adaptées à la version de GLPI, à son architecture et aux composants qui lui sont associés.
