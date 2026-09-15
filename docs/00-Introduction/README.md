Nom du document : README — Introduction du projet
Technologie : Multitechnologies
Catégorie : Introduction
Objectif : Présenter le projet, son périmètre, son approche pédagogique et l’organisation de sa documentation
Auteur : Sébastien ALLELY
Version : 1.0
Date de dernière modification : 12/09/2026

# Cybersecurity-Learning-Lab

## 1. Présentation

**Cybersecurity-Learning-Lab** est un laboratoire informatique personnel dédié à l’apprentissage de l’administration système, de l’administration réseau et de la cybersécurité.

Le projet s’appuie sur une infrastructure virtualisée permettant de mettre en œuvre, d’observer et de tester différents mécanismes de sécurité dans un environnement contrôlé.

L’objectif n’est pas uniquement de déployer des outils, mais de documenter les **choix techniques**, leur justification, les risques associés, les mesures de protection et les méthodes de validation.

Le laboratoire est ainsi conçu comme un support d’apprentissage reproductible et évolutif.

## 2. Objectifs

Le projet poursuit plusieurs objectifs :

* développer les compétences en administration système et réseau ;
* comprendre les mécanismes de sécurité des infrastructures informatiques ;
* mettre en œuvre des mesures de durcissement (*hardening*) ;
* déployer des mécanismes de protection et de détection ;
* superviser l'état technique et sécuritaire de l'infrastructure ;
* pratiquer la réponse à incident ;
* automatiser certaines tâches d'administration et de sécurité ;
* documenter les décisions techniques et leur justification ;
* identifier les limites et la dette technique du laboratoire ;
* appliquer une démarche structurée de conception et d'amélioration continue.

## 3. Public visé

Le projet s'adresse principalement aux personnes souhaitant développer ou consolider leurs compétences dans les domaines suivants :

* administration système ;
* administration réseau ;
* cybersécurité défensive (*Blue Team*) ;
* détection et supervision ;
* réponse à incident ;
* automatisation ;
* approche DevSecOps ;
* gestion des risques techniques.

Les notions techniques utilisées dans la documentation sont expliquées lorsqu'elles sont introduites afin de conserver une approche pédagogique.

## 4. Périmètre

Le laboratoire couvre notamment :

* la virtualisation avec Proxmox VE ;
* les systèmes Linux Debian et Ubuntu ;
* Active Directory sous Windows Server ;
* les services web avec Apache ;
* la gestion d'inventaire et de parc avec GLPI ;
* les bases de données MariaDB ;
* la supervision avec Zabbix ;
* la détection et la protection avec CrowdSec et Fail2ban ;
* l'analyse des journaux ;
* la gestion des sauvegardes ;
* les opérations de maintenance ;
* les procédures de diagnostic et d'exploitation.

Le périmètre peut évoluer en fonction des besoins pédagogiques et techniques du laboratoire.

## 5. Approche pédagogique

Le projet suit une approche orientée **mise en pratique**.

Chaque technologie est étudiée selon son rôle dans l'infrastructure et selon les risques qu'elle introduit ou permet de réduire.

La documentation cherche à répondre à plusieurs questions :

1. Pourquoi cette technologie est-elle utilisée ?
2. Quel actif protège-t-elle ou supporte-t-elle ?
3. Quels sont les risques associés ?
4. Quelle surface d'attaque doit être maîtrisée ?
5. Quelles mesures de sécurité sont mises en œuvre ?
6. Quels événements peuvent être observés ?
7. Comment vérifier que la configuration fonctionne ?
8. Comment maintenir et faire évoluer la solution ?

Cette démarche permet de ne pas limiter l'apprentissage à l'exécution de commandes ou à l'installation d'outils.

## 6. Méthodologie de conception

La conception du laboratoire repose sur une démarche structurée.

Elle commence par l'identification des **actifs**, c'est-à-dire les ressources importantes pour le fonctionnement du système.

Les **menaces** susceptibles d'affecter ces actifs sont ensuite identifiées et les **risques** sont analysés.

La criticité permet ensuite de déterminer les éléments nécessitant le plus d'attention.

Les décisions de sécurité sont alors justifiées en fonction :

