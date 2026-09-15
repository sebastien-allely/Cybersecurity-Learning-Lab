### `docs/10-Appendices/03-Matrice-de-correspondance.md`

# 03 - Matrice de correspondance

| Élément                           | Valeur                                                                                      |
| --------------------------------- | ------------------------------------------------------------------------------------------- |
| **Nom du document**               | `03-Matrice-de-correspondance.md`                                                           |
| **Technologie**                   | Référentiel                                                                                 |
| **Catégorie**                     | Appendices                                                                                  |
| **Objectif**                      | Mettre en relation les principales couches documentaires et opérationnelles du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                            |
| **Version**                       | 1.0                                                                                         |
| **Date de dernière modification** | 05/08/2026                                                                                  |

---

## 1. Correspondance générale

| Domaine           | Documentation               | Mise en œuvre              |
| ----------------- | --------------------------- | -------------------------- |
| Méthode           | `01-Methode-de-conception/` | décisions d'architecture   |
| Architecture      | `02-Architecture/`          | infrastructure réelle      |
| Hardening         | `03-Hardening/`             | configurations sécurisées  |
| Protection        | `04-Protection/`            | mécanismes de sécurité     |
| Monitoring        | `05-Monitoring/`            | `zabbix/`                  |
| Incident Response | `06-Incident-Response/`     | procédures et exercices    |
| Maintenance       | `07-Maintenance/`           | procédures d'exploitation  |
| Learning Path     | `09-Learning-Path/`         | parcours pédagogiques      |
| Appendices        | `10-Appendices/`            | informations transversales |

---

## 2. Principe

Chaque élément opérationnel important doit pouvoir être relié à sa documentation.

Inversement, une documentation décrivant une capacité opérationnelle doit pouvoir identifier sa mise en œuvre lorsqu'elle existe.

---

## 3. Objectif

Cette correspondance permet de limiter les divergences entre :

```text
ce qui est documenté
        ↕
ce qui est configuré
        ↕
ce qui est supervisé
        ↕
ce qui est enseigné
```
