# 04 - Analyse des risques

| Élément | Valeur |
| **Nom du document** | `04-Analyse-des-risques.md` |
| **Technologie** | Méthode de conception |
| **Catégorie** | Méthodologie |
| **Objectif** | Définir la méthode d'évaluation des risques appliquée aux actifs du laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Principe

Le risque résulte de la combinaison :

* d'une menace ;
* d'une vulnérabilité ou faiblesse exploitable ;
* d'un impact potentiel.

L'analyse permet de déterminer quelles mesures doivent être prioritaires.

---

# Démarche

Pour chaque scénario :

```text
Actif
  ↓
Menace
  ↓
Vulnérabilité
  ↓
Scénario de compromission
  ↓
Impact
  ↓
Risque
```

---

# Impacts

Les impacts doivent notamment être évalués sur :

* disponibilité ;
* intégrité ;
* confidentialité ;
* traçabilité ;
* capacité de restauration ;
* propagation à d'autres actifs.

---

# Traitement du risque

Une fois le risque identifié, plusieurs stratégies sont possibles :

* réduire le risque ;
* éviter le risque ;
* transférer le risque ;
* accepter le risque résiduel.

Dans le laboratoire, la réduction du risque constitue généralement l'approche privilégiée.

---

# Risque résiduel

Une mesure de sécurité ne supprime pas nécessairement totalement un risque.

Après traitement, il faut déterminer :

* ce qui reste exposé ;
* pourquoi cela reste acceptable ;
* quelles mesures supplémentaires seraient possibles ;
* pourquoi elles ne sont éventuellement pas retenues.

Cette notion de **risque résiduel** doit apparaître dans les décisions importantes.

---

# Priorisation

Les ressources du laboratoire étant limitées, les efforts doivent être concentrés en priorité sur :

1. les actifs critiques ;
2. les systèmes fortement exposés ;
3. les comptes privilégiés ;
4. les composants dont la compromission peut se propager ;
5. les mécanismes de sécurité dont la défaillance serait silencieuse.
