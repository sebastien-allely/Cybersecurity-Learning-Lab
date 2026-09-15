---

Nom du document : Vérification du durcissement Proxmox
Technologie : Proxmox VE
Catégorie : Travaux pratiques – Hardening
Objectif : Vérifier que les principales mesures de durcissement documentées sur les nœuds Proxmox sont effectivement appliquées
Auteur : Sébastien ALLELY
Version : 1.0
Date de dernière modification : 13/09/2026
------------------------------------------

# Vérification du durcissement Proxmox

## 1. Objectif

Ce lab a pour objectif de vérifier que les mesures de durcissement appliquées aux nœuds Proxmox correspondent aux décisions de sécurité documentées dans le projet.

Le test porte notamment sur :

* les comptes et privilèges ;
* l'accès SSH ;
* les services exposés ;
* les mises à jour ;
* la configuration système ;
* le stockage ;
* le réseau ;
* les sauvegardes ;
* la supervision.

Le test ne consiste pas uniquement à vérifier la présence d'une configuration. Il doit également permettre de déterminer si celle-ci produit le comportement de sécurité attendu.

---

## 2. Contexte

L'infrastructure repose sur deux nœuds Proxmox constituant un cluster.

Les nœuds hébergent notamment :

* un contrôleur de domaine Active Directory ;
* un serveur GLPI ;
* un serveur Zabbix.

Les mécanismes de sécurité et de supervision doivent donc être vérifiés sans provoquer d'indisponibilité inutile.

---

## 3. Prérequis

Avant le test :

* disposer d'un accès administrateur aux nœuds ;
* disposer d'un accès SSH fonctionnel ;
* vérifier que le cluster est opérationnel ;
* vérifier que les machines virtuelles critiques sont disponibles ;
* disposer d'un accès à Zabbix ;
* connaître les mesures de durcissement attendues.

---

## 4. Périmètre

Le test porte sur les deux nœuds Proxmox.

Les éléments vérifiés sont :

| Domaine      | Élément contrôlé                             |
| ------------ | -------------------------------------------- |
| Comptes      | comptes administrateurs et privilèges        |
| SSH          | authentification et configuration du service |
| Services     | services actifs et inutiles                  |
| Système      | paramètres de sécurité                       |
| Mises à jour | état des paquets                             |
| Réseau       | interfaces, bridge et exposition             |
| Stockage     | espaces disponibles et état des stockages    |
| Cluster      | quorum et état des nœuds                     |
| Sauvegardes  | présence du stockage distant                 |
| Supervision  | fonctionnement de l'agent Zabbix             |

---

## 5. Vérification des comptes et privilèges

Vérifier les comptes présents sur le système et identifier les comptes disposant de privilèges élevés.

Le résultat doit permettre de distinguer :

* les comptes standards ;
* les comptes administrateurs ;
* les comptes techniques ;
* les comptes inutilisés.

Une attention particulière doit être portée aux comptes disposant de privilèges `sudo`.

### Résultat attendu

Seuls les comptes nécessaires à l'administration disposent de privilèges élevés.

---

## 6. Vérification de SSH

Vérifier la configuration du serveur SSH.

Les points à contrôler comprennent notamment :

* méthode d'authentification ;
* utilisation des clés SSH ;
* accès administrateur direct ;
* restrictions éventuelles ;
* état du service.

### Résultat attendu

La configuration SSH respecte les mesures de durcissement définies dans la documentation du projet.

---

## 7. Vérification des services

Identifier les services actifs sur le nœud.

Les services nécessaires au fonctionnement de Proxmox et du cluster doivent être distingués des services qui ne sont pas nécessaires.

Les services critiques du cluster comprennent notamment :

* `pve-cluster` ;
* `corosync` ;
* `pvedaemon` ;
* `pveproxy` ;
* `pvestatd`.

### Résultat attendu

Les services nécessaires sont actifs et aucun service inutile n'est volontairement exposé.

---

## 8. Vérification des mises à jour

Vérifier l'état des paquets du système et identifier les éventuelles mises à jour disponibles.

