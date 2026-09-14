# Cybersecurity Learning Lab

## Métadonnées

| Élément | Valeur |
|---|---|
| Catégorie | Documentation / Laboratoire pédagogique |
| Auteur | Sébastien ALLELY |
| Objectif | Fournir un laboratoire reproductible permettant d'apprendre les principes de cybersécurité à partir d'une infrastructure concrète |
| Public | Administrateurs systèmes et réseaux, étudiants, professionnels de l'IT et personnes en reconversion vers la cybersécurité |
| Niveau | Débutant à intermédiaire |
| Langue | Français |
| Dernière modification | 08/08/2026 |
| Licence du code | Voir [`licenses/CODE.md`](licenses/CODE.md) |
| Licence de la documentation | Voir [`licenses/DOCUMENTATION.md`](licenses/DOCUMENTATION.md) |

---

## Présentation

**Cybersecurity Learning Lab** est un laboratoire pédagogique consacré à l'administration système et réseau sécurisée, à la supervision, à la détection et à la réponse aux incidents.

Le dépôt s'appuie sur un environnement de laboratoire réaliste intégrant notamment :

* Proxmox VE ;
* machines Linux et Windows ;
* Active Directory ;
* GLPI ;
* Zabbix Agent 2 et Zabbix Server ;
* CrowdSec ;
* Fail2ban ;
* mécanismes de sauvegarde et de maintenance ;
* pratiques de hardening et de supervision.

L'objectif n'est pas de fournir une simple collection de commandes, mais de présenter une **démarche cohérente de sécurisation d'une infrastructure** : comprendre l'architecture, identifier les risques, appliquer des mesures de protection, superviser leur fonctionnement, puis maintenir et améliorer l'ensemble.

---

## Public visé

Le laboratoire s'adresse principalement :

* aux administrateurs systèmes et réseaux souhaitant renforcer leurs compétences en cybersécurité ;
* aux personnes débutant dans l'administration sécurisée d'une infrastructure ;
* aux apprenants souhaitant comprendre la relation entre **architecture, hardening, protection, supervision et réponse à incident** ;
* aux professionnels souhaitant disposer d'un environnement de laboratoire reproductible pour expérimenter.

Les contenus sont volontairement progressifs. Il n'est pas nécessaire de maîtriser toutes les technologies avant de commencer.

---

## Philosophie du laboratoire

Le laboratoire suit une logique opérationnelle :

```text
Comprendre
    ↓
Concevoir
    ↓
Architecturer
    ↓
Durcir
    ↓
Protéger
    ↓
Superviser
    ↓
Détecter
    ↓
Répondre
    ↓
Maintenir
    ↓
Améliorer
```

Les technologies ne sont donc pas étudiées isolément. Chaque composant doit avoir une fonction identifiable dans l'architecture globale.

---

# Navigation

## 00 — Introduction

Point de départ du dépôt.

Cette section présente les principes généraux du laboratoire, les conventions documentaires et les règles permettant de produire une documentation cohérente.

