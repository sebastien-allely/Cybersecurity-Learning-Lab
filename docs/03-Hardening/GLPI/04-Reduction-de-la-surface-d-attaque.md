# 04 - Réduction de la surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Reduction-de-la-surface-d-attaque.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Réduire la surface d'attaque consiste à limiter les possibilités d'exploitation offertes à un attaquant sans dégrader les fonctionnalités nécessaires au fonctionnement du laboratoire.

---

# 2. Risques identifiés

Les principaux risques sont :

- exploitation d'une fonctionnalité inutile ;
- exposition d'une interface d'administration ;
- utilisation de plugins vulnérables ;
- augmentation de la dette technique ;
- erreurs de configuration.

---

# 3. Décisions retenues

Le référentiel recommande :

- désinstaller les plugins inutilisés ;
- supprimer les comptes obsolètes ;
- limiter les profils disposant de privilèges élevés ;
- désactiver les fonctionnalités non utilisées ;
- limiter les services accessibles depuis le réseau ;
- maintenir une configuration aussi simple que possible.

---

# 4. Vérification

Une revue régulière doit permettre de contrôler :

- les plugins installés ;
- les profils utilisateurs ;
- les interfaces accessibles ;
- les paramètres de sécurité de GLPI01.

---

# 5. Supervision

Les événements suivants présentent une valeur opérationnelle :

- installation d'un plugin ;
- suppression d'un plugin ;
- modification des paramètres de sécurité ;
- apparition d'un nouveau compte administrateur.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Apache HTTP Server
- PHP
- MariaDB

## Dépendances de sécurité

- CrowdSec
- Fail2ban
- ZABBIX01

---

# 7. Conclusion

La réduction de la surface d'attaque diminue le nombre de scénarios d'exploitation possibles et simplifie l'administration sécurisée de GLPI01.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ISO/IEC 27002.

## Documentation officielle

- Documentation GLPI01.

## Guides techniques

- SOCLE – Stéphane Robert.
