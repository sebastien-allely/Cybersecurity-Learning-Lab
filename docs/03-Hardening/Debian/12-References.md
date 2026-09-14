# 12 - Références

| Élément                           | Valeur                                                                                                                      |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `12-References.md`                                                                                                          |
| **Technologie**                   | Debian                                                                                                                      |
| **Catégorie**                     | Références                                                                                                                  |
| **Objectif**                      | Regrouper les sources utilisées pour définir et justifier les mesures de sécurité applicables à Debian dans le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                            |
| **Version**                       | 1.0                                                                                                                         |
| **Date de dernière modification** | 02/08/2026                                                                                                                  |

---

## 1. Objectif

Les mesures de sécurité appliquées au laboratoire ne doivent pas reposer uniquement sur des choix personnels.

Ce document regroupe les principales sources permettant de vérifier, justifier ou approfondir les décisions relatives à Debian.

Les recommandations doivent être adaptées au contexte réel du système et à son niveau d'exposition.

---

## 2. Debian

La documentation officielle Debian constitue la première source de référence pour :

* l'administration du système ;
* la gestion des paquets ;
* les services ;
* la configuration système ;
* la sécurité ;
* les mises à jour.

Les informations relatives à Debian doivent être privilégiées lorsqu'une décision concerne directement le fonctionnement du système.

---

## 3. Debian Security

Les avis de sécurité Debian constituent une source essentielle pour le suivi des vulnérabilités affectant les paquets Debian.

Ils permettent notamment de vérifier :

* les vulnérabilités publiées ;
* les paquets concernés ;
* les versions corrigées ;
* les informations relatives aux correctifs.

---

## 4. ANSSI

Les publications de l'ANSSI peuvent être utilisées pour compléter les recommandations techniques par une approche française de cybersécurité.

Elles sont notamment pertinentes pour :

* le durcissement ;
* la gestion des risques ;
* l'administration sécurisée ;
* la journalisation ;
* la supervision ;
* la réponse à incident.

---

## 5. NIST

Les publications du NIST fournissent un cadre méthodologique complémentaire pour :

* la gestion des risques ;
* la sécurité des systèmes ;
* la détection ;
* la réponse aux incidents ;
* la gestion des vulnérabilités.

---

## 6. MITRE ATT&CK

MITRE ATT&CK peut être utilisé pour mettre en correspondance certaines menaces avec les techniques susceptibles d'être utilisées contre un système Linux.

Cette référence est particulièrement utile pour relier :

**menace → technique → mécanisme de détection → mesure de protection.**

---

## 7. Référentiel du laboratoire

Les décisions finalement appliquées à Debian doivent également être confrontées au référentiel interne du **Cybersecurity-Learning-Lab**.

Le référentiel permet notamment de conserver :

* les décisions d'architecture ;
* les choix de durcissement ;
* les mesures de protection ;
* les mécanismes de supervision ;
* les procédures de maintenance ;
* les résultats des exercices.

---

## 8. Hiérarchie des références

En cas de contradiction entre plusieurs sources, la décision doit être analysée selon le contexte.

La priorité doit généralement être donnée :

1. à la documentation officielle du composant ;
2. aux avis de sécurité du fournisseur ou du projet ;
3. aux recommandations institutionnelles ;
4. aux référentiels de cybersécurité ;
5. aux ressources communautaires ou pédagogiques.

Une recommandation externe ne doit pas être appliquée automatiquement sans vérifier sa compatibilité avec l'environnement du laboratoire.

---

## 9. Traçabilité

Lorsqu'une mesure importante est issue d'une recommandation externe, la source doit être mentionnée dans le document concerné lorsque cela apporte une valeur de traçabilité.

L'objectif n'est pas d'accumuler des références mais de permettre au lecteur de comprendre **pourquoi une décision a été prise et sur quelle base elle peut être réévaluée**.
