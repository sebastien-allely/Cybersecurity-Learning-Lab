# 01 - Justification de l'outil

| Élément                           | Valeur                                                                                                                                                            |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `01-Justification-de-l-outil.md`                                                                                                                                  |
| **Technologie**                   | Proxmox VE                                                                                                                                                        |
| **Catégorie**                     | Architecture                                                                                                                                                      |
| **Objectif**                      | Justifier le choix de Proxmox VE comme solution de virtualisation du laboratoire et présenter son rôle dans l'architecture globale du Cybersecurity-Learning-Lab. |
| **Auteur**                        | Sébastien Allely                                                                                                                                                  |
| **Version**                       | 1.0                                                                                                                                                               |
| **Date de dernière modification** | 02/08/2026                                                                                                                                                        |

---

## 1. Présentation

Proxmox VE est la plateforme de virtualisation retenue pour le **Cybersecurity-Learning-Lab**.

Elle constitue la couche d'infrastructure permettant d'héberger les différentes machines virtuelles nécessaires au laboratoire de cybersécurité.

Le choix de Proxmox VE s'inscrit dans une volonté de disposer d'une infrastructure :

* reproductible ;
* administrable ;
* adaptée à l'expérimentation ;
* suffisamment représentative d'une infrastructure professionnelle ;
* permettant d'isoler les différents systèmes du laboratoire.

---

## 2. Rôle dans le laboratoire

Proxmox VE constitue la couche située entre l'infrastructure physique et les systèmes virtualisés.

L'architecture peut être représentée de manière simplifiée ainsi :

```text
Infrastructure physique
        │
        ▼
   Proxmox VE
        │
        ├── VM Active Directory
        ├── VM Zabbix
        ├── VM GLPI
        ├── VM Windows
        └── autres systèmes du laboratoire
```

Cette organisation permet de disposer de plusieurs systèmes indépendants tout en les hébergeant sur une infrastructure physique limitée.

---

## 3. Justification du choix

Proxmox VE a été retenu notamment pour les raisons suivantes :

* solution libre et open source ;
* basée sur Debian ;
* prise en charge de la virtualisation KVM ;
* prise en charge des conteneurs LXC ;
* administration centralisée ;
* gestion des machines virtuelles ;
* gestion du stockage ;
* gestion du réseau ;
* fonctionnalités de sauvegarde ;
* possibilité de constituer un cluster.

Ces caractéristiques correspondent aux besoins du laboratoire.

---

## 4. Intérêt pédagogique

Le choix de Proxmox VE permet également de reproduire des problématiques rencontrées dans des infrastructures professionnelles.

Le laboratoire permet notamment d'étudier :

* la virtualisation ;
* la segmentation ;
* le stockage ;
* les sauvegardes ;
* la supervision ;
* la disponibilité ;
* le durcissement de l'hyperviseur ;
* la gestion des accès d'administration ;
* les conséquences d'une compromission de l'infrastructure.

Proxmox VE constitue ainsi lui-même un composant de sécurité à protéger et non simplement un outil permettant d'exécuter des machines virtuelles.

---

## 5. Positionnement de sécurité

L'hyperviseur possède un niveau de criticité supérieur à celui d'une machine virtuelle isolée.

Une compromission de Proxmox VE pourrait potentiellement permettre à un attaquant d'accéder à plusieurs systèmes virtualisés.

La sécurité de l'hyperviseur doit donc notamment prendre en compte :

* les comptes d'administration ;
* l'authentification ;
* l'exposition des interfaces d'administration ;
* les services actifs ;
* le réseau ;
* le stockage ;
* les sauvegardes ;
* la journalisation ;
* la supervision ;
* les mises à jour.

Ces éléments sont détaillés dans les documents consacrés à l'architecture et au hardening de Proxmox VE.

---

## 6. Relation avec Debian

Proxmox VE s'appuie sur Debian.

Il existe donc une séparation documentaire volontaire :

**Debian** documente le socle système.

**Proxmox VE** documente la couche de virtualisation et les fonctions propres à l'hyperviseur.

Cette séparation permet d'éviter de mélanger les mesures de sécurité propres au système d'exploitation avec celles propres à la plateforme de virtualisation.

---

## 7. Sauvegarde et résilience

La plateforme doit également permettre de mettre en œuvre une stratégie de sauvegarde des machines virtuelles.

La sauvegarde constitue un élément essentiel du laboratoire car elle permet :

* de restaurer une machine après une erreur ;
* de revenir à un état connu ;
* de faciliter les expérimentations ;
* de limiter l'impact d'une mauvaise configuration ;
* de disposer d'un mécanisme de récupération après incident.

Les sauvegardes ne doivent toutefois pas être considérées comme une protection suffisante contre une compromission de l'hyperviseur.

---

## 8. Limites

Le choix de Proxmox VE ne supprime pas les contraintes liées à l'infrastructure physique.

Les capacités du laboratoire restent notamment limitées par :

* les ressources CPU ;
* la mémoire disponible ;
* le stockage ;
* les interfaces réseau ;
* les capacités de segmentation de l'équipement réseau utilisé actuellement.

Ces contraintes doivent être prises en compte dans les décisions d'architecture.

---

## 9. Conclusion

Proxmox VE constitue la couche de virtualisation du **Cybersecurity-Learning-Lab**.

Son choix permet de disposer d'une plateforme suffisamment complète pour héberger les différents composants du laboratoire tout en offrant un environnement pertinent pour étudier les problématiques d'administration, de disponibilité, de sauvegarde et de cybersécurité.

Compte tenu de son rôle central, Proxmox VE doit être considéré comme un **actif critique de l'infrastructure** et bénéficier de mesures de protection, de supervision et de sauvegarde adaptées.
