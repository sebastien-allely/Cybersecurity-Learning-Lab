### `docs/05-Monitoring/03-Elements-supervises.md`

# 03 - Éléments supervisés

| Élément                           | Valeur                                                                           |
| --------------------------------- | -------------------------------------------------------------------------------- |
| **Nom du document**               | `03-Elements-supervises.md`                                                      |
| **Technologie**                   | Zabbix                                                                           |
| **Catégorie**                     | Monitoring                                                                       |
| **Objectif**                      | Identifier les principales catégories d'éléments supervisés dans le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                 |
| **Version**                       | 1.0                                                                              |
| **Date de dernière modification** | 05/08/2026                                                                       |

---

## 1. Systèmes

La supervision couvre les systèmes participant au fonctionnement du laboratoire.

Elle peut notamment porter sur :

* les machines Linux ;
* les machines Windows ;
* les nœuds Proxmox VE ;
* les machines virtuelles.

---

## 2. Services

Les services importants peuvent être supervisés afin de vérifier leur disponibilité.

Selon les composants, cela peut concerner notamment :

* Active Directory ;
* DNS ;
* Apache ;
* MariaDB ;
* GLPI ;
* Zabbix ;
* CrowdSec ;
* Fail2ban ;
* ClamAV.

---

## 3. Ressources

Les ressources système constituent une autre catégorie de supervision :

* CPU ;
* mémoire ;
* stockage ;
* espace disque ;
* réseau ;
* charge système.

---

## 4. Sécurité

Certains mécanismes de sécurité font l'objet d'une supervision spécifique.

La finalité est de détecter notamment :

* un arrêt ;
* une indisponibilité ;
* une anomalie ;
* une dégradation ;
* un événement nécessitant une vérification.

---

## 5. Infrastructure Proxmox

Les éléments importants de l'infrastructure de virtualisation peuvent notamment être supervisés :

* nœuds ;
* ressources ;
* machines virtuelles ;
* stockage ;
* sauvegardes ;
* états critiques.

La documentation spécifique à Proxmox VE reste située dans :

```text
docs/02-Architecture/Proxmox-VE/
```

---

## 6. Cohérence

La liste réelle des éléments supervisés doit rester cohérente avec les éléments présents dans le laboratoire.

Ce document décrit les catégories.

La configuration effective est conservée dans :

```text
zabbix/
```
