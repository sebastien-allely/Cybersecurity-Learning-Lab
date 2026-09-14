# 02 - Identification des actifs

| Élément                           | Valeur                                                                                               |
| --------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `02-Identification-des-actifs.md`                                                                    |
| **Technologie**                   | Debian                                                                                               |
| **Catégorie**                     | Hardening                                                                                            |
| **Objectif**                      | Identifier les actifs Debian concernés par les mesures de sécurité et leur rôle dans le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                     |
| **Version**                       | 1.0                                                                                                  |
| **Date de dernière modification** | 02/08/2026                                                                                           |

---

## 1. Objectif

Avant d'appliquer une mesure de durcissement, il est nécessaire de connaître précisément le système concerné, son rôle et les fonctions qu'il fournit.

Le durcissement d'un système Debian doit être adapté à son usage. Une configuration applicable à un serveur générique n'est pas nécessairement adaptée à un système hébergeant une fonction d'infrastructure particulière.

---

## 2. Informations à identifier

Pour chaque système Debian, les informations suivantes doivent être collectées.

| Élément           | Description                                       |
| ----------------- | ------------------------------------------------- |
| Nom d'hôte        | Identifiant du système dans le laboratoire        |
| Adresse IP        | Adresse utilisée pour les communications réseau   |
| Version Debian    | Version majeure du système                        |
| Version du noyau  | Version actuellement utilisée                     |
| Rôle              | Fonction principale du système                    |
| Services          | Services réseau et locaux actifs                  |
| Paquets           | Logiciels installés nécessaires au fonctionnement |
| Comptes           | Comptes locaux et comptes privilégiés             |
| Interfaces réseau | Interfaces utilisées par le système               |
| Stockage          | Volumes et systèmes de fichiers utilisés          |
| Supervision       | Mécanismes de surveillance associés               |
| Sauvegarde        | Données et configurations sauvegardées            |

---

## 3. Identification du rôle

Le rôle du système constitue l'information la plus importante avant toute modification.

Un système Debian peut notamment être utilisé comme :

* serveur d'infrastructure ;
* serveur applicatif ;
* serveur de supervision ;
* serveur hébergeant une base de données ;
* système utilisé comme socle d'une autre solution ;
* système de test ou d'expérimentation.

Le rôle doit être documenté avant de décider qu'un service est inutile.

---

## 4. Services actifs

Les services actifs doivent être identifiés.

Une attention particulière doit être portée aux services accessibles depuis le réseau.

Pour effectuer une première analyse :

```bash
systemctl list-units --type=service --state=running
```

Les services activés au démarrage peuvent être examinés avec :

```bash
systemctl list-unit-files --type=service --state=enabled
```

L'écoute réseau peut être vérifiée avec :

```bash
ss -tulpen
```

Ces commandes permettent de distinguer les services réellement actifs des logiciels simplement installés.

---

## 5. Logiciels installés

La présence d'un paquet ne signifie pas nécessairement qu'un service correspondant est actif.

L'inventaire des paquets doit donc être distingué de l'inventaire des services.

Une première vérification peut être réalisée avec :

```bash
dpkg-query -W
```

La recherche d'un paquet particulier peut être réalisée avec :

```bash
dpkg -l <paquet>
```

---

## 6. Comptes et privilèges

Les comptes locaux doivent être identifiés afin de déterminer :

* quels comptes sont nécessaires ;
* quels comptes disposent d'un shell ;
* quels comptes disposent de privilèges élevés ;
* quels comptes correspondent à des services ;
* quels comptes sont inutilisés.

Les groupes privilégiés doivent notamment être vérifiés.

```bash
getent group sudo
```

Le contrôle des comptes ne doit pas conduire à supprimer un compte système sans avoir vérifié ses dépendances.

---

## 7. Interfaces réseau

Les interfaces réseau permettent d'identifier les chemins de communication du système.

Une première analyse peut être effectuée avec :

```bash
ip address
```

et :

```bash
ip route
```

Il convient notamment de déterminer :

* quelles interfaces sont utilisées ;
* quelles adresses sont attribuées ;
* quelle route par défaut est utilisée ;
* quels réseaux sont accessibles ;
* quels services sont exposés sur chaque interface.

---

## 8. Données et fichiers de configuration

Les fichiers de configuration doivent être considérés comme des actifs à protéger.

Ils peuvent contenir :

* des paramètres de fonctionnement ;
* des informations réseau ;
* des comptes de service ;
* des chemins de fichiers ;
* des certificats ;
* des secrets ou références vers des secrets.

Les fichiers de configuration importants doivent donc être **protégés et sauvegardés**.

---

## 9. Supervision et sauvegarde

Un système correctement identifié doit également être associé à ses mécanismes de supervision et de sauvegarde.

Dans le laboratoire, la supervision peut notamment être assurée par Zabbix.

Les éléments nécessaires à la restauration doivent être identifiés, en particulier :

* configuration ;
* données applicatives ;
* fichiers de service ;
* paramètres réseau ;
* certificats lorsque nécessaire.

---

## 10. Résultat attendu

À l'issue de cette identification, le système doit disposer d'une fiche permettant de répondre simplement aux questions suivantes :

* Quel est son rôle ?
* Quels services fournit-il ?
* Quels ports expose-t-il ?
* Quels comptes l'administrent ?
* Quels logiciels sont nécessaires ?
* Quelles données contient-il ?
* Comment est-il supervisé ?
* Comment est-il restauré ?

Cette connaissance constitue la base des étapes suivantes du durcissement Debian.
