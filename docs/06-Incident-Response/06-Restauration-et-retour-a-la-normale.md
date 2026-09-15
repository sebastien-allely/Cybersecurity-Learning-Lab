### `docs/06-Incident-Response/06-Restauration-et-retour-a-la-normale.md`

# 06 - Restauration et retour à la normale

| Élément                           | Valeur                                                                                 |
| --------------------------------- | -------------------------------------------------------------------------------------- |
| **Nom du document**               | `06-Restauration-et-retour-a-la-normale.md`                                            |
| **Technologie**                   | Incident Response                                                                      |
| **Catégorie**                     | Incident Response                                                                      |
| **Objectif**                      | Définir les contrôles nécessaires après une action de remédiation ou une restauration. |
| **Auteur**                        | Sébastien Allely                                                                       |
| **Version**                       | 1.0                                                                                    |
| **Date de dernière modification** | 05/08/2026                                                                             |

---

## 1. Objectif

La restauration consiste à remettre le système dans un état maîtrisé et fonctionnel.

Elle peut être réalisée par :

* correction directe ;
* restauration d'une configuration ;
* restauration d'une machine ;
* restauration depuis une sauvegarde ;
* reconstruction du système.

---

## 2. Vérifications

Avant de considérer l'incident comme terminé, vérifier :

* disponibilité du système ;
* fonctionnement des services ;
* fonctionnement des mécanismes de sécurité ;
* supervision ;
* sauvegarde ;
* absence d'anomalie résiduelle.

---

## 3. Retour à l'état nominal

Le retour à l'état nominal doit être vérifié indépendamment de l'action corrective.

Exemple :

```text
Service restauré
      ↓
Protection active
      ↓
Supervision opérationnelle
      ↓
Événement non reproduit
      ↓
Situation nominale
```

---

## 4. Documentation

Les actions réalisées et les résultats observés doivent être documentés.

Cette documentation constitue une source pour le retour d'expérience.
