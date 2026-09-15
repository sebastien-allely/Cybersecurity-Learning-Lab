### `docs/06-Incident-Response/07-Retour-d-experience.md`

# 07 - Retour d'expérience

| Élément                           | Valeur                                                              |
| --------------------------------- | ------------------------------------------------------------------- |
| **Nom du document**               | `07-Retour-d-experience.md`                                         |
| **Technologie**                   | Incident Response                                                   |
| **Catégorie**                     | Incident Response                                                   |
| **Objectif**                      | Exploiter les incidents et exercices pour améliorer le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                    |
| **Version**                       | 1.0                                                                 |
| **Date de dernière modification** | 05/08/2026                                                          |

---

## 1. Objectif

La réponse à incident ne se termine pas avec la restauration du service.

L'événement doit permettre d'améliorer le laboratoire.

---

## 2. Questions

Après un incident ou un exercice, rechercher notamment :

* L'événement a-t-il été détecté ?
* La détection était-elle suffisamment rapide ?
* Les informations disponibles étaient-elles suffisantes ?
* L'alerte était-elle exploitable ?
* La cause a-t-elle pu être déterminée ?
* Le confinement était-il adapté ?
* La remédiation était-elle efficace ?
* La restauration a-t-elle fonctionné ?
* Une information importante manquait-elle ?

---

## 3. Améliorations

Le retour d'expérience peut conduire à :

* modifier une supervision ;
* créer une nouvelle alerte ;
* modifier un seuil ;
* renforcer un système ;
* améliorer une procédure ;
* créer un nouvel exercice ;
* modifier la documentation ;
* ajouter une automatisation.

---

## 4. Boucle d'amélioration

```text
Incident / Exercice
        ↓
Analyse
        ↓
Constats
        ↓
Actions d'amélioration
        ↓
Modification
        ↓
Validation
        ↓
Documentation
```

Cette boucle rejoint le principe d'amélioration continue du laboratoire.
