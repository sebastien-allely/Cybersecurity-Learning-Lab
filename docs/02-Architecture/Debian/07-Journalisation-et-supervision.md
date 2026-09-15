# 07 - Journalisation et supervision


| Élément | Valeur |
| **Nom du document** | `07-Journalisation-et-supervision.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Renforcer la capacité de détection et d'investigation grâce à la journalisation et à la supervision. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Journalisation

Les journaux permettent :

* d'observer le fonctionnement du système ;
* d'identifier les erreurs ;
* de rechercher un événement ;
* de contribuer au diagnostic ;
* de fournir des éléments utiles lors d'une investigation.

---

## systemd-journald

Le journal peut être consulté avec :

```bash
journalctl
```

Exemples :

```bash
journalctl -b
```

```bash
journalctl -p err..alert
```

```bash
journalctl --since "24 hours ago"
```

---

## Journaux applicatifs

Certains services écrivent également dans :

```text
/var/log/
```

L'emplacement dépend du service concerné.

---

## Supervision

Les systèmes Debian du laboratoire peuvent être supervisés par Zabbix.

La supervision peut notamment porter sur :

* disponibilité ;
* CPU ;
* mémoire ;
* stockage ;
* réseau ;
* services ;
* processus ;
* événements.

---

## Rôle de la supervision

La supervision ne remplace pas la journalisation.

Les deux mécanismes répondent à des objectifs complémentaires :

```text
Supervision
    │
    └── Détection / alerte

Journalisation
    │
    └── Observation / diagnostic / investigation
```

---

## Références

* Documentation Debian
* Documentation systemd
* Référentiel Zabbix du laboratoire
* Debian Administrator's Handbook, chapitre Security
