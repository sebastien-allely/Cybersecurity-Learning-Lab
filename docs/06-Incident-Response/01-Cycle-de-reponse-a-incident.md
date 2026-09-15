### `docs/06-Incident-Response/01-Cycle-de-reponse-a-incident.md`

# 01 - Cycle de réponse à incident

| Élément                           | Valeur                                                                    |
| --------------------------------- | ------------------------------------------------------------------------- |
| **Nom du document**               | `01-Cycle-de-reponse-a-incident.md`                                       |
| **Technologie**                   | Incident Response                                                         |
| **Catégorie**                     | Incident Response                                                         |
| **Objectif**                      | Présenter le cycle général utilisé pour traiter un événement de sécurité. |
| **Auteur**                        | Sébastien Allely                                                          |
| **Version**                       | 1.0                                                                       |
| **Date de dernière modification** | 05/08/2026                                                                |

---

## 1. Cycle général

Le laboratoire utilise une approche structurée :

```text
Préparation
   ↓
Détection
   ↓
Qualification
   ↓
Investigation
   ↓
Confinement
   ↓
Remédiation
   ↓
Restauration
   ↓
Validation
   ↓
Retour d'expérience
```

---

## 2. Préparation

La préparation consiste notamment à disposer :

* d'une infrastructure documentée ;
* d'une supervision fonctionnelle ;
* de journaux exploitables ;
* de sauvegardes ;
* de mécanismes de protection ;
* de procédures de diagnostic.

---

## 3. Détection

La détection peut provenir :

* d'une alerte Zabbix ;
* de CrowdSec ;
* de Fail2ban ;
* d'un antivirus ;
* d'AIDE ;
* d'une observation manuelle ;
* d'un exercice.

---

## 4. Qualification

L'événement doit être caractérisé avant toute action importante.

Il faut notamment déterminer :

* quel actif est concerné ;
* quel service est concerné ;
* quel événement a été observé ;
* quand il s'est produit ;
* quelles sources permettent de le confirmer ;
* quel impact potentiel existe.

---

## 5. Investigation

L'investigation vise à comprendre les faits à partir des éléments disponibles.

Elle doit privilégier les observations vérifiables plutôt que les hypothèses.

---

## 6. Confinement et remédiation

Le confinement vise à limiter la propagation ou l'impact.

La remédiation vise ensuite à supprimer ou corriger la cause identifiée.

---

## 7. Restauration

Le service est restauré dans un état maîtrisé.

Une sauvegarde ou un mécanisme de récupération peut être utilisé lorsque cela est nécessaire.

---

## 8. Retour d'expérience

Chaque incident ou exercice significatif doit permettre d'identifier :

* ce qui a fonctionné ;
* ce qui n'a pas fonctionné ;
* ce qui n'a pas été détecté ;
* ce qui doit être amélioré ;
* les éventuelles modifications à apporter au laboratoire.
