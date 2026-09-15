# README — UserParameters Proxmox

| Élément                           | Valeur                                                                                                   |
| --------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                              |
| **Technologie**                   | Zabbix Agent 2 / Proxmox VE                                                                              |
| **Catégorie**                     | Supervision / UserParameters                                                                             |
| **Objectif**                      | Documenter les UserParameters déployés sur les nœuds Proxmox et expliquer leur destination et leur rôle. |
| **Auteur**                        | Sébastien Allely                                                                                         |
| **Version**                       | 1.0                                                                                                      |
| **Date de dernière modification** | 08/08/2026                                                                                               |

---

## 1. Objectif

Ce répertoire contient les fichiers de configuration `UserParameter` utilisés par **Zabbix Agent 2 sur les nœuds Proxmox VE** du laboratoire.

Les fichiers présents ici ne constituent pas une configuration générique applicable à toutes les machines Linux.

Ils correspondent aux besoins de supervision définis pour les hyperviseurs Proxmox du **Cybersecurity-Learning-Lab**.

---

## 2. Destination

Les fichiers doivent être déployés dans :

```text
/etc/zabbix/zabbix_agent2.d/
```

sur chaque nœud Proxmox concerné.

La configuration est chargée par **Zabbix Agent 2**.

Le laboratoire utilise Zabbix Agent 2 et non l'ancien Zabbix Agent.

---

## 3. Fichiers

### `proxmox.conf`

Contient les `UserParameter` permettant de superviser des éléments spécifiques à Proxmox VE, notamment :

* l'état du cluster ;
* le quorum ;
* le nombre de nœuds ;
* les votes ;
* l'état des services Proxmox ;
* l'utilisation de certains stockages ;
* l'état ZFS lorsqu'il est présent ;
* certains éléments LVM ;
* l'état du bond réseau.

Ce fichier est spécifique aux **nœuds Proxmox**.

---


### `nvme.conf`

Contient les `UserParameter` permettant de superviser l'état du stockage NVMe physique du nœud.

Les informations collectées concernent notamment :

* la température ;
* le pourcentage d'usure ;
* les erreurs d'intégrité des données ;
* les avertissements critiques ;
* l'état SMART.

Ce fichier concerne le **matériel physique du nœud Proxmox**.

Il ne concerne pas le disque virtuel d'une machine virtuelle.

---

### `crowdsec.conf`

Contient les `UserParameter` utilisés pour intégrer certains indicateurs CrowdSec dans la supervision Zabbix.

La configuration permet notamment de contrôler :

* l'état de la LAPI CrowdSec ;
* les métriques CrowdSec exposées sous forme JSON.

Ce fichier est présent sur les systèmes Proxmox sur lesquels CrowdSec est installé et supervisé.

---

## 4. Relation avec les templates Zabbix

Les `UserParameter` présents dans ce répertoire constituent la partie **agent** de la supervision.

Ils sont utilisés par les éléments Zabbix définis dans les templates correspondants.

Les fichiers de templates sont disponibles dans :

```text
../../templates/
```

Les éléments de supervision associés doivent être documentés et versionnés avec les autres composants Zabbix du dépôt.

---

## 5. Sécurité

Les `UserParameter` exécutent des commandes locales avec les privilèges de l'utilisateur `zabbix`.

Lorsque l'accès à une commande privilégiée est nécessaire, celui-ci doit être explicitement contrôlé par la configuration `sudoers`.

Les commandes utilisées doivent rester :

* limitées au besoin de supervision ;
* déterministes ;
* non interactives ;
* dépourvues de mécanismes permettant à l'utilisateur `zabbix` d'exécuter arbitrairement des commandes privilégiées.

Les droits sudo associés ne doivent pas être élargis sans justification.

---

## 6. Installation

Après déploiement ou modification d'un fichier, vérifier la configuration de l'Agent 2 puis redémarrer le service si nécessaire.

Exemple :

```bash
sudo zabbix_agent2 -t <cle>
```

Puis :

```bash
sudo systemctl restart zabbix-agent2
```

L'état du service peut être contrôlé avec :

```bash
sudo systemctl status zabbix-agent2
```

---

## 7. Principe de séparation

Les fichiers présents dans ce répertoire ne doivent pas être copiés automatiquement vers la VM Zabbix.

La VM Zabbix possède sa propre configuration dans :

```text
../Zabbix/
```

Cette séparation permet notamment d'éviter de confondre :

* les métriques du serveur Zabbix ;
* les métriques des hyperviseurs Proxmox ;
* les métriques du stockage physique des nœuds ;
* les mécanismes de sauvegarde Proxmox.

---

## 8. Correspondance avec l'infrastructure

| Fichier         | Cible                                    |
| --------------- | ---------------------------------------- |
| `proxmox.conf`  | Nœuds Proxmox                            |
| `nvme.conf`     | Stockage NVMe physique des nœuds Proxmox |
| `crowdsec.conf` | Nœuds Proxmox équipés de CrowdSec        |

La présence d'un fichier dans ce répertoire ne signifie donc pas qu'il doit être installé sur une machine virtuelle hébergée par Proxmox.
