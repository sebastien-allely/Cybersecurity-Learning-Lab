### `docs/06-Incident-Response/05-Confinement-et-remediation.md`

# 05 - Confinement et remédiation

| Élément                           | Valeur                                                                            |
| --------------------------------- | --------------------------------------------------------------------------------- |
| **Nom du document**               | `05-Confinement-et-remediation.md`                                                |
| **Technologie**                   | Incident Response                                                                 |
| **Catégorie**                     | Incident Response                                                                 |
| **Objectif**                      | Présenter les principes de limitation de l'impact et de correction d'un incident. |
| **Auteur**                        | Sébastien Allely                                                                  |
| **Version**                       | 1.0                                                                               |
| **Date de dernière modification** | 05/08/2026                                                                        |

---

## 1. Confinement

Le confinement cherche à limiter l'impact d'un événement.

Selon le scénario, il peut notamment consister à :

* bloquer une source ;
* arrêter un service compromis ;
* isoler un système ;
* désactiver temporairement un accès ;
* limiter une communication.

Toute action de confinement doit prendre en compte ses conséquences sur les services légitimes.

---

## 2. Remédiation

La remédiation cherche à supprimer ou corriger la cause de l'événement.

Elle peut notamment comprendre :

* correction de configuration ;
* suppression d'un élément malveillant ;
* mise à jour ;
* changement d'identifiants compromis ;
* restauration d'une configuration connue ;
* renforcement d'une mesure de sécurité.

---

## 3. Validation

Après remédiation, il faut vérifier :

* que la cause a été traitée ;
* que le service fonctionne ;
* que la protection est opérationnelle ;
* que l'événement ne se reproduit pas ;
* que les systèmes dépendants fonctionnent correctement.

---

## 4. Principe

Une action corrective ne doit pas être considérée comme terminée simplement parce que l'alerte a disparu.

La situation doit être vérifiée à plusieurs niveaux :

```text
Incident
   ↓
Action corrective
   ↓
Service
   ↓
Protection
   ↓
Supervision
   ↓
Retour à l'état nominal
```
