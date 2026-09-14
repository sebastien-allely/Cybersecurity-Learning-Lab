# 04 - Surface d'attaque

| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | CrowdSec |
| **Catégorie** | Architecture |
| **Objectif** | Identifier la surface d'attaque associée à CrowdSec et aux composants nécessaires à son fonctionnement. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Composants exposés

CrowdSec doit limiter autant que possible les composants accessibles depuis le réseau.

La **Local API (LAPI)** constitue notamment un composant sensible.

Elle doit être accessible uniquement aux composants qui en ont réellement besoin.

---

# Surface locale

La surface d'attaque de CrowdSec comprend notamment :

* le processus CrowdSec ;
* ses fichiers de configuration ;
* les parsers ;
* les scénarios ;
* les décisions ;
* la LAPI ;
* les fichiers journaux ;
* les mécanismes de remédiation.

Une compromission de la configuration pourrait modifier le comportement de détection ou de réaction.

---

# Surface réseau

Les communications nécessaires entre les composants doivent être limitées.

Le laboratoire doit éviter toute exposition inutile de la LAPI ou d'une interface d'administration.

Les ports et services effectivement utilisés doivent être documentés dans la configuration du laboratoire.

---

# Surface liée aux journaux

Les journaux constituent une donnée d'entrée critique.

Un attaquant capable de modifier, supprimer ou falsifier les événements analysés par CrowdSec pourrait réduire l'efficacité de la détection.

Les permissions sur les fichiers de journaux doivent donc être maîtrisées.

---

# Réduction de la surface d'attaque

Les principes retenus sont :

* limiter les services actifs ;
* limiter les communications réseau ;
* protéger les fichiers de configuration ;
* protéger les journaux ;
* limiter les privilèges du service ;
* ne pas exposer inutilement la LAPI ;
* superviser le fonctionnement de CrowdSec.
