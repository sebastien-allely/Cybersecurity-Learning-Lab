### `docs/07-Maintenance/03-Sauvegardes-et-restauration.md`

# 03 - Sauvegardes et restauration

| Élément                           | Valeur                                                                                 |
| --------------------------------- | -------------------------------------------------------------------------------------- |
| **Nom du document**               | `03-Sauvegardes-et-restauration.md`                                                    |
| **Technologie**                   | Maintenance                                                                            |
| **Catégorie**                     | Maintenance                                                                            |
| **Objectif**                      | Décrire le rôle des sauvegardes dans la maintenance et la récupération du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                       |
| **Version**                       | 1.0                                                                                    |
| **Date de dernière modification** | 05/08/2026                                                                             |

---

## 1. Objectif

Les sauvegardes permettent de récupérer un système après :

* erreur de configuration ;
* défaillance ;
* expérimentation ;
* corruption ;
* incident ;
* perte de données.

---

## 2. Principe

Une sauvegarde n'est utile que si elle peut être restaurée.

La stratégie doit donc associer :

```text
Sauvegarde
   +
Vérification
   +
Restauration testée
```

---

## 3. Proxmox VE

Les sauvegardes des machines virtuelles constituent un élément important de la résilience du laboratoire.

La stratégie détaillée est documentée dans la documentation Proxmox VE.

---

## 4. Restauration

Une restauration doit être suivie de contrôles :

* démarrage ;
* système ;
* réseau ;
* services ;
* sécurité ;
* supervision ;
* cohérence des données.

---

## 5. Limites

Une sauvegarde ne protège pas à elle seule contre une compromission.

Elle doit être considérée comme un mécanisme de récupération et non comme un mécanisme de prévention.
