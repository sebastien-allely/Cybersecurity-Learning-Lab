### `docs/05-Monitoring/05-KPI-techniques-et-fonctionnels.md`

# 05 - KPI techniques et fonctionnels

| Élément                           | Valeur                                                                                                                    |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `05-KPI-techniques-et-fonctionnels.md`                                                                                    |
| **Technologie**                   | Zabbix                                                                                                                    |
| **Catégorie**                     | Monitoring                                                                                                                |
| **Objectif**                      | Distinguer les indicateurs techniques des indicateurs permettant d'évaluer le fonctionnement des services du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                          |
| **Version**                       | 1.0                                                                                                                       |
| **Date de dernière modification** | 05/08/2026                                                                                                                |

---

## 1. KPI techniques

Les KPI techniques permettent de suivre l'état des infrastructures.

Ils peuvent notamment concerner :

* disponibilité ;
* CPU ;
* mémoire ;
* stockage ;
* espace disque ;
* réseau ;
* charge ;
* état des services ;
* état des agents ;
* sauvegardes.

Ils permettent d'identifier les dégradations et les tendances.

---

## 2. KPI fonctionnels

Les KPI fonctionnels cherchent à déterminer si une fonction attendue du laboratoire est opérationnelle.

Ils peuvent notamment porter sur :

* disponibilité d'un service ;
* fonctionnement d'un mécanisme d'authentification ;
* fonctionnement d'une supervision ;
* fonctionnement d'une mesure de protection ;
* réussite d'une opération attendue ;
* capacité de récupération après une défaillance.

---

## 3. Différence

Un indicateur technique répond principalement à :

> Comment fonctionne l'infrastructure ?

Un indicateur fonctionnel répond davantage à :

> La fonction attendue fonctionne-t-elle réellement ?

Les deux niveaux sont complémentaires.

---

## 4. Utilisation pédagogique

Les KPI permettent également d'apprendre à distinguer :

* une métrique ;
* un seuil ;
* une alerte ;
* un indicateur ;
* un objectif opérationnel.

L'apprenant doit être capable d'expliquer pourquoi un indicateur est collecté et quelle décision il permet de prendre.

---

## 5. Évolution

Les KPI doivent être réévalués lorsque le laboratoire évolue.

Un indicateur qui ne permet aucune action ou analyse utile doit être supprimé ou remplacé.
