# 02 - Surface d'attaque

| Élément                           | Valeur                                                                                                                       |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `02-Surface-d-attaque.md`                                                                                                    |
| **Technologie**                   | Ubuntu                                                                                                                       |
| **Catégorie**                     | Hardening                                                                                                                    |
| **Objectif**                      | Identifier les principaux éléments constituant la surface d'attaque d'un système Ubuntu et définir les moyens de la réduire. |
| **Auteur**                        | Sébastien Allely                                                                                                             |
| **Version**                       | 1.0                                                                                                                          |
| **Date de dernière modification** | 02/08/2026                                                                                                                   |

---

## 1. Définition

La surface d'attaque regroupe les éléments susceptibles d'être exploités pour compromettre le système ou ses données.

Elle comprend notamment :

* les services réseau ;
* les ports ouverts ;
* les logiciels installés ;
* les comptes ;
* les privilèges ;
* les interfaces réseau ;
* les tâches planifiées ;
* les fichiers de configuration ;
* les mécanismes d'administration.

---

## 2. Services

Les services actifs doivent être identifiés :

```bash
systemctl list-units --type=service --state=running
```

Les services activés au démarrage :

```bash
systemctl list-unit-files --type=service --state=enabled
```

Chaque service doit être associé à une justification.

---

## 3. Ports réseau

Les ports ouverts peuvent être identifiés avec :

```bash
ss -tulpen
```

Pour chaque port, il faut déterminer :

* le service associé ;
* son rôle ;
* les sources autorisées ;
* la nécessité de son exposition.

Un port sans justification doit être investigué.

---

## 4. Paquets installés

Les logiciels installés constituent également une composante de la surface d'attaque.

L'inventaire peut être obtenu avec :

```bash
dpkg-query -W
```

Les paquets inutiles doivent être évalués avant suppression.

---

## 5. Comptes

Les comptes locaux peuvent être recensés avec :

```bash
getent passwd
```

Les comptes privilégiés doivent être identifiés.

Les comptes inutilisés doivent être désactivés ou supprimés lorsque cela est possible sans compromettre le fonctionnement du système.

---

## 6. Administration distante

SSH constitue une surface d'exposition importante lorsqu'il est utilisé.

Les mesures doivent notamment viser :

* la limitation des utilisateurs autorisés ;
* l'authentification forte ;
* la limitation de l'exposition réseau ;
* la restriction de l'utilisation de `root` ;
* la surveillance des tentatives d'authentification.

---

## 7. Réduction

La réduction de la surface d'attaque suit le principe :

**identifier → justifier → supprimer ou restreindre → superviser.**

Une réduction de surface d'attaque doit toujours être vérifiée après modification.

---

## 8. Validation

Après modification :

```bash
systemctl --failed
```

Puis :

```bash
ss -tulpen
```

Les journaux doivent également être contrôlés.

Une modification qui provoque l'indisponibilité d'un service nécessaire doit être corrigée ou réévaluée.
