### `docs/07-Maintenance/06-Maintenance-de-la-supervision.md`

# 06 - Maintenance de la supervision

| Élément                           | Valeur                                                     |
| --------------------------------- | ---------------------------------------------------------- |
| **Nom du document**               | `06-Maintenance-de-la-supervision.md`                      |
| **Technologie**                   | Zabbix                                                     |
| **Catégorie**                     | Maintenance                                                |
| **Objectif**                      | Maintenir la pertinence et la fiabilité de la supervision. |
| **Auteur**                        | Sébastien Allely                                           |
| **Version**                       | 1.0                                                        |
| **Date de dernière modification** | 05/08/2026                                                 |

---

## 1. Objectif

La supervision évolue avec l'infrastructure.

Lorsqu'un composant est ajouté, modifié ou supprimé, les éléments de supervision associés doivent être réévalués.

---

## 2. Vérifications

Il faut notamment contrôler :

* agents ;
* templates ;
* items ;
* triggers ;
* dépendances ;
* UserParameters ;
* tableaux de bord ;
* seuils ;
* alertes.

---

## 3. Suppression

Les éléments de supervision devenus inutiles doivent être supprimés.

Une supervision obsolète peut générer du bruit et réduire la qualité des alertes.

---

## 4. Cohérence

Les configurations versionnées dans :

```text
zabbix/
```

doivent rester cohérentes avec la supervision réellement utilisée.

---

## 5. Validation

Après modification :

* vérifier la collecte ;
* tester les conditions d'alerte ;
* vérifier la récupération ;
* contrôler les tableaux de bord ;
* vérifier l'absence d'alertes parasites.
