# 01 - Justification de l'outil

| Élément | Valeur |
| **Nom du document** | `01-Justification-de-l-outil.md` |
| **Technologie** | CrowdSec |
| **Catégorie** | Architecture |
| **Objectif** | Justifier l'intégration de CrowdSec dans l'architecture de sécurité du laboratoire et préciser son rôle dans la détection et la réponse automatisée aux comportements malveillants. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Rôle de CrowdSec dans le laboratoire

CrowdSec est utilisé comme mécanisme de **détection comportementale et de réponse collaborative**.

Il analyse les événements produits par les services surveillés afin d'identifier des comportements pouvant correspondre à des attaques ou à des abus, puis peut produire des décisions permettant de bloquer les sources identifiées.

Dans le laboratoire, CrowdSec constitue donc une couche complémentaire aux mécanismes de sécurité natifs des systèmes.

Il ne remplace notamment pas :

* le pare-feu ;
* les permissions système ;
* l'authentification ;
* l'antivirus ;
* l'intégrité système ;
* la supervision Zabbix.

---

# Justification du choix

L'intégration de CrowdSec répond principalement aux besoins suivants :

* détecter des comportements malveillants à partir des journaux ;
* identifier les tentatives répétées d'attaque ;
* automatiser certaines réponses ;
* centraliser les décisions de sécurité via la LAPI ;
* disposer d'un mécanisme complémentaire aux protections locales ;
* fournir des événements exploitables par la supervision.

Le choix s'inscrit dans une approche **défense en profondeur**.

---

# Positionnement dans l'architecture

CrowdSec est déployé sur les systèmes pour lesquels l'analyse des journaux apporte une valeur de sécurité.

Dans le laboratoire, il est notamment utilisé sur :

* le serveur Active Directory ;
* le serveur Zabbix ;
* le serveur GLPI ;
* les nœuds Proxmox.

Les composants CrowdSec doivent rester proportionnés au rôle et à l'exposition de chaque système.

---

# Limites

CrowdSec ne doit pas être considéré comme un EDR ou un XDR.

Il ne fournit pas à lui seul :

* une analyse comportementale complète des processus ;
* une protection mémoire ;
* une analyse exhaustive des fichiers ;
* une réponse à incident complète ;
* une protection contre toutes les formes de compromission.

Son efficacité dépend notamment :

* de la qualité des journaux disponibles ;
* des scénarios configurés ;
* des parsers utilisés ;
* de la pertinence des décisions ;
* de l'intégration avec les mécanismes de blocage.

---

# Principe retenu

CrowdSec est donc considéré comme une **couche de détection et de réaction**, intégrée au dispositif global de sécurité du laboratoire.

Son fonctionnement doit être observé et supervisé afin de détecter également une éventuelle défaillance de CrowdSec lui-même.
