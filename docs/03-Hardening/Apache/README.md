| Nom du document | README.md |
| Technologie | Apache HTTP Server |
| Catégorie | Hardening |
| Objectif | Présenter l'organisation des documents de durcissement d'Apache |
| Auteur | Sébastien Allely |
| Version | 1.0 |
| Date de dernière modification | 22/09/2026 |

# Durcissement Apache

## 1. Objectif

Ce répertoire regroupe la documentation consacrée au durcissement d'Apache HTTP Server.

L'objectif est de réduire la surface d'attaque du serveur Web, de sécuriser les communications et les mécanismes d'accès, de limiter l'exposition des informations techniques et d'assurer un fonctionnement maîtrisé du service.

## 2. Organisation

Les documents sont structurés selon les principales étapes du durcissement d'un serveur Web.

| Document                                     | Contenu                                               |
| -------------------------------------------- | ----------------------------------------------------- |
| `01-Justification-des-decisions.md`          | Justification des décisions de sécurité               |
| `02-Identification-des-actifs.md`            | Identification des composants et ressources concernés |
| `03-Analyse-des-risques.md`                  | Analyse des risques associés au service               |
| `04-Surface-d-attaque.md`                    | Réduction de la surface d'attaque                     |
| `05-Configuration-initiale.md`               | État et principes de configuration initiale           |
| `06-Durcissement.md`                         | Mesures principales de durcissement                   |
| `07-Journalisation-et-supervision.md`        | Journalisation et supervision                         |
| `08-TLS-HTTPS.md`                            | Sécurisation des communications HTTPS                 |
| `09-Authentification-et-controle-d-acces.md` | Authentification et contrôle des accès                |
| `10-Checklist.md`                            | Contrôle final du durcissement                        |

## 3. Méthode

Les mesures sont documentées selon la démarche générale du projet :

**besoin → risque → décision de sécurité → mise en œuvre → validation → maintenance**

La checklist constitue le support de contrôle final.

## 4. Périmètre

Cette documentation concerne le durcissement d'Apache HTTP Server dans le cadre du laboratoire.

Les paramètres doivent être adaptés au contexte, aux applications hébergées et aux exigences de sécurité de l'environnement cible.
