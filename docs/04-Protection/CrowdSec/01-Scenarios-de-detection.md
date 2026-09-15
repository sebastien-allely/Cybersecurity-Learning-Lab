# 01 - Scénarios de détection

| Élément                           | Valeur                                                                                     |
| --------------------------------- | ------------------------------------------------------------------------------------------ |
| **Nom du document**               | `01-Scenarios-de-detection.md`                                                             |
| **Technologie**                   | CrowdSec                                                                                   |
| **Catégorie**                     | Protection                                                                                 |
| **Objectif**                      | Expliquer le rôle des scénarios CrowdSec dans la détection des comportements malveillants. |
| **Auteur**                        | Sébastien Allely                                                                           |
| **Version**                       | 1.0                                                                                        |
| **Date de dernière modification** | 05/08/2026                                                                                 |

---

## 1. Rôle d'un scénario

Un scénario CrowdSec analyse une succession d'événements afin d'identifier un comportement correspondant à une menace.

Il se situe après l'acquisition et l'analyse des journaux.

```text
Log
 ↓
Parser
 ↓
Scénario
 ↓
Détection
```

Le scénario ne remplace donc pas le parser.

Le parser transforme le journal en événement exploitable tandis que le scénario recherche une séquence d'événements correspondant à un comportement.

---

## 2. Principe de fonctionnement

Un scénario peut notamment prendre en compte :

* le nombre d'événements ;
* leur fréquence ;
* leur nature ;
* leur origine ;
* leur succession ;
* une fenêtre temporelle.

Cette approche permet de détecter des comportements qui ne seraient pas nécessairement significatifs lorsqu'ils sont considérés individuellement.

---

## 3. Exemple conceptuel

Une succession d'échecs d'authentification peut être représentée ainsi :

```text
Échec
Échec
Échec
Échec
Échec
 ↓
Seuil atteint
 ↓
Détection
```

Le seuil et la fenêtre temporelle dépendent du scénario.

Il est important de ne pas modifier arbitrairement ces paramètres sans vérifier leur impact sur les faux positifs et les faux négatifs.

---

## 4. Validation

La validation d'un scénario doit être réalisée dans un environnement contrôlé.

L'exercice doit vérifier :

1. la génération de l'événement ;
2. sa présence dans les journaux ;
3. son traitement par le parser ;
4. le déclenchement du scénario ;
5. la création de la détection ;
6. la génération éventuelle d'une décision ;
7. la prise en compte par le mécanisme de remédiation.

---

## 5. Limites

Un scénario dépend directement de la qualité des données qu'il reçoit.

Un journal incomplet, absent ou mal parsé peut empêcher une détection.

Il est donc incorrect d'évaluer uniquement la qualité d'un scénario sans vérifier l'ensemble de la chaîne de détection.
