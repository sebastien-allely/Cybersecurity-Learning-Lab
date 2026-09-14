# 02 - Architecture


| Élément | Valeur |
| **Nom du document** | `02-Architecture.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Protection |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |




## Objectif

Comprendre le fonctionnement interne de Fail2ban avant toute configuration.

## Fonctionnement

Application
        ↓
Journal systemd / fichier log
        ↓
Filtre (Regex)
        ↓
Détection d'échec
        ↓
Jail
        ↓
Action
        ↓
nftables
        ↓
Adresse IP bannie

## Les composants

### Journaux

Source des événements.

### Filtres

Expressions régulières détectant les comportements suspects.

### Jails

Association :

- filtre
- journal
- politique de bannissement
- action

### Actions

Exécution automatique :

- ajout d'une règle nftables ;
- notification ;
- script personnalisé.

### Backend

Dans le Cybersecurity Learning Lab, le backend recommandé est :

systemd

afin d'utiliser directement les journaux persistants.

## Architecture retenue

Une jail par service exposé.

Exemple :

- SSH
- Proxmox
- Apache
- Nginx
- GLPI01

Chaque jail possède :

- son filtre ;
- ses paramètres ;
- sa validation indépendante.

## Pourquoi cette architecture ?

- simplicité ;
- maintenance facilitée ;
- débogage rapide ;
- réduction des faux positifs ;
- reproductibilité.

## Conclusion

La séparation des jails permet une administration plus lisible et plus évolutive.
