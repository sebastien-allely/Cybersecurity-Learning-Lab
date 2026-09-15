# 04 - Surface d'attaque

| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les composants et interfaces constituant la surface d'attaque associée à Fail2ban. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Surface locale

Fail2ban ajoute principalement une surface de configuration et d'exécution locale.

Les éléments sensibles comprennent :

* les fichiers de configuration ;
* les jails ;
* les filtres ;
* les actions ;
* les journaux ;
* le processus Fail2ban ;
* les mécanismes de bannissement.

---

# Surface réseau

Fail2ban n'a pas vocation à exposer une interface réseau d'administration.

Son fonctionnement agit principalement sur les mécanismes locaux de filtrage du système.

La surface réseau dépend donc surtout des services que Fail2ban protège.

---

# Surface liée aux journaux

Les journaux constituent une dépendance majeure.

Un attaquant capable de modifier ou de supprimer les événements analysés peut réduire l'efficacité de la détection.

Les permissions sur les journaux doivent donc être maîtrisées.

---

# Réduction de la surface d'attaque

Les principes retenus sont :

* n'activer que les jails nécessaires ;
* utiliser uniquement les filtres nécessaires ;
* limiter les privilèges ;
* protéger les fichiers de configuration ;
* protéger les journaux ;
* éviter les actions inutiles ;
* superviser Fail2ban ;
* tester les modifications avant leur déploiement.

---

# Configuration

Les fichiers de configuration doivent être protégés et sauvegardés.

Les éléments critiques comprennent notamment :

```text
/etc/fail2ban/
/etc/fail2ban/jail.d/
/etc/fail2ban/filter.d/
```

Les fichiers personnalisés du laboratoire doivent également être conservés dans le référentiel prévu à cet effet.
