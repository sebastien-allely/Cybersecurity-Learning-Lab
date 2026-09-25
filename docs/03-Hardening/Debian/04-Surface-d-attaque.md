# 04 - Surface d'attaque

| Élément                           | Valeur                                                                                                                       |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `04-Surface-d-attaque.md`                                                                                                    |
| **Technologie**                   | Debian                                                                                                                       |
| **Catégorie**                     | Hardening                                                                                                                    |
| **Objectif**                      | Identifier les principaux éléments constituant la surface d'attaque d'un système Debian et définir les moyens de la réduire. |
| **Auteur**                        | Sébastien Allely                                                                                                             |
| **Version**                       | 1.0                                                                                                                          |
| **Date de dernière modification** | 02/08/2026                                                                                                                   |

---

## 1. Définition

La surface d'attaque représente l'ensemble des éléments qu'un attaquant pourrait exploiter pour obtenir un accès au système, exécuter du code, augmenter ses privilèges ou accéder à des données.

Sur Debian, cette surface comprend notamment :

* les services réseau ;
* les ports ouverts ;
* les logiciels installés ;
* les comptes utilisateurs ;
* les mécanismes d'authentification ;
* les interfaces réseau ;
* les permissions ;
* les tâches planifiées ;
* les fichiers de configuration ;
* les mécanismes d'administration ;
* les composants du système.

Le principe de réduction de la surface d'attaque consiste à supprimer ou limiter tout élément qui n'est pas nécessaire au fonctionnement du système.

---

## 2. Services réseau

Les services réseau constituent l'une des principales surfaces d'exposition.

Une première analyse peut être réalisée avec :

```bash
ss -tulpen
```

Cette commande permet notamment d'identifier :

* les ports en écoute ;
* les protocoles utilisés ;
* les processus associés ;
* les adresses d'écoute.

Un service écoutant sur toutes les interfaces doit faire l'objet d'une attention particulière.

Lorsqu'un service n'a besoin d'être accessible que localement, son écoute doit être limitée à l'interface appropriée.

---

## 3. Services système

Les services actifs doivent être comparés au rôle réel du système.

Lister les services actifs :

```bash
systemctl list-units --type=service --state=running
```

Identifier les services activés au démarrage :

```bash
systemctl list-unit-files --type=service --state=enabled
```

Lorsqu'un service est inutile, il convient d'abord d'identifier son origine et ses dépendances avant de le désactiver.

La suppression d'un service ne doit jamais être réalisée uniquement parce qu'il semble inutile à première vue.

---

## 4. Logiciels installés

Chaque paquet installé augmente potentiellement la surface d'attaque.

Cela ne signifie pas qu'il faut rechercher une installation minimale à tout prix.

L'objectif est plutôt de maintenir une correspondance entre :

**paquets installés → services nécessaires → rôle du système.**

L'inventaire peut être réalisé avec :

```bash
dpkg-query -W
```

Les paquets inutiles doivent être identifiés puis supprimés lorsque leur suppression ne compromet pas le fonctionnement du système.

---

## 5. Ports exposés

Les ports ouverts doivent être documentés.

Pour chaque port, il convient de déterminer :

* quel service l'utilise ;
* pourquoi il est nécessaire ;
* quelles sources doivent pouvoir y accéder ;
* s'il doit être accessible localement ou sur le réseau ;
* si son exposition peut être réduite.

Un port ouvert sans justification constitue une dette de sécurité.

---

## 6. Comptes utilisateurs

Les comptes constituent une autre composante importante de la surface d'attaque.

Il convient d'identifier :

* les comptes humains ;
* les comptes système ;
* les comptes de service ;
* les comptes privilégiés ;
* les comptes inutilisés.

Les comptes inutilisés doivent être désactivés ou supprimés lorsque cela est possible.

Il faut cependant éviter de supprimer arbitrairement les comptes système nécessaires au fonctionnement de Debian ou d'un service.

---

## 7. Administration distante

SSH représente une surface d'attaque particulièrement importante sur les systèmes administrés à distance.

Les mesures de réduction comprennent notamment :

* limiter les sources autorisées ;
* utiliser une authentification forte ;
* éviter l'authentification par mot de passe lorsque le contexte le permet ;
* limiter les comptes autorisés ;
* limiter les privilèges ;
* surveiller les tentatives d'authentification.

La configuration SSH doit être adaptée au rôle du système et à la méthode d'administration utilisée dans le laboratoire.

---

## 8. Permissions et privilèges

Une mauvaise gestion des permissions peut permettre à un utilisateur ou à un processus de modifier des fichiers sensibles.

Les éléments particulièrement importants comprennent :

* fichiers système ;
* fichiers de configuration ;
* clés privées ;
* secrets ;
* scripts exécutés avec des privilèges élevés ;
* répertoires contenant des données sensibles.

Le principe du moindre privilège doit être appliqué aux utilisateurs comme aux services.

---

## 9. Tâches planifiées

Les tâches planifiées peuvent être utilisées légitimement pour la maintenance mais également servir de mécanisme de persistance.

Il faut donc vérifier :

```bash
crontab -l
```

ainsi que les mécanismes système associés à cron et systemd.

Les tâches doivent être documentées lorsqu'elles jouent un rôle important dans le fonctionnement du système.

---

## 10. Fichiers de configuration

Les fichiers de configuration doivent être considérés comme des actifs sensibles.

Ils peuvent contenir des informations permettant :

* de modifier le comportement du service ;
* d'accéder à des données ;
* d'obtenir des privilèges ;
* de se connecter à une autre infrastructure.

Les fichiers de configuration importants doivent donc être :

* protégés contre les modifications non autorisées ;
* accessibles uniquement aux utilisateurs ou services nécessaires ;
* sauvegardés ;
* surveillés lorsque leur intégrité est critique.

---

## 11. Réduction de la surface d'attaque

La réduction doit suivre une logique simple :

1. identifier ;
2. justifier ;
3. supprimer lorsque possible ;
4. restreindre lorsque la suppression est impossible ;
5. surveiller ;
6. documenter.

Cette démarche évite de transformer le durcissement en une succession de modifications non maîtrisées.

---

## 12. Validation

Après chaque modification importante, le fonctionnement du système doit être vérifié.

Il faut notamment contrôler :

```bash
systemctl --failed
```

puis :

```bash
ss -tulpen
```

et vérifier les journaux pertinents.

Une réduction de surface d'attaque qui provoque l'indisponibilité d'un service nécessaire n'est pas une mesure de sécurité correctement implémentée.
