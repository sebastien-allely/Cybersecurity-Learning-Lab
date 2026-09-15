### `docs/05-Monitoring/04-Severite-et-alertes.md`

# 04 - Sévérité et alertes

| Élément                           | Valeur                                                                       |
| --------------------------------- | ---------------------------------------------------------------------------- |
| **Nom du document**               | `04-Severite-et-alertes.md`                                                  |
| **Technologie**                   | Zabbix                                                                       |
| **Catégorie**                     | Monitoring                                                                   |
| **Objectif**                      | Définir les principes utilisés pour qualifier les événements de supervision. |
| **Auteur**                        | Sébastien Allely                                                             |
| **Version**                       | 1.0                                                                          |
| **Date de dernière modification** | 05/08/2026                                                                   |

---

## 1. Objectif

Les alertes doivent permettre de distinguer les situations nécessitant une intervention des simples informations techniques.

La sévérité permet de hiérarchiser les événements.

---

## 2. Principes

Une alerte doit être évaluée selon :

* la criticité de l'actif ;
* l'impact ;
* le caractère immédiat ou différé ;
* la possibilité d'exploitation ;
* les dépendances ;
* la capacité de récupération.

---

## 3. Niveaux

Le laboratoire utilise les niveaux de sévérité définis par Zabbix.

Ils doivent être interprétés selon le contexte du laboratoire et non comme une classification universelle.

Une même anomalie technique peut donc avoir une importance différente selon l'actif concerné.

---

## 4. Dépendances

Les triggers peuvent être liés par des dépendances.

L'objectif est notamment d'éviter qu'une cause primaire provoque une avalanche d'alertes secondaires.

Exemple :

```text
Service critique arrêté
        ↓
fonction indisponible
        ↓
plusieurs symptômes
```

L'alerte principale doit être privilégiée lorsque cela est possible.

---

## 5. Alertes de sécurité

Une alerte liée à la sécurité doit rester contextualisée.

Par exemple, l'arrêt d'un service CrowdSec peut constituer une alerte importante car il signifie qu'une mesure de protection n'est plus opérationnelle.

Cependant, l'alerte Zabbix ne constitue pas à elle seule la preuve d'une compromission.

Elle doit conduire à une vérification.

---

## 6. Qualité

Les alertes doivent être régulièrement vérifiées afin de détecter :

* les faux positifs ;
* les seuils trop sensibles ;
* les alertes inutiles ;
* les situations non détectées ;
* les dépendances incorrectes.

---

## 7. Validation

Toute nouvelle alerte doit pouvoir être testée.

Le test doit permettre de vérifier :

1. la condition de déclenchement ;
2. la sévérité ;
3. le message ;
4. la récupération ;
5. les éventuelles dépendances ;
6. la cohérence avec le comportement attendu.
