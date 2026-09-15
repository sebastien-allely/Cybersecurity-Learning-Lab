# 06 - Durcissement

| Élément                           | Valeur                                                                                                  |
| --------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `06-Durcissement.md`                                                                                    |
| **Technologie**                   | Debian                                                                                                  |
| **Catégorie**                     | Hardening                                                                                               |
| **Objectif**                      | Définir les mesures permettant de réduire la surface d'attaque et les risques liés aux systèmes Debian. |
| **Auteur**                        | Sébastien Allely                                                                                        |
| **Version**                       | 1.0                                                                                                     |
| **Date de dernière modification** | 02/08/2026                                                                                              |

---

## 1. Objectif

Le durcissement Debian consiste à réduire les possibilités d'exploitation du système tout en conservant les fonctionnalités nécessaires à son rôle.

Il s'appuie sur plusieurs axes :

* réduction de la surface d'attaque ;
* sécurisation des comptes ;
* sécurisation de l'administration ;
* contrôle réseau ;
* protection des fichiers ;
* journalisation ;
* mises à jour ;
* supervision.

---

## 2. Réduction des logiciels inutiles

Les paquets qui ne sont pas nécessaires au rôle du système doivent être identifiés.

La suppression doit être précédée d'une analyse des dépendances.

Il ne faut pas supprimer un paquet système uniquement parce qu'il n'est pas directement utilisé par un administrateur.

---

## 3. Réduction des services

Les services inutiles doivent être désactivés.

Avant toute désactivation :

```bash
systemctl status <service>
```

Puis vérifier les dépendances et l'utilisation réelle du service.

Une fois la décision prise :

```bash
systemctl disable --now <service>
```

La modification doit ensuite être validée.

---

## 4. Sécurisation des comptes

Les comptes inutiles doivent être désactivés ou supprimés selon le contexte.

Les comptes privilégiés doivent être limités.

L'administration quotidienne doit autant que possible utiliser un compte nominatif avec élévation de privilèges contrôlée.

L'utilisation directe du compte `root` doit être limitée aux opérations qui le nécessitent réellement.

---

## 5. Sécurisation de SSH

Lorsque SSH est utilisé, sa configuration doit être durcie.

Les principes comprennent :

* limiter les utilisateurs autorisés ;
* privilégier l'authentification par clé ;
* désactiver l'authentification par mot de passe lorsque cela est compatible avec le contexte ;
* limiter l'accès réseau ;
* éviter l'utilisation directe de `root` ;
* surveiller les tentatives d'accès.

Avant de recharger SSH, la configuration doit être vérifiée :

```bash
sshd -t
```

Une erreur de configuration SSH peut provoquer une perte d'accès administratif. Une session de secours doit donc être disponible avant toute modification importante.

---

## 6. Contrôle des permissions

Les fichiers sensibles doivent être accessibles uniquement aux utilisateurs et services nécessaires.

Une attention particulière doit être portée aux :

```text
/etc/shadow
/etc/gshadow
/etc/ssh/
/etc/sudoers
/etc/sudoers.d/
```

Les fichiers contenant des secrets ou des clés privées doivent bénéficier de permissions adaptées à leur usage.

---

## 7. Réduction de l'exposition réseau

Les services doivent être exposés uniquement sur les interfaces nécessaires.

Le système doit également limiter les communications entrantes et sortantes lorsque le contexte le permet.

La mise en œuvre d'un filtrage réseau doit tenir compte :

* des services nécessaires ;
* de la supervision ;
* de l'administration ;
* des sauvegardes ;
* des dépendances du système.

Une règle de filtrage trop restrictive peut rendre le système indisponible.

---

## 8. Journalisation

Les journaux constituent une source essentielle pour :

* détecter une anomalie ;
* analyser une tentative d'intrusion ;
* comprendre une panne ;
* réaliser une investigation.

Les journaux doivent être conservés suffisamment longtemps pour permettre leur exploitation.

La capacité de stockage doit également être surveillée afin d'éviter qu'un remplissage du système de fichiers ne provoque une indisponibilité.

---

## 9. Intégrité

Les fichiers critiques doivent pouvoir faire l'objet d'un contrôle d'intégrité lorsque le niveau de risque le justifie.

Les modifications inattendues de :

* fichiers système ;
* fichiers de configuration ;
* scripts ;
* fichiers exécutables ;

peuvent constituer un indicateur de compromission.

Dans le laboratoire, ces contrôles peuvent être associés aux mécanismes de supervision existants.

---

## 10. Mises à jour

Le système doit bénéficier des mises à jour de sécurité Debian.

Une politique de mise à jour doit prendre en compte :

* criticité du système ;
* disponibilité ;
* dépendances ;
* possibilité de restauration ;
* tests préalables lorsque nécessaire.

Le maintien en condition de sécurité est un processus continu.

---

## 11. Protection et sauvegarde des configurations

Les fichiers de configuration importants doivent être protégés et sauvegardés.

Une modification de configuration ne doit pas être considérée comme réversible uniquement parce qu'elle est documentée.

Une copie exploitable doit être disponible lorsque le fichier est critique pour le fonctionnement du service.

Les sauvegardes doivent elles-mêmes être protégées.

---

## 12. Supervision

Le durcissement doit être associé à une capacité de surveillance.

Les éléments importants à superviser comprennent notamment :

* disponibilité du système ;
* utilisation CPU ;
* mémoire ;
* espace disque ;
* services critiques ;
* erreurs ;
* événements de sécurité ;
* état des mécanismes de protection.

La supervision ne remplace pas le durcissement. Elle permet de détecter lorsqu'une mesure préventive n'a pas suffi.

---

## 13. Validation

Après application des mesures, vérifier notamment :

```bash
systemctl --failed
```

```bash
ss -tulpen
```

```bash
journalctl -p warning..alert
```

L'objectif est de confirmer simultanément :

* la réduction de l'exposition ;
* le fonctionnement des services nécessaires ;
* l'absence d'erreurs critiques ;
* la capacité d'administration ;
* la continuité de la supervision.

---

## 14. Principe de réversibilité

Chaque modification importante doit pouvoir être annulée.

Avant une modification de configuration critique :

1. sauvegarder le fichier ;
2. modifier ;
3. vérifier la syntaxe ;
4. appliquer ;
5. contrôler le fonctionnement ;
6. conserver la possibilité de restaurer l'état précédent.

Le durcissement doit améliorer la sécurité sans transformer l'administration du système en opération irréversible.
