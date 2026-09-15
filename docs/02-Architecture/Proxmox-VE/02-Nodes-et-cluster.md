# 02 - Nœuds et cluster


| Élément | Valeur |
| **Nom du document** | `02-Nodes-et-cluster.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Décrire les nœuds Proxmox VE et l'organisation du cluster. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


Machines virtuelles principales :

* `AD01`
* `SRV-WIN`
* `GLPI01`

---

## Cluster et quorum

Le quorum permet au cluster de déterminer s'il dispose d'un nombre suffisant de membres pour fonctionner de manière cohérente.

La vérification de l'état du cluster peut être réalisée avec :

```bash
pvecm status
```

La liste des nœuds peut être obtenue avec :

```bash
pvecm nodes
```

---

## Répartition actuelle

```text
PVE1
 ├── ZABBIX01

PVE2
 ├── AD01
 ├── SRV-WIN
 └── GLPI01
```

Cette répartition permet de distribuer les charges entre les deux nœuds.

---

## Dépendance

Le fonctionnement du cluster dépend notamment :

* de la disponibilité des nœuds ;
* du réseau ;
* de la synchronisation des informations du cluster ;
* des ressources matérielles ;
* du stockage ;
* des services Proxmox.

Avec seulement deux nœuds, la perte d'un nœud doit être considérée comme un événement significatif pour la disponibilité du cluster.

---

## Architecture cible

L'ajout d'un troisième nœud pourrait être étudié afin d'améliorer certains aspects liés au quorum et à la résilience.

Cette évolution n'est toutefois pas considérée comme déployée dans le laboratoire.

Elle devra être évaluée selon :

* les besoins ;
* les ressources disponibles ;
* la complexité ;
* le bénéfice réel pour le laboratoire.

---

## Références

* Documentation officielle Proxmox VE
* Documentation du cluster Proxmox VE
* Documentation Debian
