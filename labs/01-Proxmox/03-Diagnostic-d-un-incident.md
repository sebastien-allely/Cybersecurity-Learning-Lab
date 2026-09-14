# Diagnostic d'un incident Proxmox

**Nom du document** : Diagnostic d'un incident Proxmox
**Technologie** : Proxmox VE
**Catégorie** : Lab pratique
**Objectif** : Diagnostiquer méthodiquement un incident affectant un nœud, le cluster, une machine virtuelle ou un service Proxmox.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif du lab

Ce lab consiste à analyser un incident affectant l'infrastructure Proxmox et à déterminer sa cause avant d'appliquer une action corrective.

L'objectif est de mettre en œuvre une démarche de diagnostic reproductible :

1. qualifier l'incident ;
2. identifier les composants affectés ;
3. collecter les informations techniques ;
4. formuler des hypothèses ;
5. vérifier ces hypothèses ;
6. appliquer une correction ;
7. valider le retour à la normale ;
8. documenter l'incident.

Le diagnostic doit privilégier la collecte de preuves avant toute modification de configuration.

---

## 2. Scénarios étudiés

Le lab peut être réalisé à partir de plusieurs situations :

* perte d'accès à l'interface d'administration ;
* nœud Proxmox indisponible ;
* perte du quorum du cluster ;
* service Proxmox arrêté ;
* machine virtuelle inaccessible ;
* problème de stockage ;
* problème réseau ;
* comportement anormal d'une machine virtuelle.

Le scénario utilisé doit être documenté avant le début du diagnostic.

---

## 3. Qualification de l'incident

Déterminer :

* le symptôme observé ;
* la date et l'heure de début ;
* les systèmes concernés ;
* les utilisateurs ou services impactés ;
* le niveau de criticité ;
* les dernières modifications connues.

Ne pas modifier immédiatement le système afin de préserver les éléments nécessaires à l'analyse.

---

## 4. Vérification de l'état du cluster

Contrôler :

* l'état du cluster ;
* le quorum ;
* le nombre de nœuds attendus ;
* le nombre de nœuds disponibles ;
* l'état de Corosync.

Exemple :

```bash
pvecm status
```

Cette commande permet de vérifier l'état du cluster et notamment son quorum.

---

## 5. Vérification des services

Contrôler les principaux services Proxmox :

```bash
systemctl status pve-cluster
```

Cette commande permet de vérifier l'état du service responsable de la configuration distribuée du cluster.

```bash
systemctl status corosync
```

Cette commande permet de vérifier le fonctionnement de la communication de cluster.

```bash
systemctl status pvedaemon
```

Cette commande permet de vérifier le service fournissant les opérations d'administration Proxmox.

```bash
systemctl status pveproxy
```

Cette commande permet de vérifier le service fournissant l'interface d'administration Web et l'API Proxmox.

---

## 6. Vérification des machines virtuelles

Identifier les machines virtuelles concernées et vérifier leur état.

Exemple :

```bash
qm list
```

Cette commande affiche les machines virtuelles présentes sur le nœud et leur état d'exécution.

Pour examiner une machine virtuelle précise :

```bash
qm status <VMID>
```

Cette commande permet de vérifier l'état d'une machine virtuelle identifiée par son VMID.

---

## 7. Vérification du stockage

Contrôler les espaces de stockage disponibles :

```bash
pvesm status
```

Cette commande permet de vérifier l'état des stockages configurés dans Proxmox.

Contrôler également l'espace disque du système :

```bash
df -h
```

Cette commande permet d'identifier une éventuelle saturation des systèmes de fichiers.

---

## 8. Vérification du réseau

Contrôler :

* les interfaces réseau ;
* les bridges ;
* les adresses IP ;
* les routes ;
* la connectivité entre les nœuds.

Exemples :

```bash
ip addr
```

Cette commande affiche les interfaces et leurs adresses IP.

```bash
ip route
```

Cette commande affiche la table de routage du système.

Tester ensuite la connectivité vers le nœud ou service concerné.

---

## 9. Analyse des hypothèses

Pour chaque hypothèse, documenter :

| Hypothèse             | Preuve recherchée  | Résultat | Conclusion |
| --------------------- | ------------------ | -------- | ---------- |
| Service arrêté        | État systemd       |          |            |
| Perte réseau          | Connectivité       |          |            |
| Perte de quorum       | `pvecm status`     |          |            |
| Stockage indisponible | `pvesm status`     |          |            |
| Saturation disque     | `df -h`            |          |            |
| Problème VM           | `qm status` / logs |          |            |

Une hypothèse ne doit être considérée comme confirmée qu'après observation d'un élément technique permettant de l'étayer.

---

## 10. Correction

Une fois la cause identifiée :

1. définir l'action corrective ;
2. évaluer son impact ;
3. appliquer la correction ;
4. contrôler immédiatement le résultat ;
5. vérifier les services dépendants.

Toute modification importante doit être documentée.

---

## 11. Validation

Après correction, vérifier :

* l'accessibilité du nœud ;
* l'état du cluster ;
* le quorum ;
* l'état des services ;
* l'état des machines virtuelles ;
* l'état du stockage ;
* la supervision Zabbix.

Le retour à la normale doit être démontré par des contrôles techniques.

---

## 12. Approche Blue Team

La démarche Blue Team consiste à :

* détecter l'anomalie ;
* préserver les informations utiles ;
* qualifier l'incident ;
* rechercher les indicateurs techniques ;
* identifier la cause ;
* corriger ;
* surveiller le retour à la normale ;
* documenter le retour d'expérience.

---

## 13. Approche Red Team

Dans un environnement de laboratoire, le scénario peut être déclenché volontairement afin d'observer les conséquences d'une défaillance.

L'objectif n'est pas de dégrader inutilement l'infrastructure mais de reproduire un événement contrôlé permettant de vérifier :

* la capacité de détection ;
* la capacité de diagnostic ;
* la qualité de la journalisation ;
* l'efficacité de la supervision ;
* la procédure de restauration.

---

## 14. Compte rendu

Le compte rendu doit contenir :

* description de l'incident ;
* impact ;
* chronologie ;
* preuves collectées ;
* hypothèses étudiées ;
* cause identifiée ;
* actions réalisées ;
* résultat ;
* mesures préventives proposées.

---

## 15. Critères de réussite

Le lab est considéré comme réussi lorsque l'apprenant est capable de :

* qualifier l'incident ;
* identifier les composants concernés ;
* collecter des preuves ;
* formuler et tester des hypothèses ;
* déterminer la cause ;
* appliquer une correction maîtrisée ;
* valider le retour à la normale ;
* produire un compte rendu technique.

---

## 16. Références

* Documentation officielle Proxmox VE
* ANSSI
* NIST
* MITRE ATT&CK
* SOCLE de Stéphane Robert, lorsqu'une mesure technique d'implémentation ou de durcissement est concernée
