### `docs/05-Monitoring/07-Validation-et-diagnostic.md`

# 07 - Validation et diagnostic

| Élément                           | Valeur                                                                            |
| --------------------------------- | --------------------------------------------------------------------------------- |
| **Nom du document**               | `07-Validation-et-diagnostic.md`                                                  |
| **Technologie**                   | Zabbix                                                                            |
| **Catégorie**                     | Monitoring                                                                        |
| **Objectif**                      | Définir une méthode de validation et de diagnostic des mécanismes de supervision. |
| **Auteur**                        | Sébastien Allely                                                                  |
| **Version**                       | 1.0                                                                               |
| **Date de dernière modification** | 05/08/2026                                                                        |

---

## 1. Validation

Une supervision n'est considérée comme opérationnelle qu'après validation.

La validation doit vérifier :

1. la collecte ;
2. la condition normale ;
3. la condition anormale ;
4. le déclenchement ;
5. la sévérité ;
6. le message ;
7. la récupération.

---

## 2. Méthode de diagnostic

Lorsqu'une alerte apparaît, il faut éviter de modifier immédiatement la configuration.

La démarche recommandée est :

```text
Alerte
  ↓
Vérification de l'événement
  ↓
Identification de l'actif
  ↓
Identification de la cause probable
  ↓
Vérification du système concerné
  ↓
Analyse des journaux
  ↓
Correction
  ↓
Vérification
  ↓
Retour à l'état nominal
```

---

## 3. Différencier panne et incident de sécurité

Une alerte de supervision ne doit pas être automatiquement considérée comme un incident de sécurité.

Il faut rechercher les éléments permettant de distinguer :

* panne ;
* erreur de configuration ;
* maintenance ;
* saturation ;
* comportement anormal ;
* événement de sécurité ;
* compromission potentielle.

Cette distinction permet d'éviter les conclusions hâtives.

---

## 4. Corrélation

Lorsqu'un événement est détecté, les informations provenant de plusieurs sources doivent être comparées lorsque cela est pertinent.

Exemples :

```text
Zabbix
  +
journaux système
  +
CrowdSec
  +
Fail2ban
  +
service concerné
```

Cette corrélation permet d'améliorer la compréhension de la situation.

---

## 5. Validation après correction

Après une correction, il faut vérifier :

* la disparition de l'alerte ;
* le retour des données ;
* le fonctionnement du service ;
* le fonctionnement du mécanisme de sécurité ;
* l'absence d'effet secondaire.

La résolution d'une alerte ne doit donc pas être confondue avec la simple disparition du trigger.
