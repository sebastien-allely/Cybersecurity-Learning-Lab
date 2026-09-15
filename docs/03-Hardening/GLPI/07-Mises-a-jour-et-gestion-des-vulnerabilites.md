# 07 - Mises à jour et gestion des vulnérabilités


| Élément | Valeur |
| **Nom du document** | `07-Mises-a-jour-et-gestion-des-vulnerabilites.md` |
| **Technologie** | GLPI |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le maintien en condition de sécurité (MCS) garantit que GLPI01 reste protégé face à l'évolution des vulnérabilités affectant l'application et ses composants.

---

# 2. Actifs concernés

Les mesures décrites concernent notamment :

- GLPI01 ;
- les plugins installés ;
- PHP ;
- Apache HTTP Server ;
- MariaDB ;
- Ubuntu Server ;
- les dépendances logicielles.

---

# 3. Risques identifiés

Les principaux risques sont :

- exploitation d'une vulnérabilité connue ;
- plugin obsolète ;
- incompatibilité après mise à jour ;
- dette technique ;
- perte de support de l'éditeur.

---

# 4. Décisions retenues

Le référentiel recommande :

- maintenir GLPI01 dans une version supportée ;
- supprimer les plugins inutilisés ;
- maintenir les plugins utilisés à jour ;
- appliquer les correctifs de sécurité dans des délais adaptés à leur criticité ;
- documenter chaque mise à jour ;
- vérifier le bon fonctionnement de GLPI01 après toute évolution.

---

# 5. Vérification

Une revue régulière doit permettre de contrôler :

- la version de GLPI01 ;
- les versions des plugins ;
- la version de PHP ;
- la version d'Apache ;
- la version de MariaDB ;
- les correctifs appliqués.

---

# 6. Supervision

Les événements suivants présentent une valeur opérationnelle :

- disponibilité d'une mise à jour critique ;
- plugin non compatible ;
- erreur après mise à jour ;
- arrêt de GLPI01 après maintenance.

---

# 7. Dépendances avec les autres référentiels

## Dépendances techniques

- Apache HTTP Server
- PHP
- MariaDB
- Ubuntu Server

## Dépendances de sécurité

- ZABBIX01
- CrowdSec
- Fail2ban

---

# 8. Conclusion

Le maintien à jour constitue l'une des mesures les plus efficaces pour limiter le risque d'exploitation de vulnérabilités connues.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation GLPI01.

## Guides techniques

- SOCLE – Stéphane Robert (à vérifier avant chaque mise à jour du présent document).
