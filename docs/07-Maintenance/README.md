### `docs/07-Maintenance/README.md`

# Maintenance

| Élément                           | Valeur                                                                                                          |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                                     |
| **Technologie**                   | Maintenance                                                                                                     |
| **Catégorie**                     | Maintenance                                                                                                     |
| **Objectif**                      | Présenter les principes permettant de maintenir le laboratoire dans un état sécurisé, fonctionnel et documenté. |
| **Auteur**                        | Sébastien Allely                                                                                                |
| **Version**                       | 1.0                                                                                                             |
| **Date de dernière modification** | 05/08/2026                                                                                                      |

---

# 1. Objectif

Le laboratoire est un système évolutif.

Les composants, versions, vulnérabilités, configurations et besoins peuvent changer.

La maintenance permet de conserver la cohérence entre :

```text
Architecture
    ↕
Configuration
    ↕
Sécurité
    ↕
Supervision
    ↕
Documentation
```

---

# 2. Types de maintenance

Le laboratoire distingue notamment :

* maintenance corrective ;
* maintenance préventive ;
* maintenance évolutive ;
* maintenance de sécurité ;
* maintenance documentaire.

---

# 3. Maintenance corrective

Elle intervient lorsqu'un dysfonctionnement est identifié.

La démarche doit chercher à :

1. identifier la cause ;
2. corriger ;
3. vérifier ;
4. documenter ;
5. déterminer si une action préventive est nécessaire.

---

# 4. Maintenance de sécurité

Elle comprend notamment :

* mises à jour ;
* correction des vulnérabilités ;
* vérification des comptes ;
* vérification des services ;
* contrôle des configurations ;
* maintien des mécanismes de protection ;
* vérification de la supervision.

---

# 5. Maintenance documentaire

Toute modification importante de l'infrastructure doit conduire à vérifier les documents concernés.

Une configuration qui évolue sans documentation correspondante crée une divergence entre le laboratoire réel et le référentiel.

---

# 6. Cycle

```text
Observer
   ↓
Identifier
   ↓
Évaluer
   ↓
Modifier
   ↓
Tester
   ↓
Superviser
   ↓
Documenter
   ↓
Réévaluer
```

---

# 7. Documentation associée

Les procédures techniques spécifiques restent dans les dossiers correspondant aux technologies concernées.

Ce dossier définit la démarche générale.
