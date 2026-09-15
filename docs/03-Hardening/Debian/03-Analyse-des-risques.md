# 03 - Analyse des risques

| Élément                           | Valeur                                                                                                 |
| --------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `03-Analyse-des-risques.md`                                                                            |
| **Technologie**                   | Debian                                                                                                 |
| **Catégorie**                     | Hardening                                                                                              |
| **Objectif**                      | Analyser les risques associés aux systèmes Debian et déterminer les mesures permettant de les réduire. |
| **Auteur**                        | Sébastien Allely                                                                                       |
| **Version**                       | 1.0                                                                                                    |
| **Date de dernière modification** | 02/08/2026                                                                                             |

---

## 1. Objectif

L'analyse des risques permet de déterminer quelles mesures de durcissement doivent être prioritaires.

Le principe retenu dans le laboratoire consiste à ne pas appliquer les mesures de sécurité indépendamment du contexte.

Le risque dépend notamment :

* de la valeur de l'actif ;
* de son exposition ;
* des données traitées ;
* des privilèges détenus ;
* des dépendances ;
* des conséquences d'une compromission.

---

## 2. Actifs concernés

Pour un système Debian, les actifs à considérer comprennent notamment :

| Actif                     | Risque principal                         |
| ------------------------- | ---------------------------------------- |
| Système d'exploitation    | Compromission ou élévation de privilèges |
| Comptes utilisateurs      | Accès non autorisé                       |
| Comptes privilégiés       | Prise de contrôle du système             |
| Services réseau           | Exploitation d'une vulnérabilité         |
| Fichiers de configuration | Modification ou divulgation              |
| Secrets                   | Compromission de comptes ou services     |
| Données applicatives      | Vol, modification ou destruction         |
| Journaux                  | Perte de capacité de détection           |
| Sauvegardes               | Perte de capacité de restauration        |
| Interfaces réseau         | Exposition involontaire                  |

---

## 3. Menaces principales

Les principales menaces prises en compte sont :

### 3.1 Accès non autorisé

Un attaquant peut tenter d'obtenir un accès au système par :

* un service réseau exposé ;
* des identifiants compromis ;
* une authentification faible ;
* une mauvaise configuration des permissions.

### 3.2 Exploitation d'une vulnérabilité

Une vulnérabilité affectant :

* le noyau ;
* un paquet ;
* un service ;
* une bibliothèque ;
* une application ;

peut permettre une compromission du système.

### 3.3 Élévation de privilèges

Après obtention d'un accès initial, un attaquant peut rechercher un moyen d'obtenir des privilèges supplémentaires.

Les configurations de comptes, les permissions de fichiers, les services et les composants logiciels doivent donc être considérés.

### 3.4 Mouvement latéral

Un système compromis peut servir de point d'appui pour atteindre d'autres composants du laboratoire.

La segmentation réseau et la limitation des communications permettent de réduire ce risque.

### 3.5 Persistance

Un attaquant ayant obtenu un accès peut chercher à maintenir sa présence au moyen :

* de comptes ;
* de services ;
* de tâches planifiées ;
* de modifications de configuration ;
* de mécanismes de démarrage.

La journalisation et la vérification de l'intégrité contribuent à détecter ces modifications.

---

## 4. Évaluation du risque

L'analyse peut être structurée autour de deux dimensions :

* probabilité d'occurrence ;
* impact.

Une représentation simple peut être utilisée :

| Probabilité | Impact | Niveau de risque |
| ----------- | ------ | ---------------- |
| Faible      | Faible | Faible           |
| Faible      | Fort   | Modéré           |
| Forte       | Faible | Modéré           |
| Forte       | Fort   | Élevé            |

Cette matrice doit être adaptée au contexte réel de l'actif.

---

## 5. Mesures de réduction

Les mesures de réduction des risques peuvent être regroupées par domaine.

### Surface d'attaque

* supprimer les paquets inutiles ;
* désactiver les services inutiles ;
* limiter les ports exposés.

### Authentification

* limiter les comptes ;
* utiliser des mécanismes d'authentification robustes ;
* limiter les privilèges ;
* contrôler l'administration distante.

### Réseau

* limiter les flux ;
* filtrer les connexions ;
* éviter l'exposition inutile de services ;
* séparer les composants lorsque cela est possible.

### Système

* maintenir Debian à jour ;
* contrôler les permissions ;
* protéger les fichiers de configuration ;
* limiter les privilèges des services.

### Détection

* conserver les journaux nécessaires ;
* superviser les services ;
* surveiller les événements importants ;
* détecter les modifications anormales.

### Résilience

* protéger les sauvegardes ;
* sauvegarder les configurations importantes ;
* vérifier périodiquement la capacité de restauration.

---

## 6. Risque résiduel

Le durcissement ne permet pas de supprimer totalement le risque.

Après application des mesures, il reste notamment :

* les vulnérabilités inconnues ;
* les erreurs de configuration ;
* les identifiants compromis ;
* les vulnérabilités des applications ;
* les erreurs humaines ;
* les dépendances externes.

Le risque résiduel doit donc être accepté explicitement ou faire l'objet de mesures complémentaires.

---

## 7. Priorisation

Les premières mesures doivent cibler les risques présentant le meilleur rapport entre réduction du risque et effort de mise en œuvre.

L'ordre de traitement recommandé est :

1. supprimer les services inutiles ;
2. sécuriser les accès administratifs ;
3. réduire l'exposition réseau ;
4. maintenir les logiciels à jour ;
5. renforcer les permissions ;
6. protéger les fichiers de configuration ;
7. mettre en place la journalisation ;
8. assurer la supervision ;
9. vérifier les sauvegardes ;
10. contrôler régulièrement la configuration.

---

## 8. Conclusion

L'analyse des risques permet d'éviter un durcissement purement mécanique.

Chaque mesure appliquée à Debian doit répondre à une question simple :

> Quel risque cette mesure réduit-elle et quel impact opérationnel introduit-elle ?

Cette approche permet de conserver un équilibre entre sécurité, disponibilité, maintenabilité et capacité d'administration du système.
