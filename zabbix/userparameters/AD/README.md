# UserParameters — Active Directory

| Élément                           | Valeur                                                                                                                                                        |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                                                                                   |
| **Technologie**                   | Zabbix Agent 2 / Active Directory                                                                                                                             |
| **Catégorie**                     | Supervision                                                                                                                                                   |
| **Objectif**                      | Documenter les UserParameters spécifiques à la supervision du contrôleur de domaine Active Directory du laboratoire et préciser leur périmètre d'utilisation. |
| **Auteur**                        | Sébastien Allely                                                                                                                                              |
| **Version**                       | 1.0                                                                                                                                                           |
| **Date de dernière modification** | 10/08/2026                                                                                                                                                    |

---

## 1. Rôle du répertoire

Ce répertoire contient les éléments de configuration **Zabbix Agent 2 spécifiques à la cible Active Directory** du laboratoire.

La configuration présentée ici est destinée à un serveur **Windows Server 2019** utilisé comme contrôleur de domaine Active Directory.

Elle ne doit pas être copiée sur :

* les nœuds Proxmox ;
* la VM Zabbix ;
* les autres machines Linux ;
* les autres serveurs Windows qui ne fournissent pas les mêmes services Active Directory.

---

## 2. Fichier disponible

| Fichier              | Cible                       | Fonction                                                                                                               |
| -------------------- | --------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `ad-monitoring.conf` | Contrôleur Active Directory | UserParameters permettant de superviser Active Directory, DNS, réplication, sauvegardes, DFSR et sessions utilisateurs |

Le fichier doit être placé dans le répertoire de configuration de Zabbix Agent 2 :

```text
C:\Program Files\Zabbix Agent 2\zabbix_agent2.d\
```

---

## 3. Éléments supervisés

Les UserParameters actuellement définis couvrent plusieurs domaines.

### Active Directory

* nombre de rôles FSMO ;
* présence du partage SYSVOL ;
* résolution DNS locale ;
* échecs de réplication Active Directory.

### Sauvegardes

* âge de la dernière sauvegarde ;
* présence d'une sauvegarde ;
* état de l'opération de sauvegarde.

Les contrôles utilisent `wbadmin`.

### DFS Replication

* événements permettant de détecter une situation de backlog DFSR.

### Sessions utilisateurs

* nombre de sessions ;
* liste des utilisateurs connectés.

### DNS Active Directory

* présence de l'enregistrement SRV LDAP du contrôleur de domaine.

---

## 4. Installation

Copier `ad-monitoring.conf` dans :

```text
C:\Program Files\Zabbix Agent 2\zabbix_agent2.d\
```

Puis vérifier que le fichier de configuration principal de Zabbix Agent 2 charge bien le répertoire `zabbix_agent2.d`.

Après modification, redémarrer le service **Zabbix Agent 2**.

---

## 5. Validation

Les UserParameters doivent être testés directement depuis l'agent avant leur utilisation dans les éléments Zabbix.

Exemple :

```powershell
& "C:\Program Files\Zabbix Agent 2\zabbix_agent2.exe" -t ad.fsmo.count
```

D'autres clés peuvent être testées selon le même principe :

```text
ad.sysvol.present
ad.dns.resolve.local
ad.replication.failures
ad.backup.age
ad.backup.present
ad.backup.status
ad.dfsr.backlog
windows.users.count
windows.users.list
ad.dns.srv
```

Une valeur retournée par l'agent doit être interprétée en fonction de la métrique concernée. Une commande fonctionnant correctement au niveau PowerShell ne garantit pas à elle seule que le UserParameter est correctement exécuté par Zabbix Agent 2.

---

## 6. Sécurité

Les UserParameters exécutent des commandes PowerShell depuis le contexte du service Zabbix Agent 2.

Ils doivent donc rester limités à des commandes nécessaires à la supervision.

L'utilisation de :

```text
-ExecutionPolicy Bypass
```

est conservée ici parce qu'elle fait partie de la configuration validée du laboratoire. Elle ne doit pas être considérée comme une recommandation générale pour les scripts PowerShell.

Toute modification d'un UserParameter doit être testée avant son déploiement.

---

## 7. Relation avec les autres UserParameters

Les UserParameters du laboratoire sont organisés **par cible**, et non uniquement par technologie.

```text
zabbix/
└── userparameters/
    ├── Proxmox/
    ├── Zabbix/
    └── AD/
```

Cette organisation permet d'éviter qu'un apprenant installe par erreur une configuration destinée à une autre machine.

Par exemple :

* `Proxmox/proxmox.conf` concerne les nœuds Proxmox ;
* `Proxmox/nvme.conf` concerne le stockage physique des nœuds Proxmox ;
* `Zabbix/crowdsec.conf` concerne la VM Zabbix ;
* `AD/ad-monitoring.conf` concerne le contrôleur de domaine Windows.

---

## 8. Documentation associée

La compréhension de cette configuration doit être complétée par :

* la documentation générale du [Zabbix Agent 2](../../docs/05-Monitoring/README.md) ;
* la documentation de l'architecture de supervision ;
* la documentation Active Directory du laboratoire ;
* les templates Zabbix associés présents dans `zabbix/templates/`.

Les UserParameters constituent uniquement la partie **agent** de la supervision. Les items, triggers, macros et autres éléments nécessaires à leur exploitation dans Zabbix doivent être documentés et versionnés dans les répertoires correspondants de `zabbix/`.
