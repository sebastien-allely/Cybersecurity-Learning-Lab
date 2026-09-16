# ROADMAP

| Élément                           | Valeur                                                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `ROADMAP.md`                                                                                                 |
| **Technologie**                   | Référentiel du laboratoire                                                                                   |
| **Catégorie**                     | Gestion de projet                                                                                            |
| **Objectif**                      | Présenter l'état d'avancement du projet et les évolutions prévues du référentiel Cybersecurity-Learning-Lab. |
| **Auteur**                        | Sébastien Allely                                                                                             |
| **Version**                       | 1.1                                                                                                          |
| **Date de dernière modification** | 15/09/2026                                                                                                   |

---

## Objectif

Cette feuille de route présente les principaux modules du projet **Cybersecurity-Learning-Lab**, leur état d'avancement et les évolutions prévues.

Elle permet de distinguer les éléments intégrés à la V1 des travaux restant à réaliser ou à approfondir.

Les priorités pourront évoluer en fonction des retours de la communauté, des évolutions technologiques et des référentiels de cybersécurité.

### Légende

* `[x]` Réalisé et intégré au référentiel.
* `[~]` Partiellement réalisé ou nécessitant encore des compléments.
* `[ ]` Prévu, non encore réalisé.
* `→` Amélioration continue.

---

# Phase 0 — Fondation du projet

## Documentation

* [x] README
* [x] PROJECT_CHARTER
* [x] Guide de rédaction
* [x] CONTRIBUTING
* [x] SECURITY
* [x] CODE_OF_CONDUCT
* [x] Licences

**État : terminé pour la V1.**

La gouvernance du projet, les règles de contribution, les principes de rédaction et les licences sont intégrés au référentiel.

---

# Phase 1 — Infrastructure

## Architecture

* [x] Architecture du laboratoire
* [x] Cluster Proxmox VE
* [x] Réseau
* [x] Sauvegardes
* [x] Bonnes pratiques

**État : réalisé pour la V1.**

L'architecture est documentée selon une approche de conception prenant en compte les actifs, les menaces, les risques, la criticité et la justification des décisions techniques.

---

# Phase 2 — Durcissement

* [x] Durcissement Proxmox
* [x] Durcissement Debian
* [x] Durcissement Apache
* [x] Durcissement MariaDB
* [x] Durcissement PHP
* [x] SSH

**État : réalisé pour la V1.**

Les principes et mesures de durcissement retenus sont documentés et intégrés au référentiel.

---

# Phase 3 — Protection

* [x] Fail2ban
* [x] CrowdSec
* [~] ClamAV
* [~] AIDE

**État : partiellement réalisé.**

Fail2ban et CrowdSec disposent d'une documentation dédiée dans le référentiel.

ClamAV et AIDE sont intégrés au périmètre de sécurité et de supervision du laboratoire, mais leur couverture documentaire n'est pas encore équivalente à celle de Fail2ban et CrowdSec.

---

# Phase 4 — Supervision

* [x] ZABBIX01
* [x] Templates
* [x] Tableaux de bord
* [x] Détection
* [~] KPI techniques
* [~] KPI fonctionnels

**État : réalisé avec compléments prévus.**

La supervision Zabbix constitue le système de monitoring du laboratoire.

Les éléments de supervision, de détection et de visualisation sont intégrés au projet. Les indicateurs techniques et fonctionnels pourront être enrichis progressivement afin de mieux mesurer la disponibilité, la sécurité et la qualité de service.

---

# Phase 5 — Gestion des services

* [x] Active Directory
* [x] GLPI01
* [x] DNS
* [x] LDAP
* [x] Sauvegardes

**État : réalisé pour la V1.**

Les principaux services du laboratoire et leurs mécanismes associés sont documentés dans les différentes parties du référentiel.

---

# Phase 6 — Réponse à incident

* [~] Journalisation
* [~] Investigation
* [~] Collecte des preuves
* [~] Analyse des journaux

**État : partiellement réalisé.**

Les principes de réponse à incident et d'analyse sont présents dans le projet.

La mise en œuvre pourra être approfondie dans une version ultérieure, notamment sur les procédures opérationnelles, la collecte structurée des éléments de preuve et les scénarios d'investigation.

---

# Phase 7 — Automatisation

* [~] Scripts PowerShell
* [~] Scripts Bash
* [~] Scripts Python
* [ ] Industrialisation

**État : en développement.**

L'automatisation constitue une évolution du projet et sera développée progressivement.

L'objectif est de privilégier des scripts reproductibles, documentés, idempotents lorsque cela est pertinent, et intégrables dans les processus d'administration et de sécurité du laboratoire.

---

# Phase 8 — Laboratoires

Chaque composant disposera de son propre laboratoire lorsque cela est pertinent.

Chaque laboratoire peut comprendre :

* [x] Installation
* [x] Configuration
* [x] Validation
* [x] Supervision
* [x] Simulation d'attaque
* [x] Dépannage
* [x] Exercices

**État : réalisé pour la V1.**

Les laboratoires prévus pour la V1 ont été développés, vérifiés et clôturés.

Les futurs laboratoires suivront la même méthodologie sans remettre en cause les travaux déjà validés.

---

# Phase 9 — Amélioration continue

* → Relecture
* → Mise à jour des référentiels
* → Mise à jour des scripts
* → Veille technologique
* → Retours de la communauté

**État : permanent.**

Cette phase ne constitue pas une étape à clôturer définitivement.

Le référentiel est destiné à évoluer avec les versions des technologies utilisées, les référentiels de cybersécurité, les retours d'expérience et les besoins pédagogiques.

---

# État de la V1

La **V1 du Cybersecurity-Learning-Lab** constitue une base fonctionnelle et documentée couvrant :

* la méthodologie de conception ;
* l'architecture du laboratoire ;
* le durcissement des composants ;
* les mécanismes de protection ;
* la supervision ;
* la gestion des principaux services ;
* les laboratoires pédagogiques ;
* la gouvernance et la maintenance du référentiel.

La V1 n'a pas pour objectif de couvrir immédiatement l'ensemble des fonctionnalités prévues à long terme.

Les principaux axes d'évolution concernent notamment :

* l'enrichissement de la réponse à incident ;
* l'automatisation ;
* l'industrialisation des procédures ;
* l'enrichissement des KPI ;
* l'approfondissement de ClamAV et AIDE ;
* l'évolution des scénarios pédagogiques ;
* la veille et l'actualisation des référentiels.

L'objectif reste de privilégier la **qualité, la reproductibilité et la traçabilité** à la quantité de contenu.

Un module est considéré comme suffisamment mature pour être intégré lorsqu'il a été documenté, testé, supervisé lorsque pertinent et relu.
