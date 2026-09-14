# 09 - Sauvegardes


| Élément | Valeur |
| **Nom du document** | `09-Sauvegardes.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Principe

Une sauvegarde Debian doit permettre de reconstruire le système ou de restaurer les données nécessaires à son fonctionnement.

Les éléments à considérer dépendent du rôle du serveur.

---

## Fichiers de configuration

Les fichiers de configuration critiques se trouvent principalement sous :

```text
/etc/
```

Ils doivent être protégés et sauvegardés lorsqu'ils sont nécessaires à la reconstruction du service.

---

## Données

Les données applicatives peuvent notamment se trouver dans :

```text
/var/
```

ou dans un emplacement spécifique au service.

La stratégie doit être adaptée à chaque application.

---

## Proxmox

Pour les systèmes Debian hébergés comme VM, la sauvegarde de la VM fournit un niveau de protection supplémentaire.

Elle ne remplace cependant pas nécessairement une sauvegarde logique des données applicatives.

---

## Restauration

Une sauvegarde n'est réellement utile que si sa restauration est possible.

Les tests doivent notamment vérifier :

* l'existence de la sauvegarde ;
* son intégrité ;
* la capacité à restaurer ;
* la cohérence de la configuration ;
* le redémarrage du service.

---

## Références

* Documentation Debian
* Référentiel Sauvegardes du laboratoire
* Debian Administrator's Handbook
