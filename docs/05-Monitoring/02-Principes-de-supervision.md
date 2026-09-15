### `docs/05-Monitoring/02-Principes-de-supervision.md`

# 02 - Principes de supervision

| Élément                           | Valeur                                                                                    |
| --------------------------------- | ----------------------------------------------------------------------------------------- |
| **Nom du document**               | `02-Principes-de-supervision.md`                                                          |
| **Technologie**                   | Zabbix                                                                                    |
| **Catégorie**                     | Monitoring                                                                                |
| **Objectif**                      | Définir les principes permettant de construire une supervision pertinente et exploitable. |
| **Auteur**                        | Sébastien Allely                                                                          |
| **Version**                       | 1.0                                                                                       |
| **Date de dernière modification** | 05/08/2026                                                                                |

---

## 1. Superviser pour agir

Une donnée de supervision doit avoir une finalité.

Avant de créer un item, une question doit pouvoir être formulée :

> Quelle décision ou quelle action cette information permet-elle de prendre ?

La collecte de métriques sans objectif opérationnel doit être évitée.

---

## 2. Disponibilité

La disponibilité permet notamment de vérifier :

* qu'un hôte répond ;
* qu'un agent fonctionne ;
* qu'un service critique est disponible ;
* qu'une fonction importante reste accessible.

Une indisponibilité doit être associée à son impact.

---

## 3. Performance

Les ressources importantes peuvent être supervisées notamment :

* CPU ;
* mémoire ;
* stockage ;
* espace disque ;
* charge système ;
* réseau.

Les seuils doivent être adaptés au rôle du système.

Un seuil technique ne constitue pas nécessairement une alerte de sécurité.

---

## 4. Sécurité

Certains événements techniques peuvent avoir une dimension de sécurité.

Exemples :

* arrêt d'un mécanisme de protection ;
* modification inattendue d'un état ;
* augmentation anormale d'événements ;
* indisponibilité d'une fonction de sécurité ;
* échec répété d'une opération importante.

La supervision ne doit toutefois pas transformer chaque événement en incident de sécurité.

---

## 5. Qualité des alertes

Une alerte doit être :

* compréhensible ;
* contextualisée ;
* associée à une sévérité ;
* exploitable ;
* testable.

Une alerte générant systématiquement des faux positifs perd rapidement sa valeur opérationnelle.

---

## 6. Sévérité

La sévérité doit refléter l'importance de la situation et non simplement la gravité technique du symptôme.

Elle doit prendre en compte notamment :

* la criticité de l'actif ;
* l'impact ;
* la durée ;
* le caractère isolé ou généralisé ;
* les dépendances ;
* les conséquences potentielles.

---

## 7. Supervision de la supervision

Le fonctionnement de Zabbix lui-même doit être contrôlé.

Il faut notamment pouvoir identifier :

* une absence de données ;
* un problème d'agent ;
* un problème de collecte ;
* un problème affectant le serveur de supervision.

Une supervision indisponible constitue elle-même un risque opérationnel.

---

## 8. Évolution

Les items, triggers et tableaux de bord doivent être réévalués lorsque :

* l'architecture évolue ;
* un service est ajouté ou supprimé ;
* un risque évolue ;
* un seuil devient inadapté ;
* une alerte n'est plus pertinente ;
* une nouvelle capacité de détection est introduite.

La supervision fait donc partie du cycle de maintenance du laboratoire.
