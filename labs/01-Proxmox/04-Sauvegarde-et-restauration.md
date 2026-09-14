# Sauvegarde et restauration Proxmox

**Nom du document** : Sauvegarde et restauration Proxmox
**Technologie** : Proxmox VE
**Catégorie** : Lab pratique
**Objectif** : Mettre en œuvre, vérifier et tester une procédure de sauvegarde et de restauration d'une machine virtuelle Proxmox.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif du lab

Ce lab permet de mettre en pratique une stratégie de sauvegarde de machines virtuelles et de vérifier qu'une sauvegarde peut réellement être utilisée pour restaurer un service.

Une sauvegarde n'est considérée comme exploitable qu'après vérification de sa capacité à être restaurée.

---

## 2. Prérequis

L'apprenant doit disposer :

* d'un nœud Proxmox fonctionnel ;
* d'une machine virtuelle de laboratoire ;
* d'un stockage de sauvegarde disponible ;
* d'un espace suffisant sur le stockage cible.

---

## 3. Identification de la machine virtuelle

Identifier :

* le VMID ;
* le nom de la machine virtuelle ;
* son rôle ;
* son stockage ;
* ses disques virtuels ;
* son niveau de criticité.

Exemple :

```bash
qm list
```

Cette commande permet d'identifier les machines virtuelles disponibles et leur état.

---

## 4. Vérification du stockage de sauvegarde

Contrôler les stockages Proxmox :

```bash
pvesm status
```

Cette commande permet de vérifier que le stockage destiné aux sauvegardes est disponible.

Vérifier également l'espace disponible.

---

## 5. Réalisation de la sauvegarde

Effectuer une sauvegarde de la machine virtuelle en utilisant le mécanisme de sauvegarde Proxmox.

Documenter :

* la date ;
* l'heure ;
* la machine virtuelle ;
* le stockage cible ;
* le mode de sauvegarde ;
* le résultat ;
* la taille de la sauvegarde.

---

## 6. Vérification de la sauvegarde

Une sauvegarde réussie doit être contrôlée.

Vérifier :

* son existence ;
* sa taille ;
* son horodatage ;
* son intégrité ;
* l'absence d'erreur dans les journaux de sauvegarde.

L'objectif est de distinguer une sauvegarde simplement créée d'une sauvegarde réellement exploitable.

---

## 7. Test de restauration

Effectuer la restauration dans un environnement contrôlé.

Documenter :

* la sauvegarde utilisée ;
* la date de la sauvegarde ;
* le VMID de destination ;
* le stockage utilisé ;
* les éventuelles modifications nécessaires.

---

## 8. Validation de la restauration

Après restauration, vérifier :

* le démarrage de la machine virtuelle ;
* le système de fichiers ;
* les services ;
* le réseau ;
* les données attendues ;
* la supervision.

La restauration est considérée comme valide uniquement lorsque le service attendu est opérationnel.

---

## 9. RPO et RTO

Le **RPO** (*Recovery Point Objective*) correspond à la quantité maximale de données que l'organisation accepte de perdre.

Le **RTO** (*Recovery Time Objective*) correspond au délai maximal accepté pour restaurer le service.

Mesurer le temps nécessaire entre :

1. le début de la restauration ;
2. la remise en fonctionnement du service.

Comparer le résultat au RTO défini.

---

## 10. Analyse

Répondre aux questions suivantes :

* La sauvegarde était-elle disponible ?
* Était-elle exploitable ?
* Les données restaurées étaient-elles cohérentes ?
* Le RPO est-il respecté ?
* Le RTO est-il respecté ?
* Existe-t-il un point unique de défaillance ?
* La procédure de restauration est-elle suffisamment documentée ?

---

## 11. Approche Blue Team

La Blue Team doit garantir :

* la disponibilité des sauvegardes ;
* leur supervision ;
* leur protection ;
* leur vérification ;
* la documentation de la restauration ;
* la capacité à restaurer dans les délais prévus.

---

## 12. Approche Red Team

Un scénario contrôlé peut simuler :

* la perte d'une machine virtuelle ;
* la corruption d'une machine virtuelle ;
* la perte d'un stockage ;
* l'indisponibilité du service.

L'objectif est de vérifier si la stratégie de sauvegarde permet effectivement de revenir à un état fonctionnel.

---

## 13. Compte rendu

Documenter :

* sauvegarde utilisée ;
* heure de début ;
* heure de fin ;
* résultat ;
* erreurs éventuelles ;
* durée de restauration ;
* état du service après restauration ;
* RPO constaté ;
* RTO constaté ;
* actions d'amélioration.

---

## 14. Critères de réussite

Le lab est réussi lorsque l'apprenant est capable de :

* créer une sauvegarde ;
* vérifier son existence ;
* effectuer une restauration ;
* valider le service restauré ;
* mesurer le RTO ;
* déterminer le RPO ;
* identifier les limites de la stratégie de sauvegarde.

---

## 15. Références

* Documentation officielle Proxmox VE
* ANSSI
* NIST
* SOCLE de Stéphane Robert lorsqu'une mesure technique d'implémentation est utilisée
