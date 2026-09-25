| Nom du document | README.md |
| Technologie | Active Directory Domain Services |
| Catégorie | Hardening |
| Objectif | Présenter l'organisation des documents de durcissement d'Active Directory |
| Auteur | Sébastien Allely |
| Version | 1.0 |
| Date de dernière modification | 22/09/2026 |

# Durcissement Active Directory

## 1. Objectif

Ce répertoire regroupe la documentation consacrée au durcissement d'Active Directory Domain Services.

L'objectif est de réduire la surface d'attaque du service d'annuaire, de renforcer la gestion des comptes et de l'authentification, d'améliorer la journalisation et de maintenir le service dans un état sécurisé.

## 2. Organisation

Les documents suivent une progression allant de la justification des décisions de sécurité jusqu'à la vérification finale.

| Document                                           | Contenu                                                 |
| -------------------------------------------------- | ------------------------------------------------------- |
| `01-Justification-des-decisions.md`                | Justification des principales décisions de durcissement |
| `02-Gestion-des-comptes.md`                        | Gestion des comptes et des privilèges                   |
| `03-Authentification.md`                           | Mesures relatives à l'authentification                  |
| `04-Reduction-de-la-surface-d-attaque.md`          | Réduction de la surface d'attaque                       |
| `05-Protection-des-donnees.md`                     | Protection des données liées au service                 |
| `06-Journalisation.md`                             | Journalisation et traçabilité                           |
| `07-Mises-a-jour-et-gestion-des-vulnerabilites.md` | Mises à jour et gestion des vulnérabilités              |
| `08-Supervision.md`                                | Supervision de l'environnement Active Directory         |
| `09-Maintenance.md`                                | Maintien en condition opérationnelle et de sécurité     |
| `10-Checklist.md`                                  | Contrôle final du durcissement                          |

## 3. Méthode

Les mesures sont documentées selon la démarche générale du projet :

**besoin → risque → décision de sécurité → mise en œuvre → validation → maintenance**

La checklist constitue le support de contrôle final et ne remplace pas les procédures de validation détaillées.

## 4. Périmètre

Cette documentation concerne le durcissement d'Active Directory dans le cadre du laboratoire.

Elle ne constitue pas une procédure universelle applicable sans adaptation à tout environnement de production.
