### `docs/06-Incident-Response/03-Collecte-et-preservation.md`

# 03 - Collecte et préservation

| Élément                           | Valeur                                                                                               |
| --------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `03-Collecte-et-preservation.md`                                                                     |
| **Technologie**                   | Incident Response                                                                                    |
| **Catégorie**                     | Incident Response                                                                                    |
| **Objectif**                      | Présenter les principes de collecte et de préservation des éléments nécessaires à une investigation. |
| **Auteur**                        | Sébastien Allely                                                                                     |
| **Version**                       | 1.0                                                                                                  |
| **Date de dernière modification** | 05/08/2026                                                                                           |

---

## 1. Objectif

Une investigation repose sur des éléments observables.

La collecte doit donc chercher à préserver les informations utiles à la compréhension de l'événement.

---

## 2. Sources potentielles

Selon le scénario, les informations peuvent provenir :

* des journaux système ;
* des journaux applicatifs ;
* de Zabbix ;
* de CrowdSec ;
* de Fail2ban ;
* de ClamAV ;
* d'AIDE ;
* de l'état des processus ;
* de l'état des services ;
* des informations réseau disponibles.

---

## 3. Préservation

La collecte doit limiter les modifications inutiles de l'environnement étudié.

Il faut notamment :

* documenter l'heure ;
* identifier le système ;
* noter les commandes utilisées ;
* conserver les résultats pertinents ;
* ne pas modifier inutilement les fichiers étudiés.

---

## 4. Traçabilité

Chaque élément collecté doit pouvoir être associé à :

* sa source ;
* sa date ;
* son système ;
* son contexte ;
* la personne ou l'exercice ayant réalisé la collecte.

---

## 5. Limites du laboratoire

Le laboratoire ne constitue pas à ce stade une plateforme forensic complète.

Les procédures doivent donc être présentées selon les capacités réellement disponibles.

Les extensions futures pourront intégrer des mécanismes spécialisés de collecte et d'analyse.
