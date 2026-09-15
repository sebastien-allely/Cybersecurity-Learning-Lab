### `docs/06-Incident-Response/README.md`

# Réponse à incident

| Élément                           | Valeur                                                                                    |
| --------------------------------- | ----------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                               |
| **Technologie**                   | Réponse à incident                                                                        |
| **Catégorie**                     | Incident Response                                                                         |
| **Objectif**                      | Présenter la démarche de réponse à incident appliquée dans le Cybersecurity-Learning-Lab. |
| **Auteur**                        | Sébastien Allely                                                                          |
| **Version**                       | 1.0                                                                                       |
| **Date de dernière modification** | 05/08/2026                                                                                |

---

# 1. Pourquoi un dossier Incident Response ?

La supervision permet de détecter des événements.

La protection permet de réduire certains risques.

La réponse à incident traite ce qui se produit lorsqu'un événement nécessite une investigation et une action.

La chaîne peut être représentée ainsi :

```text
Événement
   ↓
Détection
   ↓
Qualification
   ↓
Investigation
   ↓
Confinement
   ↓
Remédiation
   ↓
Restauration
   ↓
Validation
   ↓
Retour d'expérience
```

---

# 2. Positionnement dans le laboratoire

Le dossier s'appuie notamment sur :

* la méthode de conception ;
* l'architecture ;
* le hardening ;
* les mécanismes de protection ;
* la supervision ;
* les journaux système ;


Il constitue donc une étape de mise en pratique des mécanismes précédents.

---

# 3. Objectif pédagogique

L'objectif n'est pas uniquement de savoir identifier une alerte.

L'apprenant doit progressivement apprendre à :

* comprendre ce qui s'est produit ;
* déterminer si l'événement est significatif ;
* identifier les actifs concernés ;
* rechercher les éléments permettant de qualifier la situation ;
* limiter l'impact ;
* corriger la cause ;
* restaurer le fonctionnement ;
* vérifier la situation ;
* documenter les conclusions.

---

# 4. Périmètre

La réponse à incident du laboratoire est limitée aux capacités réellement disponibles dans l'environnement.

Elle pourra notamment exploiter :

* journaux système ;
* journaux applicatifs ;
* Zabbix ;
* CrowdSec ;
* Fail2ban ;
* ClamAV ;
* AIDE ;
* informations disponibles sur les systèmes concernés.

Les capacités futures pourront être ajoutées lorsque de nouveaux composants seront intégrés au laboratoire.

---

# 5. Relation avec les exercices

Les scénarios d'incident pourront ultérieurement servir de base à la conception d'exercices pratiques, lorsque le modèle pédagogique et le mécanisme d'évaluation auront été définis.

L'apprenant pourra ainsi passer de :

```text
documentation
     ↓
observation
     ↓
exercice
     ↓
investigation
     ↓
remédiation
```

---
