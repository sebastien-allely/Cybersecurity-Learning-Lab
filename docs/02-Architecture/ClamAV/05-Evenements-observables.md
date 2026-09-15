# 05 - Événements observables

| Élément | Valeur |
| **Nom du document** | `05-Evenements-observables.md` |
| **Technologie** | ClamAV |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les événements permettant de contrôler le fonctionnement de ClamAV et les résultats des analyses antivirus. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Événements de fonctionnement

Les événements importants comprennent :

* démarrage d'un service ;
* arrêt d'un service ;
* échec d'une mise à jour ;
* erreur de configuration ;
* erreur d'accès à un fichier ;
* interruption d'une analyse.

---

# Événements de sécurité

Les analyses peuvent notamment produire :

* aucune menace détectée ;
* fichier infecté ;
* fichier suspect ;
* fichier placé en quarantaine ;
* erreur d'analyse.

---

# Mise à jour des signatures

L'état de la base de signatures constitue également un événement important.

Une base trop ancienne doit être considérée comme une dégradation du niveau de protection.

---

# Supervision

Zabbix peut être utilisé pour surveiller les éléments pertinents de ClamAV.

La supervision doit permettre de distinguer :

* fonctionnement normal ;
* service arrêté ;
* mise à jour défaillante ;
* anomalie nécessitant une intervention.

---

# Exploitation

Les événements ClamAV peuvent être utilisés pour :

* détecter un fichier malveillant ;
* déclencher une analyse complémentaire ;
* alimenter une investigation ;
* vérifier le bon fonctionnement de la protection ;
* contrôler l'état de la base de signatures.
