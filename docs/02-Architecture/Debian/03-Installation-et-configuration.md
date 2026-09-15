# 03 - Installation et configuration


| Élément | Valeur |
| **Nom du document** | `03-Installation-et-configuration.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Installation

L'installation doit utiliser une version Debian stable supportée.

La version de référence actuelle du laboratoire est Debian 13 Trixie.

Les médias et dépôts utilisés doivent provenir de sources Debian officielles ou de miroirs Debian de confiance.

---

## Configuration initiale

Après installation, les éléments suivants doivent être vérifiés :

* nom d'hôte ;
* configuration réseau ;
* résolution DNS ;
* synchronisation temporelle ;
* dépôts APT ;
* mises à jour disponibles ;
* services actifs ;
* comptes administratifs ;
* espace disque.

---

## Gestion des paquets

La gestion des logiciels repose sur APT.

Commandes courantes :

```bash
apt update
apt upgrade
apt full-upgrade
apt install <paquet>
apt remove <paquet>
```

Les opérations de mise à jour doivent être réalisées en tenant compte du rôle du système.

---

## Dépôts

Les dépôts doivent être limités aux sources nécessaires.

L'utilisation de dépôts tiers doit être justifiée avant intégration.

---

## Configuration

Les fichiers de configuration doivent être :

* identifiés ;
* documentés ;
* protégés ;
* sauvegardés lorsqu'ils sont critiques.

Une modification de configuration doit être réalisée de manière contrôlée.

---

## Références

* Documentation Debian 13
* Debian Administrator's Handbook
* Documentation APT
