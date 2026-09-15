# 04 - Surface d'attaque

| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | ClamAV |
| **Catégorie** | Architecture |
| **Objectif** | Identifier la surface d'attaque et les dépendances techniques associées à ClamAV. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Composants exposés

ClamAV ne nécessite pas nécessairement l'exposition d'une interface réseau pour effectuer des analyses locales.

La surface d'attaque dépend donc principalement :

* des composants installés ;
* des processus actifs ;
* des fichiers de configuration ;
* des mécanismes de mise à jour ;
* des interfaces éventuellement utilisées par les autres services.

---

# Base de signatures

La base de signatures constitue un composant critique.

Une base :

* obsolète ;
* corrompue ;
* incomplète ;

réduit directement la capacité de détection.

La mise à jour doit donc être considérée comme une dépendance de sécurité.

---

# Permissions

Les permissions sur :

* les fichiers de configuration ;
* les bases de signatures ;
* les journaux ;
* les répertoires analysés ;
* la quarantaine ;

doivent être maîtrisées.

Une analyse exécutée avec des privilèges insuffisants peut produire un résultat incomplet.

---

# Quarantaine

Lorsque la quarantaine est utilisée, son contenu doit être protégé contre :

* l'exécution accidentelle ;
* l'accès non autorisé ;
* la suppression involontaire ;
* la réintroduction d'un fichier malveillant.

---

# Réduction de la surface

Les principes retenus sont :

* installer uniquement les composants nécessaires ;
* limiter les interfaces réseau ;
* protéger les fichiers de configuration ;
* protéger la base de signatures ;
* contrôler les permissions ;
* limiter les répertoires analysés à ceux présentant un intérêt ;
* superviser le fonctionnement.
