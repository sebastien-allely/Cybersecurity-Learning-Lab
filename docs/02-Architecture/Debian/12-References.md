# 12 - Références

| Élément                           | Valeur                                                                                                                                                                          |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `12-References.md`                                                                                                                                                              |
| **Technologie**                   | Debian                                                                                                                                                                          |
| **Catégorie**                     | Références                                                                                                                                                                      |
| **Objectif**                      | Regrouper les principales sources utilisées pour documenter l'architecture, l'installation, l'exploitation et les caractéristiques du socle Debian utilisé dans le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                                                                                |
| **Version**                       | 1.0                                                                                                                                                                             |
| **Date de dernière modification** | 02/08/2026                                                                                                                                                                      |

---

## 1. Objectif du document

Ce document regroupe les références utilisées pour documenter Debian dans le référentiel **Cybersecurity-Learning-Lab**.

Les sources permettent notamment de vérifier :

* les caractéristiques de Debian ;
* les mécanismes d'installation et d'administration ;
* la gestion des paquets ;
* le fonctionnement des services ;
* la gestion du réseau ;
* la journalisation ;
* les mises à jour ;
* la gestion des vulnérabilités ;
* les bonnes pratiques d'exploitation.

Les références sont complémentaires aux décisions et observations propres au laboratoire.

---

# 2. Documentation officielle Debian

La documentation officielle Debian constitue la référence principale pour le système Debian.

Elle permet notamment de consulter les informations relatives :

* à l'installation ;
* à l'administration ;
* aux paquets ;
* aux services ;
* au réseau ;
* au stockage ;
* à la sécurité ;
* à la maintenance du système.

La documentation officielle doit être privilégiée lorsqu'une information concerne directement le fonctionnement de Debian.

---

# 3. Debian Administrator's Handbook

Le **Debian Administrator's Handbook** constitue une ressource complémentaire pour comprendre l'administration d'un système Debian.

Il est particulièrement utile pour approfondir :

* l'installation ;
* la gestion des paquets ;
* les services ;
* le réseau ;
* le stockage ;
* l'administration système ;
* la maintenance.

Cette ressource complète la documentation officielle sans la remplacer.

---

# 4. Debian Security

Les informations de sécurité publiées par Debian constituent une référence pour le suivi des vulnérabilités affectant les paquets Debian.

Elles permettent notamment d'identifier :

* les vulnérabilités publiées ;
* les paquets concernés ;
* les versions corrigées ;
* les avis de sécurité ;
* les informations nécessaires à l'évaluation d'une mise à jour.

Le suivi de ces informations participe au maintien en condition de sécurité des systèmes Debian.

---

# 5. Debian Packages

Les informations relatives aux paquets Debian permettent de vérifier :

* les versions disponibles ;
* les dépendances ;
* les paquets installés ;
* les versions corrigées ;
* les informations relatives aux composants utilisés.

Cette source est particulièrement utile lorsqu'une analyse doit porter sur un paquet précis.

---

# 6. Proxmox VE

Debian constitue également le socle technique de **Proxmox VE** utilisé dans le laboratoire.

La documentation Proxmox doit donc être consultée lorsqu'une question concerne :

* la virtualisation ;
* la configuration des nœuds ;
* le cluster ;
* le stockage ;
* le réseau Proxmox ;
* les sauvegardes ;
* l'administration de l'hyperviseur.

Les éléments propres à Proxmox sont cependant documentés dans le dossier dédié à Proxmox VE.

La documentation Debian reste la référence pour les mécanismes relevant directement du système sous-jacent.

---

# 7. Zabbix

Une VM Debian du laboratoire héberge le serveur **Zabbix**.

La documentation officielle Zabbix constitue donc la référence pour les éléments propres à la solution de supervision, notamment :

* le serveur Zabbix ;
* Zabbix Agent 2 ;
* les fichiers de configuration ;
* les UserParameters ;
* les templates ;
* les mécanismes de supervision.

Les informations propres à Zabbix sont documentées dans le dossier dédié à cette technologie.

Le présent document ne traite que du rôle de Debian comme système hôte.

---

# 8. ANSSI

Les publications de l'**ANSSI** constituent une source complémentaire pour les recommandations de sécurité applicables aux systèmes d'information.

Elles peuvent notamment être utilisées pour documenter :

* le durcissement ;
* l'administration sécurisée ;
* la gestion des comptes ;
* la journalisation ;
* la supervision ;
* la gestion des risques ;
* la réponse aux incidents.

Les recommandations doivent être adaptées au contexte réel du laboratoire.

---

# 9. NIST

Les publications du **NIST** peuvent compléter les références techniques Debian par des recommandations et cadres méthodologiques concernant :

* la gestion des risques ;
* la sécurité des systèmes ;
* la gestion des vulnérabilités ;
* la journalisation ;
* la détection ;
* la réponse aux incidents.

Elles constituent une source complémentaire et ne remplacent pas la documentation officielle Debian.

---

# 10. MITRE ATT&CK

**MITRE ATT&CK** peut être utilisé pour mettre en correspondance les menaces et techniques susceptibles de concerner un système Linux.

Cette approche permet notamment de relier :

**menace → technique → événement observable → détection → mesure de protection.**

Cette référence est particulièrement utile lorsque l'architecture Debian est étudiée sous l'angle de la cybersécurité.

---

# 11. Référentiel Cybersecurity-Learning-Lab

Les documents du référentiel constituent également une source interne.

Ils permettent de conserver la cohérence entre :

* l'architecture ;
* les choix techniques ;
* les mesures de sécurité ;
* la supervision ;
* les sauvegardes ;
* l'exploitation ;
* la maintenance ;
* les exercices de sécurité.

Une décision technique doit autant que possible pouvoir être reliée à son contexte et à son objectif.

---

# 12. Hiérarchie des références

Lorsqu'une information doit être vérifiée, l'ordre de priorité suivant est recommandé :

1. documentation officielle Debian ;
2. avis de sécurité Debian ;
3. documentation officielle du composant concerné ;
4. documentation Proxmox ou Zabbix lorsque le sujet relève de ces technologies ;
5. recommandations ANSSI ;
6. publications NIST ;
7. MITRE ATT&CK ;
8. ressources communautaires et pédagogiques.

Les informations provenant de sources secondaires doivent être confrontées à la documentation officielle avant leur application dans le laboratoire.

---

# 13. Traçabilité

Lorsqu'une décision d'architecture importante repose sur une recommandation externe, la référence utilisée doit être identifiable.

L'objectif est de permettre au lecteur de comprendre :

* quelle source a été utilisée ;
* quel élément elle justifie ;
* dans quel contexte elle s'applique ;
* si la recommandation est toujours pertinente.

Les références doivent être réévaluées lorsque :

* la version Debian évolue ;
* le rôle du système évolue ;
* une nouvelle technologie est ajoutée ;
* l'architecture du laboratoire est modifiée ;
* une vulnérabilité importante est publiée.

---

# 14. Conclusion

Les références constituent le socle documentaire permettant de distinguer les choix propres au laboratoire des recommandations générales applicables à Debian.

La documentation officielle Debian reste la référence principale pour le fonctionnement du système.

Les autres référentiels viennent compléter cette documentation selon le domaine concerné : virtualisation, supervision, cybersécurité, gestion des risques ou réponse à incident.
