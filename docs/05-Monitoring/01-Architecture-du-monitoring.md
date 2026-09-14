### `docs/05-Monitoring/01-Architecture-du-monitoring.md`

# 01 - Architecture du monitoring

| Élément                           | Valeur                                                            |
| --------------------------------- | ----------------------------------------------------------------- |
| **Nom du document**               | `01-Architecture-du-monitoring.md`                                |
| **Technologie**                   | Zabbix                                                            |
| **Catégorie**                     | Monitoring                                                        |
| **Objectif**                      | Décrire l'architecture générale de la supervision du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                  |
| **Version**                       | 1.0                                                               |
| **Date de dernière modification** | 05/08/2026                                                        |

---

## 1. Objectif

L'architecture de monitoring doit permettre de disposer d'une vision cohérente de l'état des composants du laboratoire.

Elle doit couvrir à la fois :

* la disponibilité ;
* les performances ;
* les ressources ;
* les services ;
* les mécanismes de sécurité ;
* certains événements observables.

---

## 2. Organisation générale

L'organisation peut être représentée ainsi :

```text
                         Zabbix Server
                              │
             ┌────────────────┼────────────────┐
             │                │                │
          Linux             Windows         Proxmox
             │                │                │
       ┌─────┼─────┐          │          ┌─────┴─────┐
       │     │     │          │          │           │
      GLPI  AD   autres      VM       Node 1       Node 2
       │
       ├── Apache
       ├── MariaDB
       └── sécurité
```

Cette représentation est volontairement simplifiée.

L'architecture réelle doit être considérée avec les documentations des composants concernés.

---

## 3. Agents

Les machines virtuelles Linux et Windows utilisant l'agent Zabbix sont supervisées par l'intermédiaire de celui-ci.

Le laboratoire utilise **Zabbix Agent 2** sur les machines virtuelles concernées.

Les paramètres propres à chaque système sont documentés avec les configurations correspondantes.

---

## 4. Supervision des mécanismes de sécurité

La supervision ne se limite pas à vérifier que les serveurs répondent.

Certains mécanismes de sécurité sont eux-mêmes supervisés.

Exemples :

* état de CrowdSec ;
* état de Fail2ban ;
* état de ClamAV ;
* état d'AIDE lorsque cela est pertinent ;
* événements de sécurité ;
* éléments nécessaires à la vérification du fonctionnement des protections.

L'objectif est notamment d'éviter qu'un mécanisme de protection soit arrêté ou dégradé sans que cette situation soit détectée.

---

## 5. Principe de dépendance

Les dépendances doivent être prises en compte afin d'éviter les alertes secondaires inutiles.

Par exemple, une indisponibilité d'un composant critique peut provoquer plusieurs alertes sur les services qui en dépendent.

La supervision doit donc distinguer :

* la cause probable ;
* les conséquences ;
* les symptômes secondaires.

Cette logique est notamment utilisée dans la définition des triggers et de leurs dépendances.

---

## 6. Éléments techniques

Les éléments de configuration Zabbix sont conservés dans :

```text
zabbix/
```

Ce répertoire constitue la partie exploitable de la configuration de supervision.

La documentation décrit le comportement attendu ; les fichiers du répertoire `zabbix/` constituent la mise en œuvre.
