# Automation

| Élément                           | Valeur                                                                                                                                                                                            |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                                                                                                                       |
| **Technologie**                   | Automatisation                                                                                                                                                                                    |
| **Catégorie**                     | Automatisation                                                                                                                                                                                    |
| **Objectif**                      | Présenter l'organisation des scripts et fichiers d'automatisation du Cybersecurity-Learning-Lab et définir leur rôle dans la mise en œuvre, la maintenance et la reproductibilité du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                                                                                                  |
| **Version**                       | 1.0                                                                                                                                                                                               |
| **Date de dernière modification** | 06/08/2026                                                                                                                                                                                        |

---

# 1. Objectif

Le dossier **Automation** regroupe les scripts et fichiers utilisés pour automatiser certaines opérations du **Cybersecurity-Learning-Lab**.

L'automatisation a pour objectif de réduire les opérations manuelles répétitives, d'améliorer la reproductibilité des configurations et de limiter les erreurs humaines.

Elle ne remplace toutefois pas la documentation technique.

Chaque automatisation doit rester compréhensible, vérifiable et associée à la documentation décrivant le mécanisme qu'elle met en œuvre.

---

# 2. Organisation

Le dossier est organisé par technologie ou langage utilisé :

```text
automation/
├── bash/
├── powershell/
├── python/
└── sql/
```

## Bash

Le répertoire `bash/` contient les scripts et fichiers de configuration destinés principalement aux systèmes Linux.

Il peut notamment contenir :

* des scripts d'administration ;
* des scripts de durcissement ;
* des configurations de services ;
* des filtres ou fichiers utilisés par les mécanismes de sécurité ;
* des automatisations liées à la maintenance.

---

## PowerShell

Le répertoire `powershell/` contient les scripts destinés principalement aux systèmes Windows.

Il peut notamment être utilisé pour :

* l'administration Windows ;
* Active Directory ;
* la collecte d'informations ;
* les contrôles de configuration ;
* l'automatisation de tâches de sécurité.

---

## Python

Le répertoire `python/` est destiné aux automatisations nécessitant Python.

Il pourra notamment être utilisé pour :

* le traitement de données ;
* l'analyse de journaux ;
* la génération de rapports ;
* l'automatisation de tâches complexes ;
* les futurs exercices du laboratoire.

---

## SQL

Le répertoire `sql/` contient les scripts SQL nécessaires aux opérations documentées dans le laboratoire.

Ils peuvent notamment concerner :

* l'initialisation de bases de données ;
* la vérification de données ;
* les opérations d'administration ;
* les exercices portant sur les bases de données.

---

# 3. Relation avec la documentation

Les fichiers présents dans `automation/` ne constituent pas une documentation autonome.

Lorsqu'un script ou une configuration est utilisé par une technologie du laboratoire, son utilisation doit être expliquée dans la documentation correspondante.

La relation attendue est donc :

```text
Documentation
      │
      ▼
Décision technique
      │
      ▼
Automatisation
      │
      ▼
Mise en œuvre
      │
      ▼
Validation
```

L'automatisation doit ainsi découler d'une décision documentée et non constituer un mécanisme isolé.

---

# 4. Principe de reproductibilité

Une automatisation doit autant que possible être :

* reproductible ;
* explicite ;
* documentée ;
* vérifiable ;
* maintenable ;
* adaptée à l'environnement du laboratoire.

Lorsqu'un script modifie une configuration de sécurité, son comportement doit être suffisamment documenté pour permettre à l'apprenant de comprendre les changements effectués.

---

# 5. Sécurité

Les scripts du laboratoire peuvent modifier des composants sensibles.

Ils doivent donc être considérés comme faisant partie de la surface de gestion de l'infrastructure.

Un script ne doit notamment pas :

* contenir de mot de passe ou de secret en clair ;
* dépendre silencieusement d'un environnement particulier ;
* modifier une configuration critique sans possibilité de vérification ;
* désactiver un mécanisme de sécurité sans justification documentée.

Les fichiers sensibles ou contenant des informations propres à une infrastructure réelle ne doivent pas être publiés dans le dépôt.

---

# 6. Validation

Avant d'être intégré au laboratoire, un mécanisme d'automatisation doit être testé dans l'environnement prévu.

La validation doit notamment vérifier :

* le résultat attendu ;
* les erreurs éventuelles ;
* l'impact sur les services existants ;
* la possibilité de reproduire l'opération ;
* la compatibilité avec la documentation.

Les automatisations utilisées dans le laboratoire doivent rester cohérentes avec les versions et configurations documentées.

---

# 7. Relation avec les exercices

Les scripts d'automatisation peuvent également être utilisés dans les exercices pédagogiques.

L'apprenant doit toutefois être capable de comprendre l'opération réalisée avant d'utiliser une automatisation qui la reproduit.

L'objectif du laboratoire n'est pas uniquement de fournir des scripts fonctionnels, mais de permettre de comprendre les mécanismes qu'ils automatisent.

---

# 8. Évolution

Le contenu de ce dossier évoluera progressivement avec le laboratoire.

De nouvelles automatisations pourront être ajoutées lorsqu'une opération :

* est suffisamment stable ;
* présente un intérêt pédagogique ou opérationnel ;
* a été testée ;
* est documentée ;
* apporte un gain réel de reproductibilité.

L'automatisation ne doit pas être introduite uniquement pour automatiser une opération qui reste plus pertinente à réaliser manuellement dans un objectif pédagogique.

---

# Conclusion

Le dossier **Automation** constitue la couche d'automatisation du **Cybersecurity-Learning-Lab**.

Il permet de regrouper les scripts et fichiers nécessaires à la reproductibilité du laboratoire tout en maintenant une séparation claire entre :

* la compréhension d'une technologie ;
* sa configuration ;
* sa documentation ;
* son automatisation ;
* sa validation.

Cette séparation permet de conserver une finalité pédagogique au projet tout en préparant progressivement son industrialisation.
