# 05 - Événements observables

| Élément | Valeur |
| **Nom du document** | `05-Evenements-observables.md` |
| **Technologie** | CrowdSec |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les événements permettant de surveiller le fonctionnement de CrowdSec et les comportements de sécurité détectés. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Événements de fonctionnement

Le fonctionnement de CrowdSec doit pouvoir être contrôlé à travers notamment :

* l'état du service ;
* l'état de la LAPI ;
* les erreurs de fonctionnement ;
* les erreurs de lecture des journaux ;
* les problèmes liés aux parsers ;
* les problèmes liés aux scénarios.

---

# Événements de sécurité

Les événements produits par CrowdSec permettent notamment d'observer :

* les comportements détectés ;
* les sources identifiées ;
* les scénarios déclenchés ;
* les décisions générées ;
* les décisions actives ;
* les éventuelles expirations de décisions.

---

# Intégration Zabbix

CrowdSec est intégré à la supervision **Zabbix** du laboratoire.

Les éléments critiques doivent permettre de détecter au minimum :

* l'arrêt du service CrowdSec ;
* l'indisponibilité de la LAPI ;
* les anomalies importantes affectant le fonctionnement du dispositif.

La supervision ne doit pas être limitée à l'existence du processus : elle doit également vérifier que les composants nécessaires au fonctionnement sont opérationnels.

---

# Exploitation des événements

Les événements observés peuvent servir à :

1. détecter un comportement suspect ;
2. confirmer le fonctionnement du dispositif ;
3. analyser une tentative d'attaque ;
4. vérifier qu'une décision a été correctement appliquée ;
5. investiguer un incident.

Les événements CrowdSec doivent être considérés comme une source complémentaire aux journaux système et applicatifs.
