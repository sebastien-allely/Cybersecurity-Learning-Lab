# ROADMAP

| Élément                           | Valeur                                                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `ROADMAP.md`                                                                                                 |
| **Technologie**                   | Référentiel du laboratoire                                                                                   |
| **Catégorie**                     | Gestion de projet                                                                                            |
| **Objectif**                      | Présenter l'état d'avancement du projet et les évolutions prévues du référentiel Cybersecurity-Learning-Lab. |
| **Auteur**                        | Sébastien Allely                                                                                             |
| **Version**                       | 1.2                                                                                                          |
| **Date de dernière modification** | 11/10/2026                                                                                                   |

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


---

# V2 — Sécurisation approfondie et validation opérationnelle

## Objectif de la V2

La V2 fait évoluer le laboratoire d'une base principalement documentée vers une infrastructure dont les contrôles de sécurité sont davantage intégrés, testés et démontrés. Elle conserve l'historique de la V1 : les évolutions sont ajoutées sans présenter rétroactivement les nouveaux travaux comme réalisés dans la V1.

Les statuts de cette section décrivent le cadrage au moment de la rédaction. Un élément ne passe à « réalisé » ou « validé » qu'après vérification technique et documentation des preuves. La préparation d'une procédure ne signifie pas que la modification a été déployée.

### Légende V2

- `[ ]` Prévu ou à évaluer.
- `[~]` En cours, partiellement réalisé ou nécessitant une vérification.
- `[x]` Réalisé et validé selon des critères documentés.
- `→` Amélioration continue.

## V2.0 — État des lieux et critères d'acceptation

- [~] Consolider l'inventaire des actifs, services, versions, flux et dépendances.
- [ ] Mettre à jour l'analyse des risques et la criticité des composants.
- [ ] Définir pour chaque chantier le périmètre, les prérequis, les tests, les risques, le retour arrière et les critères d'acceptation.
- [ ] Distinguer les mesures prévues, déployées, testées et validées.
- [ ] Vérifier l'anonymisation de la documentation publique et l'absence de secrets.

**Condition de sortie :** l'état initial est suffisamment vérifié pour planifier les changements sans supposer que les versions ou configurations historiques sont encore exactes.

## V2.1 — Résilience, virtualisation et sauvegardes

- [ ] Réévaluer les risques de disponibilité liés à l'hyperviseur et à ses dépendances.
- [ ] Revoir le durcissement de l'administration de la virtualisation et les règles de pare-feu associées.
- [ ] Vérifier les politiques de sauvegarde, la protection des accès et la séparation des responsabilités.
- [ ] Définir et exécuter des tests de restauration représentatifs.
- [ ] Documenter les objectifs RPO/RTO, les résultats des exercices et les écarts constatés.
- [ ] Évaluer la cible de stockage de sauvegarde et sa maintenance.

**Condition de sortie :** les sauvegardes sont vérifiables et au moins un scénario de restauration prioritaire est exécuté et documenté.

## V2.2 — Réseau, filtrage et politique IPv6

- [ ] Définir les zones de sécurité, les actifs, les flux autorisés et les flux interdits.
- [ ] Étudier et planifier le déploiement d'OPNsense et la segmentation réseau.
- [ ] Construire des règles inter-zones explicites selon le moindre privilège.
- [ ] Documenter les accès d'administration et le chemin de secours avant toute restriction.
- [ ] Planifier et vérifier la désactivation d'IPv6 sur les systèmes et équipements concernés, y compris interfaces, services et filtrage ; identifier et traiter les dépendances avant de retirer le protocole.
- [ ] Évaluer l'intérêt et le périmètre d'une détection réseau IDS/IPS sans l'activer sans tests préalables.

**Dépendances :** inventaire des flux, accès de secours et plan de retour arrière avant toute modification de filtrage susceptible de couper l'administration.

**Condition de sortie :** les flux nécessaires sont testés, les flux non autorisés sont bloqués conformément à la politique, et les accès d'administration restent maîtrisés.

## V2.3 — PKI, certificats et communications TLS

- [ ] Définir l'architecture d'autorité racine et d'autorité intermédiaire, les responsabilités et le cycle de vie des certificats.
- [ ] Documenter la protection, la sauvegarde et les conditions d'activation des clés d'autorité.
- [ ] Tenir un inventaire des certificats, identités, usages, échéances et procédures de révocation.
- [ ] Définir les profils de certificats en fonction des besoins réels de chaque service.
- [ ] Préparer la validation de la chaîne de confiance et le renouvellement avant expiration.
- [ ] Déployer progressivement TLS sur les interfaces et communications qui le nécessitent.

**Dépendances :** identité des services, résolution de noms, synchronisation horaire et validation des clients. Ne pas imposer un mode TLS obligatoire avant d'avoir vérifié tous les consommateurs concernés.

**Condition de sortie :** les certificats sont vérifiables, leur cycle de vie est documenté et les services prioritaires fonctionnent avec une chaîne de confiance valide.

## V2.4 — Active Directory et identité

- [ ] Préparer puis valider LDAPS avec les certificats de la PKI.
- [ ] Identifier et tester les clients LDAP avant toute restriction ou désactivation du LDAP non chiffré.
- [ ] Évaluer DNSSEC et les autres contrôles DNS selon les capacités et dépendances de l'architecture.
- [ ] Définir une stratégie de tiering d'administration et limiter les comptes privilégiés.
- [ ] Renforcer l'audit, les stratégies de sécurité et la surveillance des services AD.
- [ ] Documenter les procédures de récupération et les scénarios de panne du service d'annuaire.

