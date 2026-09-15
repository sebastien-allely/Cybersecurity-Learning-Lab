# Création de filtres personnalisés


| Élément | Valeur |
| **Nom du document** | `07-Creation-filtres-personnalises.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Protection |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |




---

# 1. Objectif

Les filtres constituent le cœur du fonctionnement de Fail2ban. Ils permettent d'analyser les journaux générés par les services du système afin d'identifier des comportements susceptibles de révéler une tentative d'attaque.

Chaque filtre repose sur une ou plusieurs expressions régulières (*regular expressions* ou *regex*) qui recherchent des motifs spécifiques dans les fichiers de journalisation. Lorsqu'un événement correspond à une règle définie dans un filtre, Fail2ban peut incrémenter un compteur d'échecs. Si le seuil configuré dans la *jail* est atteint, une action est exécutée, comme le bannissement temporaire de l'adresse IP concernée.

Ce document présente la méthodologie retenue dans le cadre du **Cybersecurity Learning Lab** pour concevoir, tester et maintenir des filtres personnalisés fiables et facilement maintenables.

---

## 1.1 Pourquoi créer un filtre personnalisé ?

Fail2ban est distribué avec un grand nombre de filtres officiels couvrant les services les plus courants :

- OpenSSH ;
- Apache HTTP Server ;
- Nginx ;
- MariaDB / MySQL ;
- Postfix ;
- Dovecot ;
- vsftpd ;
- etc.

Dans de nombreux cas, ces filtres répondent parfaitement au besoin et doivent être privilégiés.

Cependant, certaines applications produisent des journaux qui ne sont pas couverts par les filtres officiels. D'autres nécessitent une détection plus spécifique afin d'identifier des comportements propres à leur fonctionnement.

C'est notamment le cas de :

- GLPI01 ;
- Proxmox VE ;
- certaines applications métiers ;
- des développements internes.

Dans ces situations, il devient nécessaire de développer un filtre personnalisé.

---

## 1.2 Quand utiliser un filtre officiel ?

Les filtres officiels doivent toujours être privilégiés lorsqu'ils répondent au besoin.

Ils présentent plusieurs avantages :

- ils sont maintenus par la communauté Fail2ban ;
- ils bénéficient des corrections et améliorations apportées au projet ;
- ils sont largement testés dans différents environnements ;
- ils réduisent les développements spécifiques à maintenir.

Le développement d'un filtre personnalisé ne doit donc jamais être le premier choix.

---

## 1.3 Quand développer un filtre spécifique ?

Un filtre personnalisé est justifié lorsqu'au moins l'une des situations suivantes est rencontrée :

- aucun filtre officiel n'existe pour le service concerné ;
- les journaux de l'application utilisent un format spécifique ;
- une menace particulière n'est pas détectée par les filtres existants ;
- une logique métier propre à l'application doit être surveillée.

Dans le cadre du Cybersecurity Learning Lab, les filtres personnalisés développés concernent principalement :

- GLPI01 ;
- Proxmox VE.

L'objectif n'est pas de remplacer les filtres officiels, mais de compléter les fonctionnalités de Fail2ban lorsque cela apporte une réelle valeur ajoutée.

---

# 2. Fonctionnement d'un filtre Fail2ban

Un filtre Fail2ban est un fichier de configuration chargé d'analyser les journaux d'un ou plusieurs services afin d'identifier des événements correspondant à une tentative d'attaque.

Contrairement à une idée reçue, Fail2ban ne surveille pas directement un service. Il surveille les journaux générés par ce service et recherche des motifs définis à l'aide d'expressions régulières.

Lorsqu'un événement correspond à une règle du filtre, celui-ci est transmis à la *jail*. La *jail* applique alors sa propre logique (nombre maximal de tentatives, durée d'observation, durée du bannissement, action à exécuter, etc.).

Le filtre et la *jail* sont donc deux composants distincts mais complémentaires :

- le **filtre** détecte les événements ;
- la **jail** décide de la réponse à apporter.

---

## 2.1 Principe général

Le fonctionnement de Fail2ban peut être résumé par le schéma suivant :

```text
        Requête réseau
              │
              ▼
      Service surveillé
 (SSH, Apache, GLPI01, ...)
              │
              ▼
     Fichier de journal
 (/var/log/auth.log, access.log, ...)
              │
              ▼
     Filtre Fail2ban (.conf)
              │
      Correspondance ?
        Oui / Non
              │
              ▼
          Jail active
              │
   Dépassement du seuil ?
        Oui / Non
              │
              ▼
        Action exécutée
