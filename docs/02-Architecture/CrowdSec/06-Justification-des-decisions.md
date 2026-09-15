# 06 - Justification des décisions

| Élément | Valeur |
| **Nom du document** | `06-Justification-des-decisions.md` |
| **Technologie** | CrowdSec |
| **Catégorie** | Architecture |
| **Objectif** | Documenter les principes guidant le déploiement, la configuration et l'exploitation de CrowdSec dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Principe de défense en profondeur

CrowdSec est retenu comme une couche complémentaire du dispositif de sécurité.

Il vient compléter :

* les mécanismes de sécurité du système ;
* le pare-feu ;
* les contrôles d'accès ;
* les mécanismes d'intégrité ;
* la supervision ;
* les sauvegardes.

---

# Principe de limitation

CrowdSec ne doit analyser que les sources de journaux pertinentes.

Les scénarios doivent correspondre aux services réellement présents sur le système.

L'objectif est d'éviter une configuration inutilement complexe et de réduire les faux positifs.

---

# Principe de supervision

Le dispositif CrowdSec doit être lui-même supervisé.

Une solution de sécurité qui fonctionne silencieusement alors qu'elle est arrêtée ne constitue pas une protection fiable.

La supervision Zabbix permet notamment de détecter :

* l'arrêt du service ;
* l'indisponibilité de la LAPI ;
* les anomalies critiques identifiées par les contrôles retenus.

---

# Principe de protection de la configuration

Les fichiers de configuration CrowdSec doivent être protégés et sauvegardés.

Les modifications importantes doivent être documentées et vérifiées.

Une configuration incorrecte peut modifier directement le comportement de détection ou de blocage.

---

# Principe de validation

Toute modification importante doit être testée avant d'être considérée comme définitive.

Les tests doivent notamment vérifier :

* le fonctionnement du service ;
* la lecture des journaux ;
* le déclenchement attendu des scénarios ;
* la génération des décisions ;
* le fonctionnement de la remédiation ;
* la supervision.

---

# Principe de proportionnalité

Les décisions de blocage doivent rester proportionnées au risque.

CrowdSec ne doit pas être configuré de manière à créer une indisponibilité supérieure au risque qu'il cherche à réduire.

---

# Décision d'architecture

CrowdSec est donc retenu comme **mécanisme complémentaire de détection et de réponse**, intégré au dispositif global du laboratoire et placé sous supervision.
