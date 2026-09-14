# DOC-000 — Charte de rédaction

| Élément | Valeur |
| **Nom du document** | `01-Manifeste.md` |
| **Technologie** | Référentiel du laboratoire |
| **Catégorie** | Méthode de conception |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |

---
## 1. Objectif

Cette charte définit les règles de rédaction applicables à l'ensemble du projet **Cybersecurity Learning Lab**.

Son objectif est de garantir une documentation :

* homogène ;
* lisible ;
* pédagogique ;
* techniquement exacte ;
* facilement maintenable.

Tous les nouveaux documents devront respecter cette charte.

---

# 2. Langue

La langue officielle du projet est le **français**.

Les termes techniques sont conservés en anglais lorsqu'ils constituent la terminologie officielle (Fail2ban, CrowdSec, ZABBIX01, Trigger, Dashboard, Template, UserParameter, etc.).

---

# 3. Public visé

La documentation s'adresse principalement :

* aux étudiants ;
* aux administrateurs systèmes ;
* aux administrateurs systèmes et réseaux ;
* aux DevSecOps ;
* aux analystes SOC ;
* aux personnes souhaitant développer leurs compétences en cybersécurité.

Les explications doivent permettre une progression sans supposer une expertise préalable sur le composant étudié.

---

# 4. Style rédactionnel

Le style doit être :

* clair ;
* direct ;
* synthétique ;
* neutre ;
* factuel.

Éviter :

* les formulations marketing ;
* les superlatifs ;
* les jugements de valeur sur les outils ;
* les opinions non argumentées.

Privilégier les explications basées sur des faits, des référentiels ou des choix d'architecture explicitement justifiés.

---

# 5. Référentiels

Chaque affirmation doit appartenir à l'une des catégories suivantes :

## Recommandation officielle

Exemple :

> L'ANSSI recommande...

## Documentation officielle

Exemple :

> La documentation officielle de ZABBIX01 indique...

## Choix du projet

Exemple :

> Dans cette architecture, le choix retenu est...

Le lecteur doit toujours pouvoir distinguer une recommandation officielle d'un choix spécifique au laboratoire.

---

# 6. Structure des documents

Tous les projets techniques respecteront la structure suivante :

1. Présentation
2. Public visé
3. Prérequis
4. Compétences acquises
5. Pourquoi ce composant ?
6. Architecture
7. Installation
8. Configuration
9. Validation
10. Supervision
11. Tests
12. Dépannage
13. Limites
14. Aller plus loin
15. Résumé
16. Exercices
17. Références

---

# 7. Présentation des commandes

Toutes les commandes doivent :

* être complètes ;
* être testées sur le laboratoire ;
* pouvoir être copiées directement ;
* préciser si elles doivent être exécutées en tant que root ou avec sudo.

Les commandes incomplètes ou non testées ne doivent pas être publiées.

---

# 8. Captures d'écran

Les captures d'écran ne sont utilisées que lorsqu'elles apportent une réelle valeur pédagogique.

Les schémas sont privilégiés dès qu'ils permettent d'expliquer un concept plus clairement.

---

# 9. Scripts

Tous les scripts doivent :

* être idempotents lorsque cela est possible ;
* comporter un en-tête standardisé ;
* être commentés uniquement lorsque cela améliore réellement la compréhension ;
* être testés avant publication.

---

# 10. Supervision

Chaque composant déployé doit répondre aux questions suivantes :

* Comment vérifier qu'il fonctionne ?
* Comment détecter une panne ?
* Comment être alerté ?
* Quels indicateurs surveiller ?

Lorsqu'un composant est compatible avec ZABBIX01, un chapitre dédié à la supervision est attendu.

---

# 11. Limites

Chaque document doit présenter les limites de la solution étudiée.

Exemples :

* menaces non couvertes ;
* faux positifs possibles ;
* impacts sur les performances ;
* cas où une autre solution est préférable.

Aucun outil ne doit être présenté comme une solution universelle.

---

# 12. Sources

Les sources doivent être :

* officielles lorsque cela est possible ;
* récentes ;
* reconnues par la communauté.

Les principaux référentiels utilisés dans le projet sont :

* ANSSI ;
* NIST ;
* OWASP ;
* MITRE ATT&CK ;
* SOCLE de Stéphane Robert ;
* IT-Connect (Florian Burnel).

Les sources sont systématiquement citées. Les contenus sont reformulés et ne doivent pas être reproduits intégralement.

---

# 13. Philosophie pédagogique

Le projet privilégie l'apprentissage par la compréhension.

Chaque module doit permettre au lecteur de répondre à quatre questions :

* Pourquoi ce composant existe-t-il ?
* Quel problème résout-il ?
* Comment le mettre en œuvre ?
* Comment démontrer qu'il fonctionne ?

L'objectif n'est pas de reproduire des commandes, mais de développer une démarche d'analyse et de justification des choix techniques.

---

# 14. Critères de publication

Un document est considéré comme publiable uniquement si :

* son contenu a été relu ;
* les commandes ont été testées ;
* les références ont été vérifiées ;
* les limites sont documentées ;
* la supervision est décrite lorsqu'elle est applicable.

---

# 15. Amélioration continue

Cette charte est un document vivant.

Toute évolution devra améliorer la qualité pédagogique, technique ou documentaire du projet sans remettre en cause les principes fondateurs définis dans le PROJECT_CHARTER.
