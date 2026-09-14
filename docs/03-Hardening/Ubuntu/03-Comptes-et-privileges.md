# 03 - Comptes et privilèges

| Élément                           | Valeur                                                                                          |
| --------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Nom du document**               | `03-Comptes-et-privileges.md`                                                                   |
| **Technologie**                   | Ubuntu                                                                                          |
| **Catégorie**                     | Hardening                                                                                       |
| **Objectif**                      | Réduire les risques liés aux comptes utilisateurs et à l'attribution des privilèges sur Ubuntu. |
| **Auteur**                        | Sébastien Allely                                                                                |
| **Version**                       | 1.0                                                                                             |
| **Date de dernière modification** | 02/08/2026                                                                                      |

---

## 1. Principe du moindre privilège

Chaque compte doit disposer uniquement des privilèges nécessaires à son activité.

Un utilisateur ne doit pas disposer de privilèges administratifs permanents lorsqu'une élévation ponctuelle suffit.

---

## 2. Inventaire des comptes

Les comptes locaux peuvent être identifiés avec :

```bash
getent passwd
```

Il faut distinguer :

* comptes humains ;
* comptes système ;
* comptes de service ;
* comptes techniques.

Les comptes système ne doivent pas être supprimés arbitrairement.

---

## 3. Comptes privilégiés

Les membres du groupe `sudo` peuvent être vérifiés avec :

```bash
getent group sudo
```

Chaque membre doit avoir une justification.

L'administration doit privilégier l'utilisation d'un compte nominatif plutôt qu'un compte partagé.

---

## 4. Compte root

Le compte `root` est nécessaire au fonctionnement du système mais son utilisation directe doit être limitée.

L'administration courante doit autant que possible passer par `sudo`, ce qui permet notamment une meilleure traçabilité des opérations privilégiées.

---

## 5. Authentification

Les mécanismes d'authentification doivent être adaptés au niveau de risque.

Pour les accès SSH, l'authentification par clé doit être privilégiée lorsque le contexte le permet.

Les mots de passe doivent respecter une politique adaptée au risque et ne doivent pas constituer l'unique mécanisme de protection lorsqu'une authentification plus forte est disponible.

---

## 6. Comptes inutilisés

Un compte qui n'est plus nécessaire doit être désactivé ou supprimé selon le contexte.

Avant suppression, il faut vérifier :

* son propriétaire ;
* les fichiers associés ;
* les tâches planifiées ;
* les services ;
* les dépendances.

---

## 7. Permissions

Les fichiers sensibles doivent être protégés contre les accès non autorisés.

Une attention particulière doit être portée à :

```text
/etc/shadow
/etc/gshadow
/etc/sudoers
/etc/sudoers.d/
```

Les clés privées et fichiers contenant des secrets doivent également être protégés.

---

## 8. Protection des configurations

Les fichiers de configuration utilisés par les services critiques doivent être :

* accessibles uniquement aux comptes nécessaires ;
* protégés contre les modifications non autorisées ;
* sauvegardés avant modification ;
* restaurables en cas d'erreur.

---

## 9. Contrôle

Après modification des comptes ou privilèges, vérifier :

```bash
id
```

```bash
getent group sudo
```

et contrôler les journaux lorsque l'opération implique une élévation de privilèges.

---

## 10. Conclusion

La gestion des comptes doit permettre de limiter les possibilités d'action d'un utilisateur compromis.

Le principe retenu est :

**identifier → justifier → limiter → surveiller → réévaluer.**