L'objectif est de déterminer si le système présente un retard de maintenance susceptible d'augmenter sa surface de vulnérabilité.

### Résultat attendu

Le système est maintenu conformément à la politique de maintenance définie dans le projet.

---

## 9. Vérification du stockage

Contrôler :

* l'espace disponible sur le système ;
* l'espace disponible sur les stockages Proxmox ;
* l'état des volumes ;
* la disponibilité du stockage distant utilisé pour les sauvegardes.

Une saturation du stockage peut provoquer des indisponibilités ou empêcher l'exécution des sauvegardes.

### Résultat attendu

Les stockages sont accessibles et disposent d'un espace suffisant pour assurer leur rôle.

---

## 10. Vérification du cluster

Vérifier :

* le nombre de nœuds ;
* l'état du quorum ;
* le nombre de votes attendus ;
* le nombre de votes disponibles ;
* l'état général du cluster.

### Résultat attendu

Le cluster est dans l'état attendu et dispose du quorum.

---

## 11. Vérification du réseau

Contrôler :

* les interfaces réseau ;
* les bridges ;
* les adresses IP ;
* la passerelle ;
* la résolution DNS ;
* les éventuels mécanismes de bonding.

L'objectif est de vérifier que la configuration réseau correspond à l'architecture documentée.

### Résultat attendu

La connectivité nécessaire au fonctionnement de Proxmox, du cluster, des machines virtuelles et de la supervision est opérationnelle.

---

## 12. Vérification de la supervision

Vérifier que le nœud est correctement supervisé par Zabbix.

Les contrôles doivent notamment couvrir :

* disponibilité de l'agent ;
* état du cluster ;
* services critiques ;
* stockage ;
* état des machines virtuelles ;
* stockage distant ;
* éléments de sécurité prévus dans la supervision.

### Résultat attendu

Les événements importants sont observables depuis la supervision.

---

## 13. Vérification des sauvegardes

Vérifier que le stockage distant utilisé pour les sauvegardes est disponible.

La vérification doit également permettre de confirmer que les sauvegardes planifiées sont effectivement produites et qu'une sauvegarde récente est disponible.

Une sauvegarde considérée comme « terminée » n'est pas suffisante pour démontrer la capacité de restauration.

La capacité de restauration fait l'objet d'un lab distinct.

---

## 14. Analyse des écarts

Tout écart constaté doit être classé selon sa nature :

* configuration incorrecte ;
* configuration manquante ;
* configuration différente de la documentation ;
* service inattendu ;
* problème de supervision ;
* problème de maintenance ;
* problème de sauvegarde.

Pour chaque écart, déterminer :

1. son impact ;
2. son niveau de criticité ;
3. sa cause probable ;
4. l'action corrective ;
5. le moyen de vérifier la correction.

---

## 15. Critères de validation

Le lab est considéré comme réussi lorsque :

* les comptes privilégiés sont maîtrisés ;
* l'accès SSH respecte la configuration attendue ;
* les services nécessaires sont opérationnels ;
* aucune exposition inutile n'est identifiée ;
* le système est maintenu ;
* les stockages sont disponibles ;
* le cluster dispose du quorum ;
* la configuration réseau est cohérente ;
* Zabbix supervise correctement les nœuds ;
* le stockage de sauvegarde est accessible.

Un écart n'entraîne pas nécessairement l'échec global du lab. Il doit être documenté, évalué et traité selon sa criticité.

---

## 16. Retour d'expérience

À l'issue du test, documenter :

* les contrôles réalisés ;
* les anomalies découvertes ;
* les corrections appliquées ;
* les contrôles ayant permis de confirmer les corrections ;
* les éventuelles limites du test.

L'objectif est de transformer le résultat du lab en information exploitable pour la maintenance et l'amélioration continue du laboratoire.

---

## 17. Références

* Documentation officielle Proxmox VE ;
* documentation SSH ;
* ANSSI, recommandations relatives à l'administration sécurisée ;
* SOCLE de Stéphane Robert, lorsque les mesures vérifiées correspondent à ses recommandations techniques d'implémentation ;
* documentation Zabbix pour les éléments de supervision.
