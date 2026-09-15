### `docs/06-Incident-Response/02-Qualification-d-un-evenement.md`

# 02 - Qualification d'un événement

| Élément                           | Valeur                                                                                          |
| --------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Nom du document**               | `02-Qualification-d-un-evenement.md`                                                            |
| **Technologie**                   | Incident Response                                                                               |
| **Catégorie**                     | Incident Response                                                                               |
| **Objectif**                      | Définir une démarche permettant de déterminer la nature et l'importance d'un événement observé. |
| **Auteur**                        | Sébastien Allely                                                                                |
| **Version**                       | 1.0                                                                                             |
| **Date de dernière modification** | 05/08/2026                                                                                      |

---

## 1. Objectif

Une alerte n'est pas automatiquement un incident.

La qualification permet de déterminer ce qui s'est réellement produit avant de choisir une réponse.

---

## 2. Questions initiales

Lorsqu'un événement apparaît, il faut notamment rechercher :

* Quel actif est concerné ?
* Quel service est concerné ?
* Quand l'événement a-t-il commencé ?
* Quelle source a généré l'alerte ?
* L'événement est-il reproductible ?
* Existe-t-il des événements associés ?
* L'impact est-il avéré ?
* Existe-t-il un indicateur de compromission ?

---

## 3. Sources

La qualification peut s'appuyer sur :

```text
Zabbix
journaux système
journaux applicatifs
CrowdSec
Fail2ban
ClamAV
AIDE
état des services
```

Les sources disponibles dépendent du système étudié.

---

## 4. Classification

L'événement peut notamment être classé comme :

* faux positif ;
* panne ;
* erreur de configuration ;
* événement attendu ;
* anomalie ;
* événement de sécurité ;
* incident confirmé.

Cette classification peut évoluer pendant l'investigation.

---

## 5. Traçabilité

Les observations importantes doivent être conservées.

Il faut distinguer :

```text
Fait observé
     ≠
Hypothèse
     ≠
Conclusion
```

Cette distinction est essentielle lors d'une investigation.
