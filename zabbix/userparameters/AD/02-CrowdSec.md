# Supervision CrowdSec — Active Directory

| Élément                           | Valeur                                                                                                                                                      |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `02-CrowdSec.md`                                                                                                                                            |
| **Technologie**                   | CrowdSec / Zabbix Agent 2                                                                                                                                   |
| **Catégorie**                     | Supervision                                                                                                                                                 |
| **Objectif**                      | Décrire les éléments CrowdSec à superviser sur la machine Windows hébergeant Active Directory et distinguer le moteur CrowdSec du mécanisme de remédiation. |
| **Auteur**                        | Sébastien Allely                                                                                                                                            |
| **Version**                       | 1.0                                                                                                                                                         |
| **Date de dernière modification** | 10/08/2026                                                                                                                                                  |

---

## 1. Périmètre

La machine Active Directory du laboratoire héberge également **CrowdSec**.

La supervision CrowdSec doit être considérée comme complémentaire à la supervision Active Directory décrite dans :

```text
ad-monitoring.conf
```

Les deux fonctions ne doivent pas être confondues :

* les UserParameters `ad.*` supervisent les fonctions Active Directory ;
* les contrôles CrowdSec permettent de vérifier le fonctionnement du mécanisme de détection et de protection ;
* le bouncer Windows assure l'application locale des décisions de remédiation.

---

## 2. Architecture

Le fonctionnement peut être représenté de la manière suivante :

```text
                    ┌──────────────────────────┐
                    │      CrowdSec Engine     │
                    │      sur la machine AD   │
                    └────────────┬─────────────┘
                                 │
                                 │ décisions
                                 ▼
                    ┌──────────────────────────┐
                    │   Windows Firewall       │
                    │   CrowdSec Bouncer       │
                    └──────────────────────────┘
                                 │
                                 ▼
                         Trafic réseau bloqué
```

Le bouncer ne remplace pas le moteur CrowdSec.

Une défaillance du moteur et une défaillance du bouncer doivent donc être considérées comme deux événements distincts.

---

## 3. Éléments à superviser

La supervision doit au minimum permettre de détecter :

### Service CrowdSec

Vérifier que le service CrowdSec est démarré et fonctionnel.

Une indisponibilité du service signifie que les événements ne peuvent plus être traités normalement par le moteur CrowdSec.

### Bouncer Windows

Le bouncer doit être présent et fonctionnel.

Il constitue le mécanisme chargé d'appliquer localement les décisions de blocage.

La présence d'un bouncer ne garantit cependant pas que le moteur CrowdSec fonctionne correctement.

### Communication avec la LAPI

Lorsque cette information est exposée par l'agent, elle permet de vérifier que le composant CrowdSec peut communiquer avec sa Local API.

Cette vérification est différente d'une simple vérification du processus ou du service.

### Décisions de remédiation

La présence de décisions permet de vérifier que le système de remédiation est capable de recevoir ou d'appliquer des blocages.

Cette métrique ne doit cependant pas être utilisée seule pour déterminer l'état de santé de CrowdSec : l'absence de décision peut simplement signifier qu'aucune activité nécessitant une remédiation n'a été observée.

---

## 4. Interprétation

Les contrôles doivent être interprétés ensemble.

| État                                 | Interprétation possible                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------- |
| Service arrêté                       | CrowdSec n'est plus opérationnel                                             |
| Service actif + bouncer indisponible | Détection potentiellement fonctionnelle mais remédiation locale indisponible |
| Service actif + bouncer actif        | Fonctionnement nominal des composants principaux                             |
| Service actif + problème LAPI        | Communication interne à CrowdSec à diagnostiquer                             |
| Aucune décision                      | Pas nécessairement une anomalie                                              |
| Ancienne activité                    | Ne constitue pas à elle seule une preuve d'indisponibilité                   |

Une supervision correcte doit donc éviter les alertes basées uniquement sur l'absence d'activité.

---

## 5. Relation avec Zabbix

Les éléments de supervision Zabbix doivent être associés à la cible Active Directory.

La configuration spécifique à Active Directory se trouve dans :

```text
zabbix/userparameters/AD/ad-monitoring.conf
```

Les éventuels UserParameters spécifiques à CrowdSec doivent être ajoutés à cette cible uniquement après validation de leur présence et de leur fonctionnement sur Windows.

Il ne faut pas recopier automatiquement les UserParameters CrowdSec Linux utilisés sur les autres machines.

---

## 6. Principe de sécurité

Les commandes exécutées par Zabbix Agent 2 doivent rester limitées au strict nécessaire.

Une commande de supervision ne doit pas permettre à un utilisateur distant de déclencher arbitrairement une commande PowerShell.

Toute modification d'un UserParameter CrowdSec doit donc être :

1. documentée ;
2. testée localement ;
3. validée avec Zabbix Agent 2 ;
4. intégrée au template Zabbix correspondant ;
5. documentée dans le dépôt.

---

## 7. Documentation associée

Les éléments suivants sont complémentaires :

* `ad-monitoring.conf` — UserParameters Active Directory ;
* documentation CrowdSec du laboratoire — fonctionnement, scénarios et remédiation ;
* documentation Zabbix — éléments supervisés, seuils et alertes ;
* templates Zabbix présents dans `zabbix/templates/`.

Le présent document décrit le **périmètre de supervision CrowdSec sur la cible AD**. Il ne contient pas la configuration complète de CrowdSec ni celle du bouncer.
