# 02 - Gestion des comptes


| Élément | Valeur |
| **Nom du document** | `02-Gestion-des-comptes.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les comptes MariaDB constituent un point d'entrée privilégié vers les données hébergées.

Leur gestion doit garantir une authentification robuste et l'application du principe du moindre privilège.

---

# 2. Décisions retenues

Le référentiel retient les décisions suivantes :

- supprimer les comptes anonymes ;
- limiter l'utilisation du compte `root` ;
- créer un compte dédié par application ;
- attribuer uniquement les privilèges nécessaires ;
- supprimer les comptes inutilisés ;
- documenter les comptes disposant de privilèges élevés.

---

# 3. Vérification

Une revue périodique doit permettre de vérifier :

- les comptes existants ;
- les privilèges accordés ;
- les comptes inactifs ;
- les comptes disposant de privilèges globaux.

---

# 4. Conclusion

Une gestion rigoureuse des comptes SQL réduit significativement le risque de compromission et limite l'impact d'un compte compromis.
