# 02 - AppArmor


| Élément | Valeur |
| **Nom du document** | `02-AppArmor.md` |
| **Technologie** | Ubuntu |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Mise en œuvre dans le laboratoire

Pour la VM GLPI01, les profils AppArmor doivent être évalués pour les composants exposés, notamment :

- Apache ;
- PHP ;
- MariaDB ;
- autres services installés.

Toute modification doit être testée avant déploiement définitif.

---

# Conclusion

AppArmor est une couche de confinement particulièrement importante dans Ubuntu.

Son objectif n'est pas de remplacer les permissions Unix, le pare-feu ou les autres mécanismes de sécurité.

Il ajoute une barrière supplémentaire afin qu'une compromission d'un service ne donne pas automatiquement accès à l'ensemble du système.
