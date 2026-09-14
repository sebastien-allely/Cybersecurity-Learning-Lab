# 01 - Vue d'ensemble


| Élément | Valeur |
| **Nom du document** | `01-Vue-d-ensemble.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---


## Présentation

Debian GNU/Linux est une distribution GNU/Linux généraliste utilisée dans le laboratoire comme système d'exploitation serveur.

Elle fournit un environnement stable, maintenable et largement utilisé dans les infrastructures professionnelles.

Dans le laboratoire, Debian constitue notamment le socle du système utilisé par Proxmox VE et l'environnement du serveur Zabbix.

---

## Version de référence

La version de référence actuelle est :

```text
Debian GNU/Linux 13 - Trixie
```

Debian 13 est la version stable actuelle et bénéficie de mises à jour de sécurité publiées par le projet Debian.

---

## Caractéristiques

Debian repose notamment sur :

* un système de gestion des paquets APT ;
* des dépôts officiels ;
* un modèle de publication stable ;
* un système de suivi des vulnérabilités ;
* une documentation officielle importante ;
* un large écosystème de logiciels libres.

---

## Positionnement

Debian est utilisé comme socle système et non comme service applicatif unique.

Les services exécutés au-dessus du système sont documentés dans leurs propres référentiels.

Exemples :

```text
Debian
 ├── Proxmox VE
 └── Zabbix
```

---

## Sécurité

La sécurité de Debian repose notamment sur :

* les mises à jour de sécurité ;
* le suivi des vulnérabilités ;
* la réduction de la surface d'attaque ;
* le contrôle des services ;
* la gestion des comptes ;
* la journalisation ;
* la supervision ;
* le contrôle des accès.

Le projet Debian publie des avis de sécurité et maintient un Security Tracker permettant de suivre les vulnérabilités affectant les paquets.

---

## Références

* Documentation officielle Debian
* Debian Security Tracker
* Debian Security Advisories
* Debian Administrator's Handbook
