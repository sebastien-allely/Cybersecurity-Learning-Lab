# 07 - Supervision ZABBIX


| Élément | Valeur |
| **Nom du document** | `07-Supervision-Zabbix.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Architecture |
| **Objectif** | Décrire la supervision des composants Proxmox VE par Zabbix. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Objectif

La supervision fournit une visibilité opérationnelle sur l'état des nœuds Proxmox et des ressources utilisées par les machines virtuelles.

Le laboratoire utilise ZABBIX01 comme solution de supervision centralisée.

---

## Architecture

```text
                 ZABBIX01 Server
                      │
                      │
               ZABBIX01 Agent 2
                      │
             ┌────────┴────────┐
             │                 │
        PVE1           PVE2
             │                 │
          Proxmox            Proxmox
             │                 │
          VM / infra       VM / infra
```

---

## Agent ZABBIX01

Les nœuds concernés utilisent **ZABBIX01 Agent 2**.

Les configurations complémentaires sont notamment stockées dans :

```text
/etc/zabbix/zabbix_agent2.d/
```

---

## Modèle de supervision

Les contrôles spécifiques à Proxmox sont regroupés dans le modèle :

```text
Supervision Proxmox
```

Il permet notamment de surveiller :

* les nœuds ;
* le cluster ;
* le quorum ;
* les ressources ;
* les stockages ;
* les sauvegardes.

---

## Ressources surveillées

Les principales ressources comprennent :

* CPU ;
* mémoire ;
* stockage ;
* réseau ;
* disponibilité des services ;
* état des VM ;
* état du cluster ;
* sauvegardes.

---

## Sauvegardes

La supervision des sauvegardes est particulièrement importante.

Un hyperviseur peut fonctionner normalement tout en présentant une dégradation critique de sa capacité de restauration si les sauvegardes échouent.

---

## Rôle de ZABBIX01

ZABBIX01 permet principalement :

1. de détecter une anomalie ;
2. de générer une alerte ;
3. de conserver des données historiques ;
4. d'aider au diagnostic ;
5. de vérifier le retour à un état normal.

ZABBIX01 ne remplace ni les journaux système ni les outils d'investigation.

---

## Criticité

ZABBIX01 possède une criticité importante car il fournit la visibilité nécessaire au suivi de l'infrastructure.

Une indisponibilité de ZABBIX01 ne signifie pas nécessairement que Proxmox est indisponible.

Elle signifie en revanche que la capacité de détection et d'alerte est dégradée.

---

## Références

* Documentation officielle ZABBIX01
* Référentiel ZABBIX01 du laboratoire
* Référentiel Proxmox
