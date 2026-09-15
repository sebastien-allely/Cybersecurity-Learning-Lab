# 01 - Principes de conception

| Élément | Valeur |
| **Nom du document** | `01-Principes-de-conception.md` |
| **Technologie** | Méthode de conception |
| **Catégorie** | Méthodologie |
| **Objectif** | Définir les principes utilisés pour concevoir et faire évoluer le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Sécurité dès la conception

La sécurité doit être prise en compte avant la mise en œuvre d'un composant.

Une technologie ne doit pas être ajoutée uniquement parce qu'elle apporte une fonctionnalité.

La question préalable est :

> Quel besoin du laboratoire justifie cette technologie ?

---

# Réduction de la surface d'attaque

Chaque composant ajouté augmente potentiellement :

* le nombre de services ;
* le nombre de configurations ;
* le nombre de comptes ;
* les dépendances ;
* les possibilités d'erreur ;
* la surface d'attaque.

Le laboratoire doit donc éviter l'accumulation de composants sans justification.

---

# Défense en profondeur

Aucune mesure unique ne doit être considérée comme suffisante.

Le laboratoire combine notamment :

* durcissement ;
* contrôle des accès ;
* segmentation lorsque l'architecture le permet ;
* protection ;
* supervision ;
* sauvegardes ;
* détection ;
* réponse à incident.

Une compromission d'une couche ne doit pas nécessairement entraîner la compromission de l'ensemble du laboratoire.

---

# Proportionnalité

Une mesure de sécurité doit être proportionnée au risque traité.

Il n'est pas pertinent d'appliquer systématiquement le niveau de protection maximal à tous les composants.

La criticité de l'actif, son exposition et ses dépendances doivent être prises en compte.

---

# Traçabilité

Une décision importante doit pouvoir être reliée :

```text
Risque
  ↓
Besoin
  ↓
Décision
  ↓
Configuration
  ↓
Contrôle
```

Cette traçabilité permet de comprendre pourquoi une configuration existe et facilite son évolution.

---

# Réversibilité

Lorsque cela est possible, les changements doivent pouvoir être :

* identifiés ;
* sauvegardés ;
* testés ;
* restaurés.

Les fichiers de configuration critiques doivent notamment être protégés et sauvegardés.

---

# Principe de réalité

La documentation doit rester alignée avec le laboratoire réellement déployé.

Une configuration théorique qui n'existe pas dans le laboratoire ne doit pas être présentée comme une configuration opérationnelle.

Inversement, une modification importante réalisée dans le laboratoire doit être documentée.

---

# Évolution

Le laboratoire est considéré comme un système vivant.

Toute évolution significative doit entraîner une réévaluation :

* des actifs ;
* des dépendances ;
* des risques ;
* de la surface d'attaque ;
* des mesures de sécurité ;
* de la supervision.