[Accéder à l'introduction](docs/00-Introduction/README.md)

---

## 01 — Méthode de conception

Cette section présente la démarche utilisée pour concevoir et faire évoluer le laboratoire.

Elle permet notamment de comprendre comment passer d'un besoin de sécurité à une architecture et à des mesures techniques cohérentes.

[Accéder à la méthode de conception](docs/01-Methode-de-conception/README.md)

---

## 02 — Architecture

Cette section décrit l'architecture du laboratoire et les choix structurants.

Elle constitue le socle permettant de comprendre :

* les composants de l'infrastructure ;
* leurs rôles ;
* leurs interactions ;
* les flux ;
* les principes de segmentation et de sécurisation.

[Accéder à l'architecture](docs/02-Architecture/README.md)

---

## 03 — Hardening

Cette section regroupe les mesures de durcissement appliquées aux différents composants de l'infrastructure.

Elle couvre notamment les principes de :

* réduction de la surface d'attaque ;
* sécurisation des services ;
* contrôle des accès ;
* configuration système ;
* vérification des configurations.

[Accéder au hardening](docs/03-Hardening/README.md)

---

## 04 — Protection

Cette section présente les mécanismes de protection et de défense déployés dans le laboratoire.

### CrowdSec

CrowdSec est utilisé pour la détection comportementale et la remédiation automatisée.

[Documentation CrowdSec](docs/04-Protection/CrowdSec/README.md)

### Fail2ban

Fail2ban est étudié comme mécanisme complémentaire de protection contre certains comportements abusifs, notamment les tentatives répétées d'authentification.

[Documentation Fail2ban](docs/04-Protection/Fail2ban/README.md)

La documentation Fail2ban couvre notamment :

* introduction ;
* architecture ;
* installation ;
* configuration ;
* jail SSH ;
* jail Proxmox ;
* création de filtres personnalisés ;
* supervision Zabbix ;
* maintenance ;
* cycle de vie ;
* désinstallation.

---

## 05 — Monitoring

Cette section présente la stratégie de supervision du laboratoire.

Elle explique notamment :

* l'architecture du monitoring ;
* les principes de supervision ;
* les éléments supervisés ;
* la gestion des sévérités et des alertes ;
* les KPI ;
* les tableaux de bord ;
* la validation et le diagnostic.

[Accéder au monitoring](docs/05-Monitoring/README.md)

---

## 06 — Incident Response

Cette section présente la réponse à incident dans le contexte du laboratoire.

Elle permet de replacer les mécanismes de détection et de supervision dans une démarche opérationnelle de traitement d'un incident :

* identification ;
* qualification ;
* analyse ;
* containment ;
* remédiation ;
* retour à l'état nominal ;
* retour d'expérience.

[Accéder à la réponse à incident](docs/06-Incident-Response/README.md)

---

## 07 — Maintenance

La sécurité d'une infrastructure ne s'arrête pas après son déploiement.

Cette section traite notamment :

* de la maintenance générale ;
* des mises à jour et vulnérabilités ;
* des sauvegardes et restaurations ;
* de la vérification des configurations ;
* de la maintenance des mécanismes de sécurité ;
* de la maintenance de la supervision ;
* de la réévaluation et de l'amélioration continue.

[Accéder à la maintenance](docs/07-Maintenance/README.md)

---

## 08 — Exercices

Cette section est réservée aux exercices pratiques destinés à permettre à l'apprenant de mettre en application les notions étudiées dans le laboratoire.

> **État actuel :** cette section n'est pas intégrée au parcours principal du dépôt.

Les exercices pourront être ajoutés ultérieurement lorsque leur conception et leur mode d'évaluation seront suffisamment robustes pour être utilisés dans un contexte pédagogique.

---

## 09 — Learning Path

Cette section propose différents parcours permettant d'utiliser le laboratoire selon l'objectif de l'apprenant.

Les parcours s'appuient sur les connaissances et pratiques présentées dans les autres sections du dépôt.

Parcours disponibles :

* [Parcours de découverte](docs/09-Learning-Path/01-Parcours-de-decouverte.md)
* [Parcours administration sécurisée](docs/09-Learning-Path/02-Parcours-administration-securisee.md)
* [Parcours détection et supervision](docs/09-Learning-Path/03-Parcours-detection-et-supervision.md)
* [Parcours réponse à incident](docs/09-Learning-Path/04-Parcours-reponse-a-incident.md)
* [Parcours automatisation et amélioration](docs/09-Learning-Path/05-Parcours-automatisation-et-amelioration.md)

[Accéder au Learning Path](docs/09-Learning-Path/README.md)

---

## 10 — Appendices

Cette section regroupe les ressources complémentaires permettant d'utiliser et de comprendre plus facilement le laboratoire.

Elle contient notamment :

* les conventions ;
* les aide-mémoires de commandes ;
* les matrices de correspondance ;
* les modèles documentaires.

[Accéder aux appendices](docs/10-Appendices/README.md)

---

# Automatisation

Le répertoire `automation/` contient les éléments d'automatisation associés au laboratoire.

Les automatisations sont organisées par technologie ou langage :

* [Bash](automation/bash/)
* [PowerShell](automation/powershell/)
* [Python](automation/python/)
* [SQL](automation/sql/)

L'objectif est de séparer les scripts opérationnels de la documentation afin de permettre leur réutilisation sans mélanger procédure pédagogique et implémentation technique.

[Accéder aux automatisations](automation/README.md)

---

# Zabbix

Le répertoire `zabbix/` contient les éléments nécessaires à l'intégration de Zabbix dans le laboratoire.

Il regroupe notamment :

* les templates ;
* les UserParameters ;
* les dashboards ;
* les exports ;
* les médias ;
* les scripts ;
* les éléments nécessaires à la supervision.

Les fichiers sont organisés selon leur **cible technique**, afin d'éviter de mélanger les configurations applicables au serveur Zabbix, aux nœuds Proxmox ou aux autres composants supervisés.

[Accéder au dépôt Zabbix](zabbix/README.md)

---

# Labs

Le répertoire `labs/` regroupe les ressources directement liées à la construction et à l'utilisation du laboratoire.

Il permet de distinguer les éléments pratiques du laboratoire de la documentation théorique.

[Accéder aux labs](labs/README.md)

---

# Gestion du projet

Les documents relatifs à la gouvernance et à l'évolution du projet sont regroupés dans :

[docs/99-Project-Management](docs/99-Project-Management/)

On y trouve notamment :

* la roadmap ;
* l'architecture du dépôt ;
* le processus de revue des contributions ;
* la checklist de qualité documentaire.

---

# Contribuer

Les contributions sont possibles à condition de respecter les conventions du projet.

Avant toute contribution, consulter :

* [CONTRIBUTING.md](CONTRIBUTING.md)
* [Code of Conduct](CODE_OF_CONDUCT.md)
* [Security Policy](SECURITY.md)
* [Writing Guide](docs/00-Introduction/DOC-000-Writing-Guide.md)

Les Pull Requests doivent notamment respecter le modèle fourni dans :

`.github/PULL_REQUEST_TEMPLATE.md`

---

# Documentation et licences

Le projet distingue les licences applicables au **code**, à la **documentation** et aux autres contenus du dépôt.

Les informations détaillées sont disponibles dans :

* [Licence du code](licenses/CODE.md)
* [Licence de la documentation](licenses/DOCUMENTATION.md)

---

# Sources et références

Les références utilisées pour construire le laboratoire sont regroupées dans :

[docs/98-References](docs/98-References/)

Cette section permet notamment d'identifier les référentiels, documentations et ressources externes ayant contribué à la conception du laboratoire.

---

# Structure générale du dépôt

```text
Cybersecurity-Learning-Lab/
│
├── .github/
│   └── PULL_REQUEST_TEMPLATE.md
│
├── assets/
│
├── automation/
│   ├── bash/
│   ├── powershell/
│   ├── python/
│   └── sql/
│
├── docs/
│   ├── 00-Introduction/
│   ├── 01-Methode-de-conception/
│   ├── 02-Architecture/
│   ├── 03-Hardening/
│   ├── 04-Protection/
│   ├── 05-Monitoring/
│   ├── 06-Incident-Response/
│   ├── 07-Maintenance/
│   ├── 09-Learning-Path/
│   ├── 10-Appendices/
│   ├── 98-References/
│   └── 99-Project-Management/
│
├── labs/
│
├── licenses/
│
└── zabbix/
    ├── dashboards/
    ├── export/
    ├── media/
    ├── scripts/
    ├── templates/
    └── userparameters/
```

---

# État du projet

Le dépôt est un **laboratoire en évolution**.

Les contenus sont construits progressivement afin de conserver une cohérence entre :

**architecture → hardening → protection → monitoring → incident response → maintenance → parcours d'apprentissage.**

Les éléments techniques présents dans le dépôt doivent rester cohérents avec cette architecture et avec les procédures documentées.

---

## Point de départ recommandé

Pour découvrir le projet dans l'ordre :

1. [Introduction](docs/00-Introduction/README.md)
2. [Méthode de conception](docs/01-Methode-de-conception/README.md)
3. [Architecture](docs/02-Architecture/README.md)
4. [Hardening](docs/03-Hardening/README.md)
5. [Protection](docs/04-Protection/README.md)
6. [Monitoring](docs/05-Monitoring/README.md)
7. [Incident Response](docs/06-Incident-Response/README.md)
8. [Maintenance](docs/07-Maintenance/README.md)
9. [Learning Path](docs/09-Learning-Path/README.md)
10. [Appendices](docs/10-Appendices/README.md)
