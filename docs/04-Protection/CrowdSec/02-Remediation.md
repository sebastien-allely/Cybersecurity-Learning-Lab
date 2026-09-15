# 02 - Remédiation

| Élément                           | Valeur                                                                      |
| --------------------------------- | --------------------------------------------------------------------------- |
| **Nom du document**               | `02-Remediation.md`                                                         |
| **Technologie**                   | CrowdSec                                                                    |
| **Catégorie**                     | Protection                                                                  |
| **Objectif**                      | Documenter le passage d'une détection CrowdSec à une action de remédiation. |
| **Auteur**                        | Sébastien Allely                                                            |
| **Version**                       | 1.0                                                                         |
| **Date de dernière modification** | 05/08/2026                                                                  |

---

## 1. Principe

CrowdSec sépare volontairement la détection de la remédiation.

Une détection identifie un comportement.

Une décision formalise l'action à appliquer.

Un mécanisme de remédiation applique ensuite cette décision au système concerné.

```text
Comportement
     ↓
Détection
     ↓
Décision
     ↓
Remédiation
```

---

## 2. Intérêt de cette séparation

Cette architecture permet notamment :

* d'isoler la logique de détection ;
* de modifier le mécanisme de blocage sans réécrire les scénarios ;
* de vérifier séparément la détection et la protection ;
* de faciliter le diagnostic ;
* de superviser chaque étape.

---

## 3. Validation de la remédiation

Une remédiation doit être testée séparément de la détection.

L'apprenant doit être capable de démontrer :

```text
Événement généré
      ↓
Détection produite
      ↓
Décision créée
      ↓
Décision consommée
      ↓
Action appliquée
```

Une détection visible sans action de protection ne doit pas être considérée comme une chaîne de protection entièrement fonctionnelle.

---

## 4. Surveillance

La supervision doit permettre de détecter une perte de capacité de protection.

Le laboratoire surveille notamment l'état des composants CrowdSec nécessaires au fonctionnement de la chaîne.

Les décisions elles-mêmes ne constituent pas un élément permanent de supervision du laboratoire : leur existence peut être vérifiée lors des opérations de validation technique et, ultérieurement, dans le cadre d'exercices pédagogiques.

---

## 5. Limites

Une remédiation automatique peut provoquer des blocages légitimes lorsqu'un seuil est mal adapté.

Toute modification doit donc être testée avec :

* des comportements normaux ;
* des comportements simulant une attaque ;
* des scénarios de récupération ;
* une vérification de l'absence d'impact fonctionnel injustifié.