**Dépendances :** V2.3 pour les certificats ; inventaire et tests des clients avant de rendre LDAPS obligatoire.

**Condition de sortie :** les clients attendus fonctionnent selon la politique d'authentification retenue, les contrôles d'identité sont vérifiés et le retour arrière est documenté.

## V2.5 — Durcissement Linux et services d'infrastructure

- [ ] Revoir les baselines Debian et Ubuntu et les écarts par rapport aux recommandations retenues.
- [ ] Revalider les règles de pare-feu local et leur cohérence avec la politique réseau.
- [ ] Approfondir le durcissement SSH et les accès d'administration.
- [ ] Revoir la configuration Apache, PHP et MariaDB : exposition, privilèges, journaux, mises à jour et communications.
- [ ] Mettre en place une stratégie maîtrisée de mises à jour de sécurité Linux.
- [ ] Documenter les vérifications après changement, les impacts et les procédures de retour arrière.

**Condition de sortie :** chaque mesure est justifiée par un risque, testée sur le périmètre concerné et associée à des preuves de validation.

## V2.6 — GLPI, Zabbix et communications des agents

- [~] Vérifier l'état réel de la montée de version GLPI, les prérequis, la migration de base de données et les fonctions critiques avant de clôturer le chantier.
- [ ] Vérifier la version et le cycle de support de Zabbix avant de définir la cible de mise à niveau.
- [ ] Définir une stratégie de chiffrement et d'authentification des communications entre serveur et agents.
- [ ] Intégrer les certificats nécessaires aux interfaces HTTPS et aux communications compatibles avec la PKI.
- [ ] Revoir les droits des comptes techniques, les ports exposés et les règles de filtrage.
- [ ] Vérifier les modèles, éléments, déclencheurs, dépendances, tableaux de bord et alertes existants avant tout ajout.
- [ ] Documenter les tests fonctionnels, les sauvegardes préalables et le retour arrière.

**Condition de sortie :** les versions et migrations sont confirmées, les fonctions prioritaires sont testées et les communications sont configurées selon une politique documentée.

## V2.7 — Conteneurs et automatisation

- [ ] Définir une politique de mises à jour des images et conteneurs Docker.
- [ ] Évaluer la provenance des images, leur maintenance, les vulnérabilités et la gestion des secrets.
- [ ] Réduire les privilèges, les capacités et les ports exposés des conteneurs.
- [ ] Définir des procédures de mise à jour, de validation et de retour arrière.
- [ ] Industrialiser progressivement les scripts Bash, PowerShell et Python avec contrôles, journalisation et gestion des erreurs.
- [ ] Tester les scripts avant de les intégrer aux procédures opérationnelles.

**Condition de sortie :** les mises à jour et scripts sont reproductibles, contrôlés et documentés ; les échecs ne laissent pas un état inconnu.

## V2.8 — Détection, journalisation et réponse à incident

- [ ] Revoir la couverture de supervision de la disponibilité et de la sécurité des actifs critiques.
- [ ] Améliorer la qualité des alertes, leur priorité, leurs dépendances et leurs procédures de traitement.
- [ ] Consolider les procédures de collecte et de conservation des journaux utiles à l'investigation.
- [ ] Compléter les procédures de réponse à incident, d'analyse et de retour d'expérience.
- [ ] Revoir la couverture et la maintenance des contrôles AIDE et ClamAV.
- [ ] Définir des scénarios de test de détection, sans confondre simulation pédagogique et preuve d'absence de vulnérabilité.

**Condition de sortie :** les scénarios retenus produisent des événements attendus, les alertes sont interprétables et les procédures d'investigation sont testées.

## V2.9 — Validation finale et publication

- [ ] Vérifier les critères d'acceptation de chaque chantier et les preuves associées.
- [ ] Vérifier les liens, métadonnées, noms de fichiers, références croisées et cohérence du référentiel.
- [ ] Exécuter les tests de sécurité et de fonctionnement prévus pour chaque changement.
- [ ] Mettre à jour les inventaires, les dépendances, les risques résiduels et les procédures de maintenance.
- [ ] Vérifier l'anonymisation complète avant publication.
- [ ] Faire relire les changements par Pull Request avant fusion dans `main`.

**Condition de sortie :** aucun chantier n'est marqué validé sans preuve ; les écarts connus sont documentés avec une décision, un responsable et une échéance.

## Règles de pilotage de la V2

1. Ne pas appliquer de durcissement réseau restrictif avant d'avoir recensé et testé les flux nécessaires.
2. Ne pas imposer LDAPS ou un nouveau mécanisme TLS avant validation des certificats et de tous les clients concernés.
3. Ne pas considérer une sauvegarde comme fiable sans test de restauration.
4. Ne pas lancer une montée de version sans sauvegarde vérifiée, critères fonctionnels et stratégie de retour arrière.
5. Ne pas ajouter d'éléments Zabbix sans vérifier les éléments, déclencheurs, tags et dépendances déjà en place.
6. Ne pas présenter une commande, une règle ou un script comme validé sans test documenté.
7. Conserver une trace des choix, des exceptions et des risques résiduels.

La priorisation fine et les statuts de chaque tâche seront révisés après l'inventaire technique. Cette roadmap constitue un cadre de travail, et non une affirmation que les chantiers V2 sont déjà déployés.
