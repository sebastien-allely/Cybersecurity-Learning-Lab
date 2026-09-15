### `docs/07-Maintenance/05-Maintenance-des-mecanismes-de-securite.md`

# 05 - Maintenance des mécanismes de sécurité

| Élément                           | Valeur                                                               |
| --------------------------------- | -------------------------------------------------------------------- |
| **Nom du document**               | `05-Maintenance-des-mecanismes-de-securite.md`                       |
| **Technologie**                   | Sécurité                                                             |
| **Catégorie**                     | Maintenance                                                          |
| **Objectif**                      | Maintenir opérationnels les mécanismes de protection du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                     |
| **Version**                       | 1.0                                                                  |
| **Date de dernière modification** | 05/08/2026                                                           |

---

## 1. Mécanismes concernés

La maintenance concerne notamment les mécanismes documentés dans le laboratoire :

* Fail2ban ;
* CrowdSec ;
* ClamAV ;
* AIDE ;
* mécanismes de durcissement ;
* contrôle des accès ;
* supervision associée.

---

## 2. Vérification

Pour chaque mécanisme, vérifier notamment :

* service ;
* configuration ;
* journaux ;
* fonctionnement ;
* supervision ;
* mises à jour ;
* capacité de récupération.

---

## 3. Principe de supervision

Un mécanisme de sécurité qui n'est pas opérationnel doit être détecté.

La supervision constitue donc une partie intégrante de la maintenance de la sécurité.

---

## 4. Évolution

Toute modification importante d'un mécanisme doit être évaluée selon :

* le risque couvert ;
* les effets secondaires ;
* la supervision ;
* les procédures existantes ;
* la documentation.
