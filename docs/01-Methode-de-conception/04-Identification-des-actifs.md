# 02 - Identification des actifs

| Élément | Valeur |
| **Nom du document** | `02-Identification-des-actifs.md` |
| **Technologie** | Méthode de conception |
| **Catégorie** | Méthodologie |
| **Objectif** | Définir la méthode d'identification et de caractérisation des actifs du laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Définition

Un actif est un élément dont la disponibilité, l'intégrité, la confidentialité ou le fonctionnement présente une valeur pour le laboratoire.

Il peut s'agir :

* d'un système ;
* d'une machine virtuelle ;
* d'un service ;
* d'une donnée ;
* d'une configuration ;
* d'un compte ;
* d'un composant réseau ;
* d'un mécanisme de sécurité.

---

# Identification

Chaque actif doit être identifié selon son rôle réel.

Les informations pertinentes comprennent notamment :

* nom logique ;
* rôle ;
* système d'exploitation ;
* emplacement ;
* dépendances ;
* données manipulées ;
* services exposés ;
* mécanismes de protection ;
* mécanismes de supervision.

---

# Actifs du laboratoire

La documentation utilise des noms d'hôtes anonymisés et cohérents.

Les principaux systèmes sont notamment :

| Actif      | Rôle             |
| ---------- | ---------------- |
| `PVE1`     | Nœud Proxmox VE  |
| `PVE2`     | Nœud Proxmox VE  |
| `AD01`     | Active Directory |
| `GLPI01`   | GLPI             |
| `ZABBIX01` | Zabbix           |

Le réseau du laboratoire est documenté sous la forme :

```text
LAN : 192.168.1.0/24
```

Les équipements personnels et informations permettant d'identifier précisément l'environnement réel ne doivent pas être exposés dans le référentiel public.

---

# Dépendances

L'identification d'un actif doit également tenir compte de ses dépendances.

Exemple :

```text
GLPI01
  ├── Apache
  ├── PHP
  └── MariaDB
```

Une défaillance d'une dépendance peut donc affecter l'actif principal.

---

# Criticité

L'identification d'un actif constitue une étape préalable à l'évaluation de sa criticité.

La criticité ne doit pas être déduite uniquement du nom du système.

Elle doit prendre en compte son rôle, ses dépendances, son exposition et son impact en cas de compromission ou d'indisponibilité.
