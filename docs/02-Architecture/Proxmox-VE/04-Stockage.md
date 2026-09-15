# 04 - Stockage


| Élément | Valeur |
| **Nom du document** | `04-Stockage.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Décrire l'organisation du stockage utilisé par Proxmox VE et les dépendances associées. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


Une saturation ou une indisponibilité du stockage peut affecter directement le fonctionnement des VM.

---

## Sauvegardes

Le stockage de sauvegarde constitue une dépendance importante.

Une sauvegarde présente peu de valeur opérationnelle si son stockage devient indisponible au moment où une restauration est nécessaire.

---

## Limites actuelles

Le stockage des sauvegardes dépend actuellement de la box internet.

Cette architecture présente une dépendance commune entre :

* réseau ;
* stockage ;
* sauvegarde.

Cette dépendance doit être prise en compte dans l'analyse de résilience.

---

## Architecture cible

Une évolution vers un stockage de sauvegarde dédié pourra être étudiée.

Une solution telle que Proxmox Backup Server pourrait notamment permettre d'améliorer :

* l'isolation ;
* la gestion ;
* l'intégrité ;
* la rétention ;
* les capacités de restauration.

Cette solution n'est pas considérée comme déployée dans l'architecture actuelle.

---

## Références

* Documentation officielle Proxmox VE
* Documentation SMB/CIFS
* Référentiel Sauvegardes du laboratoire
