# 05 - Événements observables

| Élément | Valeur |
| **Nom du document** | `05-Evenements-observables.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les événements permettant de contrôler le fonctionnement de Fail2ban et les comportements détectés. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Événements de fonctionnement

Les événements importants comprennent notamment :

* démarrage du service ;
* arrêt du service ;
* erreurs de configuration ;
* erreurs de lecture des journaux ;
* erreurs liées aux filtres ;
* erreurs liées aux actions.

---

# Événements de sécurité

Fail2ban permet notamment d'observer :

* les tentatives correspondant à un filtre ;
* les dépassements de seuil ;
* les bannissements ;
* les débannissements ;
* les erreurs empêchant une action.

---

# Supervision Zabbix

Le laboratoire utilise Zabbix pour compléter la surveillance de Fail2ban.

Les contrôles doivent notamment permettre d'identifier :

* un service arrêté ;
* une anomalie de fonctionnement ;
* une situation nécessitant une intervention.

Les éléments réellement supervisés sont définis dans la documentation de monitoring du laboratoire.

---

# Exploitation

Les événements Fail2ban peuvent contribuer à :

* identifier une tentative de brute force ;
* confirmer qu'une protection s'est déclenchée ;
* vérifier l'efficacité d'une jail ;
* analyser un incident ;
* vérifier une modification de configuration.

Fail2ban doit être corrélé avec les autres sources disponibles lorsque l'événement présente une importance particulière.
