# Fail2ban — Automatisation

# Fail2ban — Automatisation

| Élément                           | Valeur                                                                                                                                                                   |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `README.md`                                                                                                                                                              |
| **Technologie**                   | Fail2ban / Bash / Linux                                                                                                                                                  |
| **Catégorie**                     | Protection / Automatisation                                                                                                                                              |
| **Objectif**                      | Documenter les filtres et configurations Fail2ban fournis par le laboratoire afin de protéger certains services contre des tentatives d'accès abusives ou malveillantes. |
| **Auteur**                        | Sébastien Allely                                                                                                                                                         |
| **Version**                       | 1.0                                                                                                                                                                      |
| **Date de dernière modification** | 11/08/2026                                                                                                                                                               |

---

## Objectif

Ce répertoire contient les éléments de configuration Fail2ban utilisés dans le laboratoire.

Fail2ban analyse les événements produits par certains services et peut déclencher une action de bannissement lorsqu'un comportement correspondant à un filtre configuré est détecté.

Les configurations présentes ici concernent notamment :

* Proxmox ;
* GLPI ;
* leurs mécanismes d'authentification et certaines interfaces associées.

Fail2ban constitue un mécanisme de protection complémentaire. Il ne remplace ni un pare-feu, ni un système de détection, ni un EDR, ni une solution de supervision.

---

## Organisation

```text
fail2ban/
├── README.md
├── filter.d/
│   ├── glpi-api.conf
│   ├── glpi-auth.conf
│   ├── glpi-inventory.conf
│   ├── proxmox-api.conf
│   └── proxmox-auth.conf
└── jail.d/
    ├── glpi.local
    └── proxmox.local
```

### `filter.d/`

Les fichiers présents dans ce répertoire définissent les motifs recherchés dans les journaux afin d'identifier les événements correspondant aux comportements surveillés.

* `glpi-api.conf` : événements associés à l'API GLPI ;
* `glpi-auth.conf` : événements associés à l'authentification GLPI ;
* `glpi-inventory.conf` : événements associés aux mécanismes d'inventaire GLPI ;
* `proxmox-api.conf` : événements associés à l'API Proxmox ;
* `proxmox-auth.conf` : événements associés à l'authentification Proxmox.

### `jail.d/`

Les fichiers présents dans ce répertoire définissent les jails qui utilisent les filtres précédents et les paramètres de protection associés.

* `glpi.local` : configuration des protections Fail2ban appliquées à GLPI ;
* `proxmox.local` : configuration des protections Fail2ban appliquées à Proxmox.

---

## Installation

Les filtres doivent être installés dans :

```text
/etc/fail2ban/filter.d/
```

Les jails doivent être installées dans :

```text
/etc/fail2ban/jail.d/
```

Après installation ou modification d'une configuration, vérifier la syntaxe et l'état du service avant de considérer la configuration comme opérationnelle.

Exemples :

```bash
sudo fail2ban-client -t
sudo systemctl restart fail2ban
sudo systemctl status fail2ban
```

La validation doit également vérifier que les journaux réellement produits par le service correspondent aux expressions définies dans les filtres.

---

## Vérification

Lister les jails actives :

```bash
sudo fail2ban-client status
```

Afficher le détail d'une jail :

```bash
sudo fail2ban-client status <jail>
```

La présence d'une jail dans la configuration ne garantit pas à elle seule son bon fonctionnement. La validation doit notamment confirmer :

1. que le fichier journal attendu existe ;
2. que le backend utilisé permet sa lecture ;
3. que les événements recherchés sont effectivement produits ;
4. que le filtre identifie correctement ces événements ;
5. que l'action de bannissement fonctionne ;
6. qu'aucun faux positif important n'est généré.

---

## Sécurité

Les configurations doivent être adaptées à l'environnement cible avant déploiement.

Une mauvaise expression régulière ou un mauvais chemin de journalisation peut provoquer :

* des détections manquées ;
* des faux positifs ;
* des bannissements légitimes ;
* ou une protection totalement inactive.

Les paramètres de bannissement doivent donc être validés avec les contraintes opérationnelles du système concerné.

---

## Fichiers associés

### Filtres

* [`glpi-api.conf`](./filter.d/glpi-api.conf)
* [`glpi-auth.conf`](./filter.d/glpi-auth.conf)
* [`glpi-inventory.conf`](./filter.d/glpi-inventory.conf)
* [`proxmox-api.conf`](./filter.d/proxmox-api.conf)
* [`proxmox-auth.conf`](./filter.d/proxmox-auth.conf)

### Jails

* [`glpi.local`](./jail.d/glpi.local)
* [`proxmox.local`](./jail.d/proxmox.local)
