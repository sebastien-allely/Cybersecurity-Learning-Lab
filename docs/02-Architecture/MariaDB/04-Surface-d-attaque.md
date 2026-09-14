# 04 - Surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les principaux éléments constituant la surface d'attaque de MariaDB. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Objectif

Identifier les éléments exposés susceptibles d'être exploités par un attaquant.

---

# Services exposés

- Port TCP 3306
- Socket UNIX
- Réplication (si utilisée)
- TLS

---

# Comptes

- root
- comptes applicatifs
- comptes d'administration
- comptes anonymes

Chaque compte augmente la surface d'attaque.

---

# Configuration

La configuration peut exposer :

- des privilèges excessifs ;
- une écoute sur toutes les interfaces ;
- des options devenues obsolètes.

---

# Plugins

Chaque plugin chargé augmente :

- le volume de code ;
- les dépendances ;
- les vulnérabilités potentielles.

---

# Sauvegardes

Les sauvegardes constituent également une surface d'attaque.

Leur protection est indispensable.

---

# Conclusion

La réduction de la surface d'attaque consiste à conserver uniquement les fonctionnalités répondant à un besoin identifié.
