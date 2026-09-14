# Zabbix

| Élément                           | Valeur                                                                                       |
| --------------------------------- | -------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                  |
| **Technologie**                   | Zabbix                                                                                       |
| **Catégorie**                     | Supervision                                                                                  |
| **Objectif**                      | Regrouper les éléments techniques de supervision utilisés par le Cybersecurity-Learning-Lab. |
| **Auteur**                        | Sébastien Allely                                                                             |
| **Version**                       | 1.0                                                                                          |
| **Date de dernière modification** | 05/08/2026                                                                                   |

---

## 1. Rôle

Le répertoire `zabbix` contient les éléments techniques permettant de reproduire la supervision du laboratoire.

Il constitue la partie opérationnelle de la supervision.

La documentation située dans `docs` explique les choix de supervision.

---

## 2. Éléments concernés

Le dépôt doit progressivement regrouper ici les éléments suivants :

* templates ;
* items ;
* triggers ;
* discovery ;
* UserParameter ;
* scripts associés ;
* macros ;
* dashboards ;
* autres éléments nécessaires à la supervision.

---

## 3. Principe de séparation

La documentation répond notamment aux questions :

* pourquoi superviser cet élément ?
* quel risque ou événement cherche-t-on à détecter ?
* pourquoi cette métrique ?
* quel seuil a été retenu ?
* quelle action doit être réalisée en cas d'alerte ?

Le répertoire `zabbix` contient les éléments permettant d'implémenter cette supervision.

---

## 4. Supervision de sécurité

La supervision ne doit pas être limitée aux performances.

Le laboratoire utilise également Zabbix pour surveiller les mécanismes de sécurité.

Exemples :

* état des services de sécurité ;
* fonctionnement de CrowdSec ;
* état de Fail2ban ;
* intégrité ;
* événements de sécurité ;
* état des sauvegardes ;
* disponibilité des composants critiques.

---

## 5. Principe de traçabilité

Chaque élément technique ajouté dans ce répertoire doit pouvoir être relié à une documentation.

La chaîne attendue est :

```text
Risque / besoin
      ↓
Décision
      ↓
Élément de supervision
      ↓
Donnée collectée
      ↓
Seuil
      ↓
Trigger
      ↓
Alerte
      ↓
Action
```

---

## 6. Agent Zabbix

Les machines virtuelles Linux et Windows du laboratoire utilisent l'agent Zabbix 2 lorsque celui-ci est nécessaire.

Les configurations spécifiques de l'agent, notamment les `UserParameter`, doivent être conservées avec les éléments permettant de les déployer et documentées dans les dossiers concernés.

---

## 7. Sécurité

Les fichiers du dépôt ne doivent contenir :

* mots de passe ;
* tokens ;
* clés privées ;
* secrets d'API ;
* informations permettant un accès direct à l'infrastructure réelle.

Les paramètres dépendants de l'environnement doivent être externalisés ou documentés comme variables à adapter.

---

## 8. Organisation du dépôt
zabbix/
└── userparameters/
    ├── Proxmox/
    │   ├── README.md
    │   ├── crowdsec.conf
    │   ├── nvme.conf
    │   └── proxmox.conf
    │
    ├── Zabbix/
    │   ├── README.md
    │   └── crowdsec.conf
    │
    └── AD/
        ├── README.md
        └── ad-monitoring.conf

Chaque répertoire correspond à une cible d'installation. Un fichier portant le même nom dans deux répertoires peut donc contenir une configuration différente adaptée à la machine concernée.

---


## 9. Fichiers associés

Fichiers associés
crowdsec.conf
UserParameters Proxmox
UserParameters Active Directory
