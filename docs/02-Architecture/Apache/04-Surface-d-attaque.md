# 04 - Surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les principaux éléments constituant la surface d'attaque d'Apache HTTP Server. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La surface d'attaque représente l'ensemble des éléments susceptibles d'être utilisés pour compromettre un serveur Apache.

L'objectif est d'identifier ces points d'exposition afin de décider lesquels sont réellement nécessaires et lesquels peuvent être supprimés, limités ou renforcés.

La réduction de la surface d'attaque constitue l'un des principes fondamentaux du référentiel de conception.

---

# 2. Définition

Pour Apache HTTP Server, la surface d'attaque comprend notamment :

- les services réseau exposés ;
- les interfaces d'administration ;
- les modules chargés ;
- les applications Web publiées ;
- les mécanismes d'authentification ;
- les certificats TLS ;
- les fichiers de configuration ;
- les dépendances logicielles.

Chaque élément supplémentaire augmente potentiellement le risque de compromission.

---

# 3. Services exposés

Les principaux services pouvant être exposés sont :

- HTTP ;
- HTTPS.

Selon l'architecture retenue, d'autres services peuvent être accessibles indirectement (reverse proxy, authentification externe, supervision...).

Chaque service exposé doit répondre à un besoin clairement identifié.

---

# 4. Applications publiées

Chaque application Web augmente la surface d'attaque du serveur.

Avant de publier une application, il convient de se demander :

- est-elle réellement nécessaire ?
- est-elle maintenue ?
- est-elle régulièrement mise à jour ?
- possède-t-elle sa propre stratégie de sécurité ?

La sécurité d'Apache dépend également de la sécurité des applications qu'il héberge.

---

# 5. Modules Apache

Chaque module chargé ajoute de nouvelles fonctionnalités.

Il augmente également :

- le volume de code exécuté ;
- le nombre de composants à maintenir ;
- les possibilités d'exploitation d'une vulnérabilité.

Le principe retenu est de ne charger que les modules strictement nécessaires.

---

# 6. Authentification

Lorsqu'une interface est protégée par authentification, il convient d'analyser :

- le mécanisme utilisé ;
- les privilèges accordés ;
- le nombre de comptes concernés ;
- les journaux produits.

Une authentification mal conçue peut constituer un point d'entrée pour un attaquant.

---

# 7. Configuration

Les fichiers de configuration représentent eux aussi une surface d'attaque.

Une mauvaise configuration peut notamment entraîner :

- une fuite d'informations ;
- l'activation involontaire d'une fonctionnalité ;
- l'exposition de ressources sensibles ;
- un affaiblissement du niveau de sécurité.

---

# 8. Dépendances

Apache dépend de plusieurs composants pouvant eux-mêmes introduire des risques :

- système d'exploitation ;
- PHP ;
- bibliothèques TLS ;
- modules tiers ;
- DNS ;
- base de données.

Le niveau de sécurité global dépend également de ces composants.

---

# 9. Réduction de la surface d'attaque

Le référentiel retient notamment les principes suivants :

- ne publier que les applications nécessaires ;
- désactiver les modules inutilisés ;
- limiter les services exposés ;
- supprimer les pages de démonstration ;
- contrôler les accès d'administration ;
- maintenir les composants à jour ;
- documenter toute exception.

---

# 10. Vérification

Une revue régulière doit permettre de vérifier :

- les ports ouverts ;
- les modules activés ;
- les applications publiées ;
- les interfaces accessibles ;
- les certificats utilisés ;
- les dépendances installées.

Toute exposition non justifiée doit être analysée.

---

# 11. Conclusion

La réduction de la surface d'attaque ne consiste pas à ajouter des mécanismes de sécurité.

Elle consiste avant tout à supprimer les éléments inutiles et à ne conserver que les fonctionnalités répondant à un besoin clairement identifié.

Cette démarche contribue directement à réduire les risques identifiés lors de l'analyse des risques.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- EBIOS Risk Manager.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Apache HTTP Server.

## Guides techniques

- SOCLE – Stéphane Robert (durcissement des services Web et des systèmes Linux).

## Veille

Toute nouvelle fonctionnalité, module ou application publiée devra faire l'objet d'une réévaluation de la surface d'attaque avant sa mise en production.
