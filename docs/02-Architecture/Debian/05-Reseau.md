# 05 - Réseau


| Élément | Valeur |
| **Nom du document** | `05-Reseau.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Réseau du laboratoire

Le réseau documentaire du laboratoire est :

```text
192.168.1.0/24
```

Cette information constitue la référence documentaire pour les exemples réseau du laboratoire.

---

## Interfaces

Les interfaces peuvent être examinées avec :

```bash
ip addr
```

Le routage :

```bash
ip route
```

Les voisins :

```bash
ip neigh
```

---

## Résolution DNS

La résolution DNS est essentielle au fonctionnement de nombreux services.

Elle doit être vérifiée lors d'un diagnostic réseau.

Exemples :

```bash
getent hosts <nom>
resolvectl status
```

Selon la configuration du système, `resolvectl` peut ne pas être disponible ou ne pas être l'outil utilisé.

---

## Connectivité

Tests courants :

```bash
ping <adresse>
```

et :

```bash
ss -lntup
```

Le premier permet de vérifier une connectivité IP de base ; le second permet d'identifier les services en écoute.

---

## Architecture

Debian peut intervenir :

* comme système hôte ;
* comme serveur ;
* comme système de supervision ;
* comme composant d'infrastructure.

La configuration réseau doit donc être adaptée au rôle du système.

---

## Références

* Documentation Debian
* Debian Administrator's Handbook
* Référentiel Réseau du laboratoire
