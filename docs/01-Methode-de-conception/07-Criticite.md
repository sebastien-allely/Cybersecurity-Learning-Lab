# 05 - Criticité

| Élément | Valeur |
| **Nom du document** | `05-Criticite.md` |
| **Technologie** | Méthode de conception |
| **Catégorie** | Méthodologie |
| **Objectif** | Définir la prise en compte de la criticité dans les décisions de sécurité du laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Principe

Tous les actifs du laboratoire n'ont pas la même importance.

La criticité permet de hiérarchiser les efforts de protection, de supervision, de sauvegarde et de restauration.

---

# Critères

La criticité doit notamment prendre en compte :

* l'impact d'une indisponibilité ;
* l'impact d'une compromission ;
* la sensibilité des données ;
* les dépendances ;
* la capacité de propagation ;
* l'exposition ;
* la difficulté de restauration.

---

# Exemple de hiérarchisation

Un composant central de l'infrastructure peut présenter une criticité supérieure à un service expérimental isolé.

Par exemple, une compromission d'un service d'annuaire peut avoir des conséquences beaucoup plus importantes qu'une compromission d'une machine de test isolée.

La criticité doit donc être déterminée par **l'impact potentiel**, et non par la technologie utilisée.

---

# Conséquences

La criticité influence notamment :

* le niveau de durcissement ;
* la fréquence de supervision ;
* la stratégie de sauvegarde ;
* les contrôles d'intégrité ;
* les exigences de restauration ;
* le niveau de documentation ;
* la priorité de traitement des vulnérabilités.

---

# Réévaluation

La criticité n'est pas nécessairement permanente.

Elle doit être réévaluée lorsqu'un actif :

* change de rôle ;
* reçoit de nouvelles données ;
* devient davantage exposé ;
* acquiert de nouvelles dépendances ;
* devient nécessaire à un autre composant.
