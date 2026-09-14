# 02 - Identification des actifs

| Élément | Valeur |
| **Nom du document** | `02-Identification-des-actifs.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les actifs protégés par Fail2ban ainsi que les composants nécessaires à son fonctionnement. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Actifs concernés

Fail2ban peut être déployé sur les systèmes Linux du laboratoire lorsqu'un service dispose de journaux exploitables et qu'une réaction automatique est pertinente.

Les systèmes concernés par les travaux du laboratoire comprennent notamment :

* `PVE1` ;
* `PVE2` ;
* `ZABBIX01` ;
* `GLPI01` ;
* `AD01`, lorsque le système et les services concernés le permettent.

L'activation effective d'une jail doit toutefois être déterminée en fonction des services réellement présents sur chaque actif.

---

# Composants

Le fonctionnement repose principalement sur :

* Fail2ban ;
* les jails ;
* les filtres ;
* les fichiers de configuration ;
* les journaux analysés ;
* les actions de bannissement.

---

# Jails

Une jail associe notamment :

* une source de journalisation ;
* un filtre ;
* un seuil ;
* une période d'observation ;
* une durée de bannissement ;
* une action.

Cette structure permet d'adapter la protection au service concerné.

---

# Filtres personnalisés

Le laboratoire utilise également des **filtres personnalisés** lorsque les filtres standards ne répondent pas suffisamment au besoin.

Les travaux associés sont documentés dans :

```text
docs/04-Protection/Fail2ban/07-Creation-filtres-personnalises.md
```

---

# Supervision

Le fonctionnement de Fail2ban est également intégré à la supervision du laboratoire.

Zabbix permet notamment de surveiller l'état du service et les éléments retenus dans la stratégie de supervision.

La protection ne doit donc pas être considérée comme fiable uniquement parce que le paquet est installé.
