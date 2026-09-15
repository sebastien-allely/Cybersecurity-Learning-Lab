# Diagnostic réseau Debian

**Nom du document** : Diagnostic réseau Debian
**Technologie** : Debian GNU/Linux
**Catégorie** : Lab pratique
**Objectif** : Diagnostiquer une anomalie réseau sur un système Debian en contrôlant les interfaces, routes, sockets, DNS et connectivité.
**Auteur** : Sébastien ALLELY
**Version** : 1.0
**Date de dernière modification** : 2026-09-13

---

## 1. Objectif

Identifier la couche responsable d'une perte ou d'une dégradation de connectivité.

---

## 2. Méthode

Vérifier successivement :

1. interface réseau ;
2. adresse IP ;
3. route ;
4. passerelle ;
5. résolution DNS ;
6. connectivité ;
7. service concerné ;
8. ports en écoute.

---

## 3. Outils

Utiliser notamment :

* `ip addr`
* `ip route`
* `ping`
* `ss`
* `resolvectl` lorsque disponible
* `dig` ou `nslookup` selon l'environnement.

---

## 4. Critères de réussite

Le diagnostic doit déterminer à quelle couche se situe le problème et fournir les preuves correspondantes.

---

## 5. Références

* Documentation Debian
* ANSSI
* NIST
