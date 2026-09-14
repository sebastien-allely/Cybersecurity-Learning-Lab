# Automatisation Bash

| Élément                           | Valeur                                                                                                            |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                                       |
| **Technologie**                   | Bash                                                                                                              |
| **Catégorie**                     | Automatisation                                                                                                    |
| **Objectif**                      | Présenter l'organisation des automatisations Bash du Cybersecurity-Learning-Lab et leur rôle dans le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                  |
| **Version**                       | 1.0                                                                                                               |
| **Date de dernière modification** | 11/08/2026                                                                                                        |

---

## 1. Objectif

Le répertoire `bash/` contient les scripts et fichiers d'automatisation destinés principalement aux systèmes Linux du **Cybersecurity-Learning-Lab**.

Ces éléments permettent notamment de reproduire certaines opérations d'administration, de configuration, de protection ou de maintenance.

L'automatisation ne remplace pas la compréhension du mécanisme qu'elle met en œuvre. Les opérations automatisées doivent donc rester documentées et vérifiables.

---

## 2. Organisation

Le contenu est organisé par technologie ou mécanisme automatisé.

```text
bash/
└── fail2ban/
```

### `fail2ban/`

Ce répertoire contient les fichiers de configuration Fail2ban utilisés dans le laboratoire.

La documentation et les fichiers associés sont regroupés dans ce sous-répertoire afin de séparer clairement les configurations spécifiques à Fail2ban du reste des automatisations Bash.

---

## 3. Principes

Les automatisations Bash doivent autant que possible être :

* reproductibles ;
* explicites ;
* documentées ;
* vérifiables ;
* maintenables ;
* adaptées à leur environnement cible.

Un script ou fichier de configuration ne doit pas être ajouté uniquement pour éviter une opération manuelle lorsqu'une exécution manuelle présente un intérêt pédagogique.

---

## 4. Sécurité

Les scripts et configurations Bash peuvent modifier des composants sensibles du laboratoire.

Ils doivent donc être considérés comme des éléments de gestion de l'infrastructure.

Ils ne doivent notamment pas :

* contenir de secrets en clair ;
* contenir d'identifiants propres à une infrastructure réelle ;
* dépendre silencieusement d'un environnement personnel ;
* désactiver un mécanisme de sécurité sans justification documentée ;
* modifier une configuration critique sans possibilité de vérification.

Les éléments spécifiques à l'infrastructure personnelle doivent être anonymisés avant leur intégration au dépôt.

---

## 5. Documentation associée

Lorsqu'une automatisation Bash met en œuvre une technologie documentée ailleurs dans le dépôt, le fichier ou répertoire concerné doit permettre de retrouver cette documentation.

La relation attendue est :

```text
Documentation
      │
      ▼
Configuration
      │
      ▼
Automatisation Bash
      │
      ▼
Validation
```

L'automatisation doit donc rester rattachée à un mécanisme documenté et ne pas devenir une configuration isolée.

---

## 6. Évolution

De nouvelles automatisations Bash peuvent être ajoutées lorsque leur utilisation apporte un intérêt réel au laboratoire, notamment en matière de :

* reproductibilité ;
* maintenance ;
* sécurité ;
* administration ;
* validation ;
* apprentissage.

Chaque ajout doit être documenté et testé avant d'être considéré comme utilisable dans le laboratoire.