(iptables, nftables, firewalld...)
```

Chaque composant possède une responsabilité clairement définie :

| Composant | Rôle |
|-----------|------|
| Service | Génère les journaux. |
| Journal | Contient les événements à analyser. |
| Filtre | Recherche les événements correspondant à une menace. |
| Jail | Détermine quand une adresse IP doit être bannie. |
| Action | Applique le bannissement via le pare-feu. |

---

## 2.2 Anatomie d'un filtre

Un filtre est un simple fichier texte placé dans :

```text
/etc/fail2ban/filter.d/
```

La structure générale est la suivante :

```ini
[INCLUDES]

before = common.conf

[Definition]

failregex = ...

ignoreregex =

datepattern =
```

Les principales sections sont décrites ci-dessous.

### Section `[INCLUDES]`

Cette section permet d'importer un ou plusieurs fichiers communs fournis par Fail2ban.

L'utilisation de fichiers communs permet d'éviter de dupliquer certaines définitions et d'assurer une meilleure compatibilité avec les filtres officiels.

---

### Directive `before`

La directive `before` indique quel fichier doit être chargé avant le filtre courant.

Dans la majorité des cas, le fichier utilisé est :

```text
common.conf
```

Celui-ci contient notamment des définitions partagées par de nombreux filtres officiels.

---

### Section `[Definition]`

Cette section contient les règles de détection du filtre.

C'est dans cette partie que sont définies les expressions régulières permettant d'identifier les événements recherchés.

---

### Directive `failregex`

Il s'agit de l'élément le plus important du filtre.

Chaque expression régulière définit un motif qui, lorsqu'il est trouvé dans les journaux, est considéré comme un événement d'échec.

Une même section peut contenir plusieurs directives `failregex`.

Chaque ligne doit correspondre à un comportement précis.

---

### Directive `ignoreregex`

Cette directive permet d'exclure certains événements pourtant détectés par `failregex`.

Elle est principalement utilisée pour éviter les faux positifs.

Dans de nombreux filtres, cette directive reste volontairement vide.

---

### Directive `datepattern`

Cette directive permet d'indiquer à Fail2ban le format de date utilisé dans les journaux analysés.

Dans la majorité des cas, Fail2ban détecte automatiquement le format utilisé.

Cette directive n'est donc renseignée que lorsque cela est nécessaire.

---

# 3. Les expressions régulières

Les filtres Fail2ban s'appuient sur des expressions régulières (*regular expressions* ou *regex*) afin d'identifier des événements particuliers dans les fichiers de journalisation.

Une expression régulière est un motif de recherche permettant de reconnaître une chaîne de caractères précise ou un ensemble de chaînes partageant une même structure.

L'objectif de ce chapitre n'est pas de présenter l'ensemble de la syntaxe des expressions régulières, mais uniquement les éléments les plus utiles pour développer des filtres Fail2ban.

---

## 3.1 Les métacaractères les plus utilisés

Le tableau suivant présente les principaux éléments rencontrés dans les filtres Fail2ban.

| Expression | Signification | Exemple |
|------------|---------------|----------|
| `.` | N'importe quel caractère | `abc.def` |
| `*` | Zéro, une ou plusieurs occurrences | `test*` |
| `+` | Une ou plusieurs occurrences | `[0-9]+` |
| `?` | Élément optionnel | `https?` |
| `^` | Début de ligne | `^Failed` |
| `$` | Fin de ligne | `error$` |
| `()` | Groupe de capture | `(POST|GET)` |
| `[]` | Ensemble de caractères | `[0-9]` |
| `[^ ]` | Exclusion d'un caractère | `[^ ]+` |
| `|` | OU logique | `GET|POST` |

---

## 3.2 La macro `<HOST>`

Fail2ban fournit plusieurs macros permettant de simplifier les expressions régulières.

La plus importante est :

```text
<HOST>
```

Cette macro détecte automatiquement les adresses IPv4, IPv6 ainsi que les noms d'hôte lorsque cela est nécessaire.

Par exemple :

```text
^<HOST> .* authentication failure$
```

Il est fortement recommandé d'utiliser cette macro plutôt que de développer une expression régulière spécifique pour les adresses IP.

Cette approche améliore la lisibilité du filtre tout en assurant une meilleure compatibilité avec les évolutions de Fail2ban.

---

## 3.3 Capturer une méthode HTTP

Les journaux Apache utilisent généralement différentes méthodes HTTP.

Les plus courantes sont :

- GET
- POST
- HEAD
- OPTIONS
- PUT
- DELETE

Une expression régulière simple permettant de reconnaître plusieurs méthodes est :

```text
(GET|POST|HEAD)
```

Cette écriture permet de détecter plusieurs valeurs possibles avec une seule expression.

---

## 3.4 Capturer une ressource

Une attaque vise généralement une ressource particulière.

Par exemple :

```text
/wp-login.php
/phpmyadmin
/xmlrpc.php
/.env
```

Une expression régulière peut donc rechercher directement ces chemins.

Exemple :

```text
/wp-login\.php
```

Le caractère `.` étant un métacaractère, il doit être échappé avec `\`.

---

## 3.5 Bonnes pratiques

Lors du développement d'un filtre, il est recommandé de respecter les principes suivants :

- privilégier plusieurs expressions simples plutôt qu'une seule expression complexe ;
- utiliser les macros fournies par Fail2ban lorsque cela est possible ;
- commenter les filtres lorsqu'une expression régulière est difficile à comprendre ;
- tester chaque modification avec `fail2ban-regex` ;
- limiter les risques de faux positifs en développant des expressions suffisamment précises.

Une expression régulière plus courte, plus lisible et correctement testée sera généralement plus facile à maintenir qu'une expression complexe cherchant à couvrir tous les cas possibles.

---

# 4. Méthodologie de développement

Le développement d'un filtre Fail2ban doit suivre une démarche progressive. Écrire directement une expression régulière complexe est une source fréquente d'erreurs et de faux positifs.

Dans le cadre du **Cybersecurity Learning Lab**, chaque filtre est développé selon une méthodologie identique afin de garantir sa fiabilité, sa lisibilité et sa maintenabilité.

---

## 4.1 Étape 1 : Identifier le journal

La première étape consiste à identifier précisément le fichier de journal contenant les événements à analyser.

Quelques exemples :

| Service | Journal |
|----------|----------|
| OpenSSH | `/var/log/auth.log` |
| Apache | `/var/log/apache2/access.log` |
| Apache | `/var/log/apache2/error.log` |
| GLPI01 | `/var/log/apache2/access.log` |
| MariaDB | `/var/log/mysql/error.log` |
| Proxmox VE | selon le service concerné |

Avant d'écrire un filtre, il est indispensable de vérifier que les événements recherchés apparaissent bien dans les journaux.

---

## 4.2 Étape 2 : Identifier les événements

Il convient ensuite d'observer plusieurs événements réels.

Par exemple :

- tentative de connexion SSH invalide ;
- accès à `/wp-login.php` ;
- scan de `/phpmyadmin` ;
- tentative d'accès à `/.env` ;
- erreur d'authentification GLPI01.

L'objectif est d'identifier les éléments qui restent constants d'une ligne à l'autre.

---

## 4.3 Étape 3 : Écrire une première expression régulière

La première expression doit rester simple.

Il est préférable de détecter un seul événement avec certitude plutôt que plusieurs événements de manière imprécise.

Le développement se fait ensuite de manière incrémentale.

---

## 4.4 Étape 4 : Tester avec fail2ban-regex

Chaque modification doit être validée avec l'outil officiel :

```bash
fail2ban-regex <journal> <filtre>
```

Par exemple :

```bash
sudo fail2ban-regex /var/log/apache2/access.log \
/etc/fail2ban/filter.d/apache-security.conf
```

Le résultat doit permettre de vérifier :

- le nombre de lignes analysées ;
- le nombre de lignes détectées ;
- les lignes ignorées ;
- les éventuels faux positifs.

Cette étape est indispensable avant toute mise en production.

---

## 4.5 Étape 5 : Utiliser un fichier de test

Tester directement sur les journaux de production n'est pas toujours pratique.

Une bonne pratique consiste à créer un fichier contenant uniquement les événements à tester.

Exemple :

```text
/tmp/apache-test.log
```

Ce fichier permet :

- de reproduire les tests rapidement ;
- de conserver des cas de test représentatifs ;
- de valider les évolutions du filtre sans perturber les journaux de production.

---

## 4.6 Étape 6 : Réaliser des tests réels

Une fois le filtre validé avec un fichier de test, il convient de reproduire les événements sur le service réel.

Par exemple :

- effectuer plusieurs connexions SSH invalides ;
- accéder volontairement à une URL surveillée ;
- simuler une tentative de scan ;
- provoquer une erreur d'authentification.

Le comportement du filtre est ensuite vérifié à l'aide des journaux et des commandes de diagnostic de Fail2ban.

---

## 4.7 Étape 7 : Documenter le filtre

Chaque filtre développé dans le projet est documenté afin de faciliter sa compréhension et sa maintenance.

La documentation précise notamment :

- l'objectif du filtre ;
- les journaux utilisés ;
- les menaces détectées ;
- les expressions régulières employées ;
- les méthodes de validation ;
- les limites éventuelles.

Cette approche garantit la reproductibilité des travaux et facilite les évolutions futures.

---

# 5. Outils de validation

Le développement d'un filtre ne s'arrête pas à l'écriture d'une expression régulière. Avant toute mise en production, il est indispensable de valider son fonctionnement afin de vérifier qu'il détecte correctement les événements recherchés sans générer de faux positifs.

Fail2ban fournit plusieurs outils permettant de tester et de diagnostiquer un filtre.

---

## 5.1 fail2ban-regex

`fail2ban-regex` est l'outil officiel de validation des filtres.

Il permet de tester un filtre sur un fichier de journal sans avoir à démarrer la jail correspondante.

### Syntaxe

```bash
fail2ban-regex <journal> <filtre>
```

### Exemple

```bash
sudo fail2ban-regex \
/var/log/apache2/access.log \
/etc/fail2ban/filter.d/apache-security.conf
```

---

## 5.2 Tester avec un fichier dédié

Lors du développement, il est recommandé de créer un fichier contenant uniquement les événements à tester.

Exemple :

```text
/tmp/apache-test.log
```

Le filtre peut alors être testé de manière reproductible :

```bash
sudo fail2ban-regex \
/tmp/apache-test.log \
/etc/fail2ban/filter.d/apache-security.conf
```

Cette méthode présente plusieurs avantages :

- les résultats sont reproductibles ;
- les journaux de production restent inchangés ;
- les tests sont plus rapides ;
- les cas de test peuvent être conservés dans le projet.

---

## 5.3 Comprendre les résultats

À l'issue du test, Fail2ban affiche un résumé.

Exemple :

```text
Lines: 12 lines, 0 ignored, 12 matched, 0 missed
```

Les informations importantes sont les suivantes :

| Champ | Signification |
|--------|---------------|
| Lines | Nombre total de lignes analysées |
| Ignored | Lignes volontairement ignorées |
| Matched | Lignes reconnues par le filtre |
| Missed | Lignes non reconnues |

Un filtre correctement développé doit détecter les événements attendus tout en ignorant les événements légitimes.

---

## 5.4 Afficher les lignes non reconnues

Lorsque certaines lignes ne sont pas détectées, `fail2ban-regex` les affiche en fin de rapport.

Exemple :

```text
Missed line(s):
192.168.1.50 - - [18/Jul/2026:15:20:01 +0000] ...
```

Cette information permet d'identifier rapidement :

- une erreur dans l'expression régulière ;
- un format de journal inattendu ;
- une faute de syntaxe ;
- un oubli dans le filtre.

---

## 5.5 Vérifier le format des dates

Fail2ban détecte automatiquement la majorité des formats de date.

Le rapport indique notamment :

```text
Date template hits:
```

Si un format est correctement reconnu, il n'est généralement pas nécessaire d'utiliser la directive `datepattern`.

Il est recommandé de laisser Fail2ban gérer automatiquement cette détection lorsque cela est possible.

---

## 5.6 Tester progressivement

Une bonne pratique consiste à développer un filtre par étapes.

Par exemple :

1. détecter une seule URL ;
2. ajouter une seconde URL ;
3. ajouter une troisième URL ;
4. tester à nouveau ;
5. poursuivre progressivement.

Cette approche facilite le diagnostic en cas d'erreur et réduit le risque de créer une expression régulière trop complexe.

---

## 5.7 Vérifier le comportement réel

Une fois le filtre validé avec `fail2ban-regex`, il convient de vérifier son fonctionnement dans un environnement réel.

Les principales commandes de diagnostic sont :

```bash
sudo fail2ban-client status
```

Lister les jails actives.

```bash
sudo fail2ban-client status <jail>
```

Afficher les informations d'une jail.

```bash
sudo fail2ban-client status apache-security
```

Exemple pour la jail `apache-security`.

Les informations affichées permettent notamment de connaître :

- le nombre d'échecs détectés ;
- les journaux surveillés ;
- les adresses IP bannies ;
- les actions actuellement appliquées.

---

## Bonnes pratiques

Lors du développement d'un filtre personnalisé, il est recommandé de toujours :

- développer une expression régulière à la fois ;
- tester chaque modification avec `fail2ban-regex` ;
- conserver un fichier de test représentatif ;
- vérifier le comportement dans les journaux réels ;
- documenter les cas de test utilisés.

Cette méthodologie permet de produire des filtres fiables, reproductibles et faciles à maintenir.

---

# 6. Les erreurs courantes

Le développement d'un filtre personnalisé est souvent plus complexe qu'il n'y paraît. La majorité des difficultés ne proviennent pas de Fail2ban lui-même, mais d'une mauvaise compréhension des journaux analysés ou d'expressions régulières inadaptées.

Les erreurs suivantes sont parmi les plus fréquemment rencontrées.

---

## 6.1 Développer avant d'analyser les journaux

Une erreur fréquente consiste à écrire directement une expression régulière sans avoir étudié les journaux de l'application.

Chaque application possède son propre format de journalisation. Deux applications utilisant Apache peuvent produire des journaux très différents.

La première étape doit toujours être l'analyse des événements réellement enregistrés.

---

## 6.2 Utiliser une expression régulière trop complexe

Il est tentant de vouloir détecter plusieurs dizaines de cas avec une seule expression régulière.

Cette approche présente plusieurs inconvénients :

- difficulté de lecture ;
- maintenance compliquée ;
- risque accru de faux positifs ;
- débogage difficile.

Il est préférable d'utiliser plusieurs expressions simples qu'une seule expression difficile à comprendre.

---

## 6.3 Oublier de tester le filtre

Un filtre qui semble correct n'est pas nécessairement fonctionnel.

Chaque modification doit être validée avec :

```bash
fail2ban-regex
```

Cette étape permet de vérifier immédiatement :

- les événements détectés ;
- les événements ignorés ;
- les éventuelles erreurs de syntaxe.

---

## 6.4 Utiliser le mauvais fichier de journal

Avant de développer un filtre, il est indispensable d'identifier le journal réellement utilisé par le service.

Par exemple :

- Apache peut utiliser plusieurs VirtualHosts ;
- plusieurs fichiers d'accès peuvent coexister ;
- certains services écrivent dans le journal système.

Un filtre parfaitement développé ne détectera jamais un événement si la jail surveille un mauvais fichier.

---

## 6.5 Confondre filtre et jail

Le filtre ne réalise aucun bannissement.

Il se contente d'identifier des événements.

La décision de bannir une adresse IP appartient exclusivement à la jail.

Cette distinction est fondamentale pour comprendre le fonctionnement de Fail2ban.

---

## 6.6 Générer des faux positifs

Un filtre trop permissif peut détecter des utilisateurs parfaitement légitimes.

Les conséquences peuvent être importantes :

- blocage d'utilisateurs ;
- interruption d'un service ;
- difficultés de diagnostic.

Chaque filtre doit donc être testé avec des journaux représentatifs avant sa mise en production.

---

## 6.7 Ignorer les filtres officiels

Fail2ban est livré avec un grand nombre de filtres maintenus par la communauté.

Avant de développer un filtre personnalisé, il est recommandé de vérifier si un filtre officiel répond déjà au besoin.

Un filtre personnalisé ne doit être développé que lorsqu'il apporte une réelle valeur ajoutée.

---

## 6.8 Bonnes pratiques

Afin de limiter les erreurs, il est recommandé de :

- analyser les journaux avant toute écriture de filtre ;
- développer progressivement ;
- tester chaque modification ;
- documenter les cas de test ;
- privilégier les filtres officiels lorsque cela est possible ;
- limiter les expressions régulières aux seuls cas réellement nécessaires.

Cette démarche permet de produire des filtres plus fiables, plus lisibles et plus simples à maintenir.

---

# 7. Cas pratiques

Cette section présente plusieurs exemples inspirés des situations rencontrées lors de la réalisation du **Cybersecurity Learning Lab**.

L'objectif n'est pas de fournir des filtres complets, mais de montrer la démarche de développement utilisée dans un environnement réel.

---

## 7.1 Détection d'un scan WordPress

### Contexte

Le serveur ne contient aucun site WordPress.

Des requêtes sont néanmoins observées vers :

```text
/wp-login.php
/wp-admin/
```

### Analyse

Ces requêtes correspondent généralement à des scans automatisés réalisés par des robots recherchant des installations WordPress vulnérables.

### Décision

Utiliser le filtre officiel :

```text
apache-botsearch.conf
```

Aucun filtre personnalisé n'est nécessaire.

---

## 7.2 Détection d'un scan phpMyAdmin

### Contexte

Les journaux Apache montrent des accès répétés vers :

```text
/phpmyadmin
/pma
```

### Analyse

Ces requêtes correspondent à des tentatives de découverte d'une interface phpMyAdmin.

### Décision

Le filtre officiel Apache couvre déjà ce type de comportement.

Le développement d'un filtre spécifique n'est donc pas nécessaire.

---

## 7.3 Recherche de fichiers sensibles

### Contexte

Des robots tentent d'accéder à :

```text
/.env
/config.php
/.git
```

### Analyse

Ces fichiers peuvent contenir des informations sensibles ou des identifiants.

### Décision

Avant tout développement spécifique, vérifier si les filtres officiels répondent déjà au besoin.

Le développement d'un filtre personnalisé n'est envisagé qu'en l'absence de couverture satisfaisante.

---

## 7.4 Développement d'un filtre GLPI01

### Contexte

GLPI01 génère des événements spécifiques qui ne sont pas couverts par les filtres Apache.

Par exemple :

- erreurs d'authentification propres à GLPI01 ;
- comportements particuliers liés à l'application ;
- événements métiers.

### Analyse

Ces événements devront être étudiés directement dans les journaux de GLPI01 afin d'identifier les informations exploitables.

### Décision

Développer un filtre dédié uniquement lorsque les filtres officiels ne répondent pas au besoin.

---

## 7.5 Développement d'un filtre Proxmox VE

### Contexte

À ce jour, Fail2ban ne fournit pas de filtre officiel spécifique à Proxmox VE.

### Analyse

Le développement d'un filtre personnalisé nécessitera :

- l'identification des journaux concernés ;
- l'analyse des événements de sécurité ;
- la validation des expressions régulières ;
- des tests en environnement réel.

### Décision

Un document spécifique est consacré à cette étude dans le cadre du projet.

---

## 7.6 Retour d'expérience

Les travaux réalisés dans le cadre du Cybersecurity Learning Lab ont conduit à plusieurs constats.

- La compréhension des journaux est plus importante que l'écriture des expressions régulières.
- Les filtres officiels couvrent déjà une grande partie des besoins.
- Un filtre personnalisé doit répondre à un besoin clairement identifié.
- Une phase de test est indispensable avant toute mise en production.
- Une documentation claire facilite fortement la maintenance des filtres.

Cette méthodologie sera appliquée à l'ensemble des filtres développés dans le projet.
