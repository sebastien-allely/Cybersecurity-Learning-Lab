# 09 - Maintenance


| Élément | Valeur |
| **Nom du document** | `09-Maintenance.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le maintien de la sécurité de MariaDB nécessite une maintenance régulière permettant de préserver la conformité du serveur avec les décisions du référentiel.

---

# 2. Principes de conception

Le référentiel retient les principes suivants :

- documenter chaque modification ;
- contrôler les changements ;
- vérifier régulièrement la conformité ;
- limiter la dette technique ;
- préparer les évolutions futures.

---

# 3. Décisions retenues

Le référentiel recommande :

- documenter les évolutions ;
- supprimer les composants inutilisés ;
- contrôler les privilèges SQL ;
- vérifier régulièrement les sauvegardes ;
- revoir les indicateurs de supervision ;
- maintenir la documentation technique.

---

# 4. Vérification

Une revue périodique doit permettre de contrôler :

- la configuration de MariaDB ;
- les comptes ;
- les plugins ;
- les sauvegardes ;
- les journaux ;
- les décisions de sécurité.

---

# 5. Supervision

Les événements suivants présentent une valeur opérationnelle :

- modification inattendue de la configuration ;
- ajout d'un plugin ;
- création d'un compte privilégié ;
- échec d'une sauvegarde ;
- dérive détectée par AIDE.

---

# 6. Conclusion

La maintenance garantit la pérennité des décisions de sécurité et limite l'apparition de dette technique.

---

# Références

- ANSSI – Guide d'hygiène informatique.
- Documentation MariaDB.
- Documentation Debian.
- SOCLE – Stéphane Robert.
