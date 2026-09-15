# 01 - Justification des décisions

| Élément                           | Valeur                                                                                          |
| --------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Nom du document**               | `01-Justification-des-decisions.md`                                                             |
| **Technologie**                   | Debian                                                                                          |
| **Catégorie**                     | Hardening                                                                                       |
| **Objectif**                      | Définir les principes guidant les décisions de durcissement des systèmes Debian du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                |
| **Version**                       | 1.0                                                                                             |
| **Date de dernière modification** | 02/08/2026                                                                                      |

---

## 1. Introduction

Debian constitue l'un des socles Linux de référence du laboratoire. Il est notamment utilisé pour certains composants d'infrastructure et pour l'environnement Proxmox VE.

Le durcissement de Debian vise à réduire la surface d'attaque du système tout en maintenant les fonctions nécessaires à son rôle opérationnel.

Le principe retenu n'est donc pas de désactiver indistinctement les fonctionnalités du système, mais de supprimer ou limiter ce qui n'est pas nécessaire, de contrôler les accès et de renforcer les capacités de détection.

---

## 2. Principes de décision

Les décisions de durcissement reposent sur plusieurs principes.

### 2.1 Réduction de la surface d'attaque

Tout service, paquet, compte ou fonctionnalité inutile constitue potentiellement une surface d'attaque supplémentaire.

Les mesures retenues cherchent donc notamment à :

* supprimer les logiciels inutiles ;
* désactiver les services non nécessaires ;
* limiter les ports exposés ;
* limiter les interfaces d'administration ;
* réduire les privilèges ;
* éviter l'exposition directe de services internes.

### 2.2 Principe du moindre privilège

Les utilisateurs, services et processus doivent disposer uniquement des privilèges nécessaires à leur fonction.

Le compte `root` ne doit pas être utilisé pour les opérations courantes.

Lorsque des privilèges élevés sont nécessaires, leur utilisation doit être explicitement contrôlée.

### 2.3 Administration sécurisée

L'administration distante doit être limitée aux protocoles et aux sources nécessaires.

SSH constitue le principal mécanisme d'administration distante des systèmes Debian du laboratoire.

La configuration doit notamment prendre en compte :

* l'authentification ;
* les comptes autorisés ;
* les privilèges ;
* les méthodes d'accès ;
* la limitation de l'exposition réseau ;
* la journalisation.

### 2.4 Maintien en condition de sécurité

Le durcissement initial ne suffit pas.

Les systèmes Debian doivent rester maintenus dans le temps par :

* l'installation régulière des mises à jour de sécurité ;
* le suivi des vulnérabilités ;
* la surveillance des services ;
* la vérification des configurations ;
* la réévaluation périodique des mesures de sécurité.

### 2.5 Détection

Une mesure de sécurité doit autant que possible permettre de détecter une anomalie lorsqu'une prévention échoue.

La journalisation système et la supervision constituent donc des composants complémentaires du durcissement.

---

## 3. Arbitrage sécurité / exploitation

Une mesure de sécurité ne doit pas être appliquée sans considérer le rôle réel du système.

La désactivation d'un service peut améliorer la sécurité d'un système générique mais provoquer une interruption de fonctionnement lorsqu'il est nécessaire au service hébergé.

Chaque décision doit donc être évaluée selon :

1. la fonction du système ;
2. les services réellement nécessaires ;
3. la menace concernée ;
4. la réduction du risque attendue ;
5. l'impact opérationnel ;
6. les possibilités de restauration.

---

## 4. Traçabilité des décisions

Les modifications importantes de configuration doivent être documentées.

Lorsqu'une mesure est appliquée, le référentiel doit permettre de comprendre :

* pourquoi elle a été appliquée ;
* quel risque elle réduit ;
* quelle configuration est concernée ;
* quelles dépendances existent ;
* comment vérifier son bon fonctionnement ;
* comment revenir à l'état précédent lorsque cela est nécessaire.

Cette approche permet d'éviter les modifications de configuration non documentées et facilite les opérations de maintenance ou de réponse à incident.

---

## 5. Référentiels

Les décisions de durcissement doivent être confrontées aux recommandations pertinentes de :

* Debian ;
* ANSSI ;
* CIS lorsque les recommandations sont applicables ;
* NIST ;
* MITRE ATT&CK pour les scénarios d'attaque et les techniques pertinentes.

Ces références ne sont pas appliquées mécaniquement. Elles servent à éclairer les décisions prises dans le contexte du laboratoire.

---

## 6. Positionnement dans le laboratoire

Debian est considéré comme un **socle de référence** du laboratoire.

Le durcissement doit donc rester suffisamment générique pour être applicable à plusieurs rôles, tout en permettant des adaptations lorsqu'un système héberge un service particulier.

Les mesures spécifiques à une technologie — par exemple Proxmox VE ou Zabbix — doivent rester documentées dans la documentation propre à cette technologie.

---

## 7. Conclusion

Le durcissement Debian repose sur une approche progressive et documentée :

1. identifier le rôle du système ;
2. identifier les actifs et services nécessaires ;
3. analyser les risques ;
4. réduire la surface d'attaque ;
5. renforcer les accès ;
6. protéger les communications ;
7. journaliser et superviser ;
8. maintenir le système à jour ;
9. vérifier régulièrement l'efficacité des mesures.

L'objectif n'est pas d'obtenir une configuration théorique maximale, mais une configuration **cohérente avec le niveau de risque accepté et le rôle du système dans le laboratoire**.
