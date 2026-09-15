# 02 - Rôle dans le laboratoire


| Élément | Valeur |
| **Nom du document** | `02-Role-dans-le-laboratoire.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Rôle de socle

Debian constitue un système d'exploitation de référence du laboratoire.

Il fournit notamment le socle nécessaire à certains composants d'infrastructure.

Le cas le plus important est Proxmox VE, dont les nœuds reposent sur Debian.

---

## Proxmox VE

L'architecture peut être représentée ainsi :

```text
Matériel
   │
   ▼
Debian
   │
   ▼
Proxmox VE
   │
   ▼
Machines virtuelles
```

Debian est donc une dépendance directe de la plateforme de virtualisation.

Une défaillance importante du socle peut avoir un impact sur les services hébergés par Proxmox.

---

## Zabbix

Le serveur de supervision Zabbix du laboratoire utilise également Debian.

```text
Debian
   │
   ▼
ZABBIX01
   │
   ▼
Supervision
```

Debian constitue ainsi le socle du système de supervision.

---

## Positionnement par rapport à Ubuntu

Le laboratoire utilise également Ubuntu pour certains services.

Debian et Ubuntu sont donc deux références distinctes.

Cette distinction permet de documenter les différences de configuration et de sécurité propres à chaque distribution.

---

## Criticité

La criticité dépend du rôle assuré par le système Debian.

Un Debian servant de socle à Proxmox possède une criticité particulièrement élevée, car plusieurs machines virtuelles peuvent dépendre indirectement de celui-ci.

---

## Références

* Documentation Debian
* Documentation Proxmox VE
* Référentiel Architecture du laboratoire
* Référentiel Zabbix
