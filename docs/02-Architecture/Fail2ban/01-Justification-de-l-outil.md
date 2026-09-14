# 01 - Justification de l'outil

| Élément | Valeur |
| **Nom du document** | `01-Justification-de-l-outil.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Architecture |
| **Objectif** | Justifier l'intégration de Fail2ban dans l'architecture de protection du laboratoire et préciser son rôle par rapport aux autres mécanismes de sécurité. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Rôle de Fail2ban dans le laboratoire

Fail2ban est utilisé comme mécanisme de **détection et de réaction automatique** face à certains comportements malveillants observables dans les journaux.

Son principe consiste à :

1. analyser les journaux d'un service ;
2. rechercher des motifs correspondant à des comportements définis ;
3. comptabiliser les occurrences ;
4. déclencher une action lorsque le seuil configuré est atteint ;
5. appliquer une mesure de protection, généralement un bannissement temporaire.

---

# Justification du choix

Fail2ban a été retenu notamment pour :

* sa faible consommation de ressources ;
* son intégration avec les systèmes Linux ;
* sa capacité à exploiter les journaux existants ;
* sa simplicité de fonctionnement ;
* sa possibilité de créer des filtres spécifiques ;
* sa capacité à protéger plusieurs services avec des jails distinctes.

Dans le laboratoire, Fail2ban constitue une **mesure de protection complémentaire**.

---

# Positionnement

Fail2ban ne remplace pas :

* un pare-feu ;
* un antivirus ;
* un EDR ;
* CrowdSec ;
* Zabbix ;
* les mécanismes d'authentification ;
* les contrôles d'accès.

Il répond à un besoin différent : **réagir automatiquement à certains comportements détectables dans les journaux**.

---

# Limites

Fail2ban dépend directement de la qualité des journaux analysés.

Il ne peut pas détecter correctement un comportement :

* qui n'est pas journalisé ;
* qui ne correspond à aucun filtre ;
* qui utilise une technique différente des motifs recherchés.

Il ne constitue donc pas une protection comportementale générale.

---

# Positionnement dans le laboratoire

Fail2ban est notamment utilisé pour protéger des services Linux et des composants du laboratoire nécessitant une protection contre certaines tentatives répétées ou comportements hostiles.

Les configurations opérationnelles sont documentées dans :

```text
docs/04-Protection/Fail2ban/
```

Les scripts, filtres et fichiers associés sont conservés dans :

```text
automation/bash/fail2ban/
```

---

# Principe retenu

Fail2ban est considéré comme une **couche de protection légère et ciblée**, venant compléter les autres mécanismes de sécurité du laboratoire.
