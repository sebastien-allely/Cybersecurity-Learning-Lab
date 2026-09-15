# 06 - Sauvegardes


| Élément | Valeur |
| **Nom du document** | `06-Sauvegardes.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Décrire la stratégie de sauvegarde des machines virtuelles Proxmox VE. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Machines sauvegardées

Les principales VM critiques actuellement concernées sont notamment :

* `AD01` ;
* `ZABBIX01` ;
* `GLPI01`.


---

## Objectifs

La sauvegarde doit permettre de restaurer les services après :

* panne ;
* corruption ;
* erreur humaine ;
* suppression accidentelle ;
* problème logiciel ;
* mise à jour problématique ;
* incident de sécurité.

---

## Restauration

La présence d'une sauvegarde ne garantit pas à elle seule la capacité de restauration.

Les procédures de restauration doivent donc être testées périodiquement.

Les résultats des tests doivent être documentés.

---

## Limites actuelles

Le stockage des sauvegardes repose actuellement sur la box internet.

Cette architecture ne constitue pas une séparation physique complète entre les services réseau et le stockage de sauvegarde.

Elle doit donc être considérée comme une limite de l'architecture actuelle.

---

## Architecture cible

Une solution de sauvegarde dédiée pourra être étudiée.

Proxmox Backup Server constitue notamment une possibilité.

L'objectif serait d'améliorer :

* l'isolation ;
* l'intégrité ;
* la gestion des rétentions ;
* les capacités de restauration ;
* la résilience.

---

## Références

* Documentation officielle Proxmox VE
* Documentation des scripts de sauvegarde du laboratoire
* Référentiel Maintenance du laboratoire
* Référentiel Sauvegardes du laboratoire
