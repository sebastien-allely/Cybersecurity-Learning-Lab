### `docs/05-Monitoring/06-Tableaux-de-bord.md`

# 06 - Tableaux de bord

| Élément                           | Valeur                                                                   |
| --------------------------------- | ------------------------------------------------------------------------ |
| **Nom du document**               | `06-Tableaux-de-bord.md`                                                 |
| **Technologie**                   | Zabbix                                                                   |
| **Catégorie**                     | Monitoring                                                               |
| **Objectif**                      | Définir le rôle des tableaux de bord dans l'exploitation du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                         |
| **Version**                       | 1.0                                                                      |
| **Date de dernière modification** | 05/08/2026                                                               |

---

## 1. Objectif

Les tableaux de bord permettent de présenter les informations de supervision de manière synthétique.

Ils doivent faciliter :

* la surveillance ;
* l'identification des anomalies ;
* l'analyse d'une situation ;
* le suivi des indicateurs ;
* la compréhension de l'état général du laboratoire.

---

## 2. Principes

Un tableau de bord doit rester lisible.

Il doit privilégier :

* les informations importantes ;
* les alertes pertinentes ;
* les tendances utiles ;
* les indicateurs associés à des objectifs.

L'accumulation de widgets ne constitue pas une amélioration de la supervision.

---

## 3. Organisation

Les tableaux de bord peuvent être organisés selon plusieurs niveaux :

```text
Laboratoire
    ↓
Infrastructure
    ↓
Technologie
    ↓
Service
    ↓
Événement
```

Cette organisation permet de passer progressivement d'une vision globale à une analyse ciblée.

---

## 4. Tableaux de bord de sécurité

Certains tableaux de bord peuvent être consacrés aux mécanismes de sécurité.

Ils peuvent notamment présenter :

* état de CrowdSec ;
* état de Fail2ban ;
* événements détectés ;
* état de ClamAV ;
* état d'AIDE ;
* alertes de sécurité ;
* événements nécessitant une investigation.

---

## 5. Mise en œuvre

Les configurations des tableaux de bord utilisées dans le laboratoire sont conservées dans :

```text
zabbix/dashboards/
```

La documentation explique leur rôle.

Les objets techniques constituent la source de vérité de leur configuration.
