# README - Architecture Debian


| Élément | Valeur |
| **Nom du document** | `README.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Présentation

Debian GNU/Linux constitue l'un des socles systèmes du **laboratoire** du projet **Cybersecurity-Learning-Lab**.

Il est utilisé notamment :

* comme système sous-jacent à Proxmox VE ;
* pour le serveur de supervision Zabbix ;
* comme référence GNU/Linux complémentaire à Ubuntu ;
* pour les expérimentations nécessitant un environnement Debian.

La documentation Debian est donc distincte de celle consacrée à Ubuntu.

---

## Version de référence

Le laboratoire utilise actuellement Debian 13, nom de code **Trixie**, comme version de référence.

Debian 13 est actuellement la version stable de Debian. Le projet Debian publie régulièrement des mises à jour de la distribution, notamment pour corriger des vulnérabilités de sécurité.

---

## Périmètre

Cette documentation couvre :

* l'architecture Debian ;
* son rôle dans le laboratoire ;
* l'installation ;
* le système de fichiers ;
* le réseau ;
* les services ;
* la journalisation ;
* la supervision ;
* les mises à jour ;
* les sauvegardes ;
* l'exploitation ;
* le diagnostic.

Les mesures de durcissement sont documentées séparément dans :

```text
docs/03-Hardening/Debian/
```

---

## Référentiels utilisés

Le référentiel Debian du laboratoire s'appuie en priorité sur :

* documentation officielle Debian ;
* Debian Security Tracker ;
* Debian Security Advisories ;
* documentation Debian 13 ;
* Debian Administrator's Handbook ;
* recommandations de sécurité pertinentes ;
* référentiel du Cybersecurity-Learning-Lab.

Debian fournit notamment un système officiel de suivi des vulnérabilités et des avis de sécurité compatibles avec les CVE.

---

## Relation avec Ubuntu

Debian et Ubuntu sont documentés séparément.

Ubuntu étant dérivé de Debian, certaines pratiques peuvent être communes, mais les deux distributions ne doivent pas être considérées comme interchangeables.

Les versions des paquets, les mécanismes de configuration, les politiques de support et certains choix d'intégration peuvent différer.

---

## Architecture actuelle

Dans le laboratoire, Debian intervient notamment dans :

```text
Infrastructure
     │
     ├── Proxmox VE
     │      └── socle Debian
     │
     └── ZABBIX01
            └── serveur Zabbix
```

Cette représentation ne constitue pas un inventaire exhaustif des futurs systèmes Debian du laboratoire.

---

## Principes documentaires

La documentation doit :

* distinguer Debian des distributions dérivées ;
* documenter l'état réellement déployé ;
* distinguer architecture actuelle et architecture cible ;
* éviter les informations permettant d'identifier l'infrastructure réelle ;
* renvoyer vers le référentiel de hardening pour les mesures de sécurité détaillées ;
* conserver les références utilisées pour les décisions techniques.
