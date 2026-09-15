### `docs/07-Maintenance/01-Principes-de-maintenance.md`

# 01 - Principes de maintenance

| Élément                           | Valeur                                                        |
| --------------------------------- | ------------------------------------------------------------- |
| **Nom du document**               | `01-Principes-de-maintenance.md`                              |
| **Technologie**                   | Maintenance                                                   |
| **Catégorie**                     | Maintenance                                                   |
| **Objectif**                      | Définir les principes généraux de maintenance du laboratoire. |
| **Auteur**                        | Sébastien Allely                                              |
| **Version**                       | 1.0                                                           |
| **Date de dernière modification** | 05/08/2026                                                    |

---

## 1. Principe général

Une modification du laboratoire doit être considérée comme un changement susceptible d'avoir des conséquences sur :

* la sécurité ;
* la disponibilité ;
* la supervision ;
* les sauvegardes ;
* la documentation ;
* les dépendances.

---

## 2. Avant modification

Avant une modification importante :

* identifier l'objectif ;
* identifier les composants concernés ;
* identifier les dépendances ;
* vérifier les sauvegardes ;
* déterminer le moyen de retour arrière lorsque nécessaire.

---

## 3. Pendant la modification

La modification doit être réalisée de manière contrôlée.

Il faut notamment :

* limiter le périmètre ;
* conserver les informations utiles ;
* vérifier les résultats intermédiaires ;
* éviter les modifications simultanées non nécessaires.

---

## 4. Après modification

Vérifier :

* fonctionnement ;
* sécurité ;
* supervision ;
* sauvegarde ;
* documentation.

---

## 5. Traçabilité

Les modifications importantes doivent pouvoir être expliquées a posteriori.

Le dépôt Git constitue notamment un mécanisme de traçabilité des modifications documentaires et des éléments versionnés.
