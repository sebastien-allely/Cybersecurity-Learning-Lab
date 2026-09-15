# 01 - Justification des décisions


| Élément | Valeur |
| **Nom du document** | `01-Justification-des-decisions.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le durcissement de GLPI01 vise à protéger les données métier, les comptes utilisateurs et les composants applicatifs contre les menaces susceptibles d'affecter leur disponibilité, leur intégrité ou leur confidentialité.

Les décisions présentées dans ce document résultent directement de l'analyse des risques réalisée pour cette technologie.

---

# 2. Risques identifiés

Les principaux risques sont :

- compromission d'un compte administrateur ;
- fuite d'informations sur le parc informatique ;
- modification non autorisée des tickets ou de l'inventaire ;
- exploitation d'une vulnérabilité applicative ;
- indisponibilité du service.

---

# 3. Principes de conception

Le référentiel repose sur les principes suivants :

- principe du moindre privilège ;
- défense en profondeur ;
- réduction de la surface d'attaque ;
- maintien en condition de sécurité ;
- supervision orientée risque.

---

# 4. Décisions retenues

Le référentiel recommande notamment :

- utiliser HTTPS exclusivement ;
- limiter les privilèges des comptes ;
- supprimer les fonctionnalités inutilisées ;
- protéger les sauvegardes ;
- superviser les événements critiques ;
- documenter toute évolution importante.

---

# 5. Vérification

Une revue régulière doit permettre de vérifier :

- la conformité de la configuration ;
- les comptes privilégiés ;
- les plugins installés ;
- les mesures de supervision.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Apache HTTP Server
- PHP
- MariaDB
- Ubuntu Server

## Dépendances de sécurité

- Active Directory
- ZABBIX01
- CrowdSec
- Fail2ban
- AIDE

---

# 7. Conclusion

Le durcissement de GLPI01 contribue directement à la protection des actifs métier du laboratoire et complète les mesures appliquées aux composants d'infrastructure.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27002.

## Documentation officielle

- Documentation GLPI01.

## Guides techniques

- SOCLE – Stéphane Robert.