* du risque ;
* du besoin fonctionnel ;
* des contraintes techniques ;
* des contraintes budgétaires ;
* des compétences disponibles ;
* de la maintenabilité ;
* de l'impact sur l'exploitation.

Les mesures retenues sont finalement validées techniquement puis intégrées dans une démarche d'amélioration continue.

Cette méthodologie constitue un élément central du projet : **la sécurité est considérée comme une démarche de conception et non comme une simple succession d'outils de protection.**

## 7. Organisation de la documentation

La documentation est organisée par domaine :

| Répertoire                 | Contenu                                        |
| -------------------------- | ---------------------------------------------- |
| `01-Methode-de-conception` | Méthodologie de conception et d'analyse        |
| `02-Architecture`          | Architecture et justification des technologies |
| `03-Hardening`             | Durcissement des systèmes et applications      |
| `04-Protection`            | Mécanismes de protection et de prévention      |
| `05-Monitoring`            | Supervision, détection et indicateurs          |
| `06-Incident-Response`     | Réponse et traitement des incidents            |
| `07-Maintenance`           | Maintenance et amélioration continue           |
| `09-Learning-Path`         | Parcours pédagogiques                          |
| `10-Appendices`            | Conventions, aide-mémoire et modèles           |
| `98-References`            | Référentiels et sources documentaires          |
| `99-Project-Management`    | Organisation et gestion du projet              |

Les technologies disposent également de leur propre documentation lorsqu'un traitement spécifique est nécessaire.

## 8. Principes de sécurité

Le laboratoire applique notamment les principes suivants :

* réduction de la surface d'attaque ;
* moindre privilège ;
* séparation des responsabilités ;
* authentification et contrôle d'accès ;
* journalisation ;
* supervision ;
* sauvegarde et restauration ;
* validation des configurations ;
* maintenance régulière ;
* analyse des risques ;
* traçabilité des décisions techniques.

Les mesures de sécurité sont évaluées en tenant compte de leur efficacité, de leur complexité et de leur impact opérationnel.

## 9. Environnement de démonstration

Les exemples et configurations destinés à la publication utilisent des valeurs **génériques et anonymisées**.

Les informations propres à l'infrastructure personnelle ne doivent pas être publiées, notamment :

* adresses IP réelles ;
* noms d'hôtes réels ;
* noms de domaine internes ;
* comptes et identifiants ;
* chemins ou partages contenant des informations sensibles ;
* informations permettant d'identifier l'infrastructure.

Les exemples utilisent donc des valeurs représentatives telles que `PVE1`, `PVE2`, `AD`, `GLPI01` ou `ZABBIX01`.

## 10. Limites du laboratoire

Ce laboratoire constitue un environnement d'apprentissage et ne doit pas être considéré comme une architecture de production universelle.

Les choix techniques sont influencés par :

* les ressources matérielles disponibles ;
* les contraintes budgétaires ;
* les objectifs pédagogiques ;
* la taille de l'environnement ;
* les besoins fonctionnels ;
* le temps disponible pour l'administration.

Certaines mesures peuvent donc être volontairement simplifiées ou différer des pratiques adaptées à une infrastructure professionnelle de grande taille.

Les limites identifiées sont documentées afin de distinguer une **contrainte connue** d'une vulnérabilité ignorée.

## 11. Amélioration continue

Le laboratoire évolue progressivement.

Les modifications importantes sont documentées afin de conserver la trace :

* des changements d'architecture ;
* des décisions de sécurité ;
* des corrections ;
* des améliorations ;
* des limites identifiées ;
* des évolutions envisagées.

Cette démarche permet de rapprocher progressivement le laboratoire d'une logique d'exploitation professionnelle tout en conservant son objectif pédagogique.

## 12. Avertissement

Les configurations, commandes et procédures présentées dans ce projet sont destinées à un environnement de laboratoire contrôlé.

Elles doivent être adaptées et validées avant toute utilisation dans un environnement de production.

L'auteur ne garantit pas qu'une configuration présentée soit adaptée à tous les contextes techniques, organisationnels ou réglementaires.

L'utilisation des techniques de sécurité, de diagnostic ou de test doit rester conforme au cadre légal et aux autorisations applicables.
