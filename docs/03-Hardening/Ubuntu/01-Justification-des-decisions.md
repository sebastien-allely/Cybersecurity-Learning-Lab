# 01 - Justification des décisions

| Élément                           | Valeur                                                                                                      |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `01-Justification-des-decisions.md`                                                                         |
| **Technologie**                   | Ubuntu                                                                                                      |
| **Catégorie**                     | Hardening                                                                                                   |
| **Objectif**                      | Définir les principes permettant de justifier les décisions de durcissement appliquées aux systèmes Ubuntu. |
| **Auteur**                        | Sébastien Allely                                                                                            |
| **Version**                       | 1.0                                                                                                         |
| **Date de dernière modification** | 02/08/2026                                                                                                  |

---

## 1. Principe général

Le durcissement d'un système Ubuntu doit être guidé par le risque et par le rôle du système.

Une modification n'est pas pertinente simplement parce qu'elle est recommandée dans une documentation générique.

Elle doit répondre à un besoin de sécurité identifié tout en conservant les fonctionnalités nécessaires.

---

## 2. Principes retenus

Les décisions de durcissement reposent notamment sur :

* le moindre privilège ;
* la réduction de la surface d'attaque ;
* la limitation de l'exposition réseau ;
* la protection des comptes ;
* la protection des fichiers de configuration ;
* la journalisation ;
* la supervision ;
* la gestion des vulnérabilités ;
* la sauvegarde ;
* la réversibilité des changements.

---

## 3. Analyse avant modification

Avant de modifier un système, il convient d'identifier :

* son rôle ;
* les services utilisés ;
* les utilisateurs ;
* les flux réseau ;
* les dépendances ;
* les fichiers de configuration ;
* les mécanismes de supervision ;
* les mécanismes de sauvegarde.

Cette analyse évite d'appliquer une mesure de sécurité qui provoquerait une perte de fonctionnalité.

---

## 4. Arbitrage sécurité / disponibilité

Une mesure de sécurité doit être évaluée en fonction de son impact.

Une configuration extrêmement restrictive mais incompatible avec le rôle du système n'est pas une bonne configuration de sécurité.

L'objectif est de rechercher un niveau de protection cohérent avec le risque accepté.

---

## 5. Traçabilité

Les décisions importantes doivent être documentées.

La documentation doit permettre de répondre à trois questions :

1. Quel risque cherchait-on à réduire ?
2. Quelle mesure a été retenue ?
3. Pourquoi cette mesure est-elle adaptée au système ?

---

## 6. Réversibilité

Les changements importants doivent être réversibles.

Avant une modification critique :

* sauvegarder le fichier de configuration ;
* vérifier la syntaxe ;
* appliquer la modification ;
* contrôler le service ;
* vérifier les journaux ;
* tester le fonctionnement.

Les fichiers de configuration critiques doivent être **protégés et sauvegardés**.
