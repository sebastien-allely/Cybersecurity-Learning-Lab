# 04 - Réduction de la surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Reduction-de-la-surface-d-attaque.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Chaque fonctionnalité activée, chaque module chargé et chaque information exposée augmentent potentiellement la surface d'attaque d'un serveur Web.

L'objectif est de limiter cette surface aux seuls composants répondant à un besoin opérationnel identifié.

---

# 2. Actifs concernés

Les décisions concernent notamment :

- les modules Apache ;
- les Virtual Hosts ;
- les informations retournées aux clients ;
- les répertoires publiés ;
- les méthodes HTTP ;
- les fichiers de configuration.

---

# 3. Risques identifiés

Une surface d'attaque excessive peut entraîner :

- l'exploitation d'une fonctionnalité inutile ;
- la divulgation d'informations techniques ;
- l'exposition involontaire de ressources sensibles ;
- une augmentation des possibilités de compromission.

---

# 4. Principes de conception

## Charger uniquement les modules nécessaires

Chaque module augmente :

- le volume de code exécuté ;
- la complexité de maintenance ;
- le nombre potentiel de vulnérabilités.

Un module sans justification doit être désactivé.

---

## Limiter les informations divulguées

Apache ne doit exposer que les informations nécessaires au fonctionnement des applications.

Les informations techniques susceptibles d'aider un attaquant doivent être limitées.

---

## Publier uniquement les ressources nécessaires

Les répertoires, fichiers et applications accessibles doivent répondre à un besoin clairement identifié.

Les contenus de démonstration, de test ou obsolètes ne doivent pas être publiés.

---

## Limiter les fonctionnalités inutiles

Les fonctionnalités non utilisées doivent être désactivées afin de réduire les possibilités d'exploitation.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- désactiver les modules inutilisés ;
- limiter les informations renvoyées dans les réponses HTTP ;
- supprimer les pages de démonstration ;
- désactiver l'indexation automatique des répertoires lorsqu'elle n'est pas nécessaire ;
- supprimer les Virtual Hosts obsolètes ;
- limiter les méthodes HTTP aux besoins réels des applications.

Chaque décision doit être documentée et justifiée.

---

# 6. Vérification

Une revue régulière doit permettre de vérifier :

- les modules activés ;
- les Virtual Hosts publiés ;
- les méthodes HTTP autorisées ;
- les informations exposées par Apache ;
- les répertoires accessibles ;
- les contenus devenus inutiles.

Toute fonctionnalité non justifiée doit être supprimée.

---

# 7. Supervision

Les éléments suivants présentent un intérêt pour la supervision :

- modification des fichiers de configuration (si un contrôle d'intégrité est déployé) ;
- activation ou suppression d'un Virtual Host ;
- indisponibilité d'un site publié ;
- apparition d'une nouvelle exposition réseau non documentée.

La supervision doit permettre de détecter une dérive de configuration sans générer d'alertes inutiles.

---

# 8. Bonnes pratiques de conception

Avant d'activer une nouvelle fonctionnalité, il convient de répondre aux questions suivantes :

- Quel besoin couvre-t-elle ?
- Quel risque supplémentaire introduit-elle ?
- Existe-t-il une alternative plus simple ?
- Peut-elle être supprimée ultérieurement sans impact ?
- Comment sera-t-elle maintenue ?
- Comment sera-t-elle supervisée ?

Une fonctionnalité non justifiée ne doit pas être activée.

---

# 9. Conclusion

La réduction de la surface d'attaque constitue l'une des mesures les plus efficaces pour diminuer le risque de compromission.

Le principe retenu est simple : conserver uniquement les fonctionnalités répondant à un besoin identifié et supprimer tout le reste.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Apache HTTP Server.

## Guides techniques

- SOCLE – Stéphane Robert (durcissement des services Web et réduction de la surface d'attaque).

## Veille

Toute nouvelle fonctionnalité ou module devra être évalué avant son activation afin de vérifier qu'il répond à un besoin réel et qu'il ne remet pas en cause les objectifs de sécurité définis par le référentiel.
