# 08 - Mises à jour et gestion des vulnérabilités


| Élément | Valeur |
| **Nom du document** | `08-Mises-a-jour-et-gestion-des-vulnerabilites.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Cycle de mise à jour

Les systèmes Debian doivent être maintenus à jour afin de bénéficier des correctifs publiés par le projet.

Debian publie régulièrement des mises à jour de sécurité pour la version stable. Debian 13.6, publiée le 11 juillet 2026, contient notamment des corrections de sécurité.

---

## APT

La première étape consiste à actualiser les informations disponibles :

```bash
apt update
```

Les mises à jour disponibles peuvent ensuite être installées avec :

```bash
apt upgrade
```

Une mise à jour plus complète peut être réalisée avec :

```bash
apt full-upgrade
```

---

## Sources de sécurité

Le projet Debian fournit plusieurs sources officielles :

* Debian Security Tracker ;
* Debian Security Advisories ;
* informations CVE ;
* données OVAL.

Le Security Tracker constitue la source principale de suivi des problèmes de sécurité Debian.

---

## Vulnérabilités

Une vulnérabilité doit être analysée selon :

* le paquet concerné ;
* la version installée ;
* la version corrigée ;
* l'exposition du service ;
* la criticité du système ;
* l'existence d'une mesure compensatoire.

---

## Mise à jour automatique

Debian documente également l'utilisation de `unattended-upgrades` pour automatiser certaines mises à jour.

Son activation doit toutefois être évaluée selon le rôle du système et les contraintes opérationnelles.

---

## Traçabilité

Les mises à jour importantes doivent être documentées lorsqu'elles peuvent affecter :

* Proxmox ;
* Zabbix ;
* les services critiques ;
* les dépendances applicatives ;
* la compatibilité système.

---

## Références

* Debian Security Information
* Debian Security Tracker
* Debian 13 Release Notes
* Debian Administrator's Handbook
