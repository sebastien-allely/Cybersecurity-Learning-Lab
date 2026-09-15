### `docs/07-Maintenance/04-Verification-des-configurations.md`

# 04 - Vérification des configurations

| Élément                           | Valeur                                                                                      |
| --------------------------------- | ------------------------------------------------------------------------------------------- |
| **Nom du document**               | `04-Verification-des-configurations.md`                                                     |
| **Technologie**                   | Maintenance                                                                                 |
| **Catégorie**                     | Maintenance                                                                                 |
| **Objectif**                      | Maintenir la cohérence entre les configurations réellement utilisées et leur documentation. |
| **Auteur**                        | Sébastien Allely                                                                            |
| **Version**                       | 1.0                                                                                         |
| **Date de dernière modification** | 05/08/2026                                                                                  |

---

## 1. Objectif

Les configurations importantes doivent être contrôlées régulièrement.

---

## 2. Vérifications

Selon le composant, contrôler notamment :

* services actifs ;
* ports exposés ;
* comptes ;
* permissions ;
* fichiers de configuration ;
* mécanismes de sécurité ;
* supervision ;
* sauvegardes.

---

## 3. Documentation

Lorsqu'une configuration réelle diverge de la documentation, il faut déterminer si :

* la configuration doit être corrigée ;
* la documentation doit être mise à jour ;
* la divergence est volontaire et doit être justifiée.

---

## 4. Automatisation

Lorsque cela apporte une valeur réelle, les vérifications répétitives peuvent être automatisées.

Les scripts réutilisables sont conservés dans :

```text
automation/
```

---

## 5. Contrôle

Une vérification doit produire un résultat exploitable.

L'objectif n'est pas de multiplier les contrôles mais d'identifier les écarts importants.
