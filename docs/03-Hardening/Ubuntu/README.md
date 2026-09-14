# Hardening Ubuntu

| Élément                           | Valeur                                                                                                |
| --------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                           |
| **Technologie**                   | Ubuntu                                                                                                |
| **Catégorie**                     | Hardening                                                                                             |
| **Objectif**                      | Présenter le périmètre et les principes de durcissement appliqués aux systèmes Ubuntu du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                      |
| **Version**                       | 1.0                                                                                                   |
| **Date de dernière modification** | 02/08/2026                                                                                            |

---

## 1. Présentation

Ce dossier regroupe les mesures de durcissement applicables aux systèmes **Ubuntu** utilisés dans le laboratoire.

Ubuntu constitue notamment le socle de certaines machines virtuelles du laboratoire, dont la VM utilisée pour **GLPI**.

Le durcissement doit être adapté au rôle réel de chaque système et ne doit pas être appliqué comme une configuration universelle.

---

## 2. Objectifs

Le durcissement vise principalement à :

* réduire la surface d'attaque ;
* limiter les privilèges ;
* sécuriser l'administration ;
* réduire l'exposition réseau ;
* protéger les fichiers de configuration ;
* assurer la journalisation ;
* maintenir le système à jour ;
* permettre la détection des anomalies ;
* conserver la capacité de restauration.

---

## 3. Méthode

Les mesures sont définies selon la démarche du référentiel :

**identifier → analyser → réduire → contrôler → superviser → maintenir.**

Chaque mesure doit être évaluée selon :

* le rôle du système ;
* les services nécessaires ;
* son exposition ;
* les dépendances ;
* les risques associés.

---

## 4. Cohérence avec Debian

Ubuntu étant basé sur Debian, plusieurs principes d'administration et de sécurité sont communs aux deux environnements.

Cependant, les recommandations doivent toujours être vérifiées contre :

* la version Ubuntu utilisée ;
* sa documentation officielle ;
* les mécanismes propres à Ubuntu ;
* les paquets effectivement installés ;
* le rôle du système.

Une procédure Debian ne doit donc pas être transposée automatiquement à Ubuntu.

---

## 5. Documentation

Les documents de ce dossier décrivent les principes et contrôles nécessaires au durcissement.

Les configurations réellement appliquées au laboratoire doivent rester cohérentes avec l'architecture documentée dans le référentiel.
