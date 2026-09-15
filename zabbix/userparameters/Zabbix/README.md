# README.md


| Élément                           | Valeur                                                                                                             |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `README.md`                                                                                                     |
| **Technologie**                   | Zabbix                                                                                                 |
| **Catégorie**                     | UserParameters                                                                                               |
| **Objectif**                      | Documenter les UserParameter spécifiques à la machine hébergeant le serveur Zabbix du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                   |
| **Version**                       | 1.0                                                                                                                |
| **Date de dernière modification** | 07/08/2026                                                                                                         |

-------------------------------------------------------------

# UserParameter — Zabbix

## 1. Rôle

Ce répertoire contient les fichiers de configuration **Zabbix Agent 2** utilisés sur la machine qui héberge le serveur Zabbix du laboratoire.

Les fichiers présents ici ne constituent pas une configuration générique de Zabbix Agent 2. Ils correspondent aux besoins de supervision définis pour cette machine dans le laboratoire.

Le dépôt utilise exclusivement **Zabbix Agent 2**.

> Les anciens fichiers ou configurations relatifs à `zabbix-agent` / `zabbix_agentd` ne font pas partie du laboratoire et ne doivent pas être reproduits.

## 2. Installation

Les fichiers `.conf` doivent être copiés dans :

```text
/etc/zabbix/zabbix_agent2.d/
```

Exemple :

```bash
sudo cp <fichier>.conf /etc/zabbix/zabbix_agent2.d/
```

Après modification de la configuration :

```bash
sudo systemctl restart zabbix-agent2
```

Puis vérifier le service :

```bash
sudo systemctl status zabbix-agent2
```

## 3. Correspondance avec le dépôt

Les fichiers présents dans ce répertoire sont associés à la **VM Zabbix**.

Ils doivent être distingués des UserParameter destinés aux nœuds Proxmox.

| Répertoire du dépôt        | Machine cible                 |
| -------------------------- | ----------------------------- |
| `userparameters/Proxmox/`  | Nœuds Proxmox                 |
| `userparameters/Zabbix/`   | VM Zabbix                     |
| `userparameters/CrowdSec/` | Configuration liée à CrowdSec |

Cette organisation permet de ne pas confondre un fichier portant un nom identique avec une configuration destinée à une autre machine.

## 4. Configuration associée

La configuration globale de l'Agent 2 est définie dans :

```text
/etc/zabbix/zabbix_agent2.conf
```

Les UserParameter sont chargés depuis les fichiers présents dans :

```text
/etc/zabbix/zabbix_agent2.d/
```

Les éléments de supervision correspondants sont documentés dans :

* [`docs/05-Monitoring/`](../../../../docs/05-Monitoring/)
* [`zabbix/templates/`](../../templates/)

## 5. Principe de sécurité

Les UserParameter permettent à Zabbix Agent 2 d'exécuter des commandes locales afin de retourner des métriques au serveur Zabbix.

Ils doivent donc être considérés comme des éléments sensibles de la configuration.

Toute commande ajoutée doit être :

* nécessaire à une supervision identifiée ;
* explicitement documentée ;
* limitée au strict nécessaire ;
* vérifiée avant son déploiement ;
* compatible avec le principe du moindre privilège.

Il ne faut pas activer `UnsafeUserParameters` sans nécessité démontrée.

## 6. Validation

Après installation ou modification, vérifier que l'Agent 2 accepte sa configuration :

```bash
sudo zabbix_agent2 -t <clé>
```

Puis vérifier le fonctionnement du service :

```bash
sudo systemctl status zabbix-agent2
```

Les clés utilisées doivent également être cohérentes avec les éléments configurés dans les templates Zabbix du laboratoire.
