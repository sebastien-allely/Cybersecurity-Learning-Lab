Nom du document : Guide de rédaction de la documentation
Technologie : Markdown
Catégorie : Documentation
Objectif : Définir les règles communes de rédaction, de structuration et de validation des documents du projet
Auteur : Sébastien ALLELY
Version : 1.0
Date de dernière modification : 2026-09-12

# Guide de rédaction de la documentation

## 1. Objectif

Ce document définit les règles communes applicables à la documentation du projet.

L'objectif est de garantir une documentation :

* cohérente ;
* lisible ;
* techniquement précise ;
* reproductible ;
* pédagogique ;
* maintenable dans le temps.

La documentation doit permettre à un lecteur de comprendre non seulement **comment** une solution est mise en œuvre, mais également **pourquoi** elle a été choisie.

## 2. Structure d'un document

Chaque document doit présenter une structure adaptée à son objectif.

Lorsque cela est pertinent, l'organisation suivante est privilégiée :

1. Objectif
2. Contexte
3. Périmètre
4. Pré-requis
5. Description technique
6. Mise en œuvre
7. Vérification
8. Sécurité
9. Limites
10. Références

Toutes les sections ne sont pas obligatoires. Elles doivent être utilisées uniquement lorsqu'elles apportent une information utile.

## 3. Métadonnées obligatoires

Chaque document Markdown doit commencer par les sept métadonnées suivantes :

* **Nom du document**
* **Technologie**
* **Catégorie**
* **Objectif**
* **Auteur**
* **Version**
* **Date de dernière modification**

Ces informations permettent d'identifier rapidement le rôle et le contexte du document.

Aucune section supplémentaire dédiée au versionnement n'est nécessaire.

## 4. Principes de rédaction

La rédaction doit privilégier :

* des phrases courtes ;
* une information par paragraphe ;
* des titres explicites ;
* des listes lorsque plusieurs éléments sont énumérés ;
* des exemples lorsque ceux-ci facilitent la compréhension ;
* un vocabulaire technique précis.

Les affirmations techniques doivent être vérifiables ou accompagnées d'une source lorsque cela est nécessaire.

Les choix d'architecture et de sécurité doivent être justifiés lorsqu'ils ont un impact significatif.

## 5. Explication des termes techniques

Un terme spécialisé doit être expliqué lors de sa première utilisation lorsque le public visé peut ne pas le connaître.

Exemple :

> Le RPO (*Recovery Point Objective*) définit la quantité maximale de données qu'une organisation accepte de perdre après un incident.

Après cette première définition, l'acronyme peut être utilisé normalement.

Cette règle concerne notamment :

* les acronymes ;
* les concepts de cybersécurité ;
* les mécanismes techniques ;
* les technologies spécifiques ;
* les termes d'administration système et réseau.

## 6. Commandes et procédures

Les commandes doivent être présentées dans des blocs de code.

Lorsqu'une commande est proposée dans une procédure, son objectif doit être expliqué avant son utilisation.

Exemple :

> Cette commande permet de vérifier l'état du service SSH :

```bash
systemctl status ssh
```

Les commandes dangereuses ou susceptibles de modifier durablement le système doivent être explicitement identifiées.

Une procédure doit distinguer autant que possible :

* la commande ;
* son objectif ;
* le résultat attendu ;
* l'interprétation du résultat.

## 7. Configuration

Les exemples de configuration doivent utiliser des valeurs génériques lorsque les données réelles ne sont pas nécessaires à la compréhension.

Les valeurs spécifiques à l'environnement réel ne doivent pas être publiées lorsqu'elles permettent d'identifier l'infrastructure.

Les exemples publics doivent privilégier des valeurs telles que :

* `192.168.1.0/24` pour un réseau de démonstration ;
* `PVE1` et `PVE2` pour les nœuds Proxmox ;
* `AD` pour le contrôleur de domaine ;
* `GLPI01` pour le serveur GLPI ;
* `ZABBIX01` pour le serveur Zabbix.

## 8. Séparation entre faits, choix et recommandations

La documentation doit distinguer trois types d'informations.

### 8.1 Fait technique

Information directement observable ou vérifiable dans l'environnement.

Exemple :

> Le laboratoire utilise deux nœuds Proxmox.

### 8.2 Choix d'architecture

Décision prise dans le cadre du projet et associée à une justification.

Exemple :

> La supervision est centralisée avec Zabbix afin de disposer d'un point de visibilité commun sur les composants du laboratoire.

### 8.3 Recommandation

Bonne pratique ou amélioration qui n'est pas nécessairement déployée dans l'environnement actuel.

Exemple :

> Une architecture comportant plusieurs contrôleurs de domaine permettrait de réduire le risque associé à la perte du contrôleur de domaine unique.

Cette distinction évite de présenter une recommandation comme une fonctionnalité réellement déployée.

## 9. Approche sécurité

Lorsque cela est pertinent, les documents doivent présenter les mécanismes de sécurité sous plusieurs angles.

### Blue Team

Le *Blue Team* représente les activités défensives : prévention, durcissement, supervision, détection, investigation et réponse à incident.

### Red Team

Le *Red Team* représente les activités offensives ou de simulation d'attaque permettant d'évaluer la résistance du système.

La documentation doit privilégier une approche contrôlée et pédagogique pour les tests offensifs.

## 10. Références

## 10. Références

Les informations techniques importantes doivent être confrontées à des sources fiables et adaptées au sujet traité.

Les sources privilégiées sont notamment :

* **ANSSI** : recommandations et référentiels de cybersécurité ;
* **NIST** : normes, publications et cadres méthodologiques ;
* **OWASP** : sécurité des applications et bonnes pratiques ;
* **MITRE ATT&CK** : référentiel de connaissances sur les tactiques et techniques d'attaque ;
* **SOCLE de Stéphane Robert** : guide technique et référence d'implémentation pour les mesures de sécurité et de durcissement lorsqu'il propose une mesure applicable au laboratoire ;
* **documentations officielles des éditeurs** : installation, configuration, fonctionnement et recommandations propres aux technologies utilisées ;
* **guides techniques reconnus** : compléments pratiques lorsque les sources précédentes ne couvrent pas suffisamment le sujet.

Le **SOCLE de Stéphane Robert** est utilisé comme **référence technique d'implémentation**. Il ne constitue pas un référentiel normatif et ne doit pas être présenté comme tel.

Une référence doit permettre au lecteur de retrouver la source utilisée.

Les sources doivent être sélectionnées selon leur :

* autorité ;
* actualité ;
* pertinence ;
* précision ;
* adéquation avec le sujet traité.

Lorsqu'une mesure de sécurité ou de durcissement est directement issue du SOCLE de Stéphane Robert, celui-ci doit être explicitement cité dans le document concerné.


## 11. Anonymisation

La documentation destinée à être publiée ne doit contenir aucune information permettant d'identifier directement l'environnement réel.

Sont notamment concernés :

* adresses IP réelles ;
* noms de domaine internes ;
* noms d'hôtes réels ;
* noms d'utilisateurs ;
* comptes de service ;
* chemins de fichiers spécifiques ;
* noms de partages ;
* identifiants ;
* informations personnelles ;
* informations permettant d'identifier l'organisation ou l'infrastructure.

Les valeurs génériques
