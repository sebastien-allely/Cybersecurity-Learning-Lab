# Références Ubuntu

| Élément                           | Valeur                                                                                                                         |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `References.md`                                                                                                                |
| **Technologie**                   | Ubuntu                                                                                                                         |
| **Catégorie**                     | Références                                                                                                                     |
| **Objectif**                      | Regrouper les sources de référence utilisées pour définir, vérifier et justifier les mesures de sécurité applicables à Ubuntu. |
| **Auteur**                        | Sébastien Allely                                                                                                               |
| **Version**                       | 1.0                                                                                                                            |
| **Date de dernière modification** | 02/08/2026                                                                                                                     |

---

## 1. Documentation officielle Ubuntu

La documentation officielle Ubuntu constitue la première source à consulter pour les mécanismes propres à Ubuntu.

Elle permet notamment de vérifier :

* l'administration du système ;
* les mécanismes de sécurité ;
* les versions supportées ;
* la gestion des paquets ;
* AppArmor ;
* les services ;
* les mises à jour.

---

## 2. Ubuntu Security Notices

Les **Ubuntu Security Notices (USN)** constituent la source de référence pour le suivi des vulnérabilités et correctifs de sécurité publiés pour Ubuntu.

Ils permettent notamment d'identifier :

* le composant concerné ;
* la vulnérabilité ;
* les versions affectées ;
* les versions corrigées ;
* les éventuelles informations d'exploitation.

---

## 3. Canonical

Les ressources de **Canonical** complètent la documentation Ubuntu pour les composants maintenus par l'éditeur.

Elles sont particulièrement utiles lorsque la configuration concerne :

* Ubuntu Server ;
* les mécanismes de sécurité Ubuntu ;
* les mises à jour ;
* les services maintenus par Canonical.

---

## 4. Debian

Ubuntu étant dérivé de Debian, la documentation Debian peut constituer une référence complémentaire pour certains mécanismes généraux du système Linux et de la gestion des paquets.

Elle ne doit toutefois pas être considérée comme une référence suffisante pour les spécificités propres à Ubuntu.

---

## 5. ANSSI

Les recommandations de l'ANSSI peuvent compléter les recommandations techniques Ubuntu avec une approche de sécurité adaptée au contexte français.

Elles sont notamment pertinentes pour :

* le durcissement ;
* l'administration sécurisée ;
* la gestion des risques ;
* la journalisation ;
* la supervision ;
* la réponse à incident.

---

## 6. NIST

Les publications du NIST peuvent être utilisées pour compléter l'approche technique par des cadres méthodologiques concernant :

* la gestion des risques ;
* la sécurité des systèmes ;
* la détection ;
* la réponse aux incidents ;
* la gestion des vulnérabilités.

---

## 7. MITRE ATT&CK

MITRE ATT&CK permet de mettre en relation les menaces avec les techniques susceptibles d'être utilisées contre des systèmes Linux.

Cette référence peut notamment aider à établir une correspondance :

**menace → technique → observation → détection → mesure de protection.**

---

## 8. Référentiel Cybersecurity-Learning-Lab

Les décisions appliquées au laboratoire doivent également être cohérentes avec le référentiel **Cybersecurity-Learning-Lab**.

Les documents internes permettent de conserver la traçabilité des :

* choix d'architecture ;
* décisions de durcissement ;
* mesures de protection ;
* mécanismes de supervision ;
* procédures de maintenance ;
* exercices ;
* contrôles.

---

## 9. Hiérarchie des sources

Lorsqu'une information doit être vérifiée, l'ordre de priorité doit généralement être :

1. documentation officielle Ubuntu ;
2. avis de sécurité Ubuntu ;
3. documentation officielle du composant concerné ;
4. recommandations institutionnelles ;
5. référentiels de cybersécurité ;
6. ressources communautaires ou pédagogiques.

Une recommandation trouvée dans une source externe doit être confrontée à la version et au rôle du système avant application.

---

## 10. Traçabilité

Lorsqu'une mesure de sécurité importante repose sur une recommandation externe, la source doit être identifiable dans la documentation concernée.

L'objectif n'est pas de multiplier les références, mais de permettre au lecteur de comprendre :

* quelle recommandation a été utilisée ;
* pourquoi elle est pertinente ;
* dans quel contexte elle a été appliquée ;
* comment vérifier son évolution.

Les références doivent être réévaluées lorsque la version d'Ubuntu, le rôle du système ou le niveau d'exposition évolue.
