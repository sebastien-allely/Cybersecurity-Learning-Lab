### `docs/05-Monitoring/README.md`

# Monitoring et supervision

| Élément                           | Valeur                                                                                                                                                              |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                                                                                         |
| **Technologie**                   | Supervision                                                                                                                                                         |
| **Catégorie**                     | Monitoring                                                                                                                                                          |
| **Objectif**                      | Présenter l'organisation de la supervision du Cybersecurity-Learning-Lab et expliquer son rôle dans la détection des événements, des défaillances et des anomalies. |
| **Auteur**                        | Sébastien Allely                                                                                                                                                    |
| **Version**                       | 1.0                                                                                                                                                                 |
| **Date de dernière modification** | 05/08/2026                                                                                                                                                          |

---

# 1. Objectif

La supervision constitue une composante essentielle du **Cybersecurity-Learning-Lab**.

Elle permet de vérifier en permanence l'état des composants du laboratoire, d'identifier les défaillances, d'observer les mécanismes de sécurité et de détecter certains événements pouvant nécessiter une investigation.

La supervision ne constitue toutefois pas un mécanisme de sécurité autonome.

Elle fournit des informations permettant notamment :

* d'identifier une anomalie ;
* de détecter une défaillance ;
* de vérifier le fonctionnement d'une mesure de sécurité ;
* de mesurer l'état d'un système ;
* d'alerter lorsqu'une situation nécessite une intervention ;
* de faciliter le diagnostic ;
* de vérifier le retour à un état nominal.

---

# 2. Positionnement

La supervision intervient après la mise en œuvre des mesures de protection.

La logique générale du laboratoire est :

```text
Architecture
      ↓
Hardening
      ↓
Protection
      ↓
Monitoring
      ↓
Détection
      ↓
Diagnostic
      ↓
Réponse
      ↓
Maintenance
```

La supervision permet ainsi de vérifier que les mesures définies dans les étapes précédentes fonctionnent réellement dans le temps.

---

# 3. Outil de supervision

Le laboratoire utilise **Zabbix** comme solution principale de supervision.

Zabbix permet notamment de superviser :

* les systèmes Linux ;
* les systèmes Windows ;
* Proxmox VE ;
* Active Directory ;
* GLPI ;
* les mécanismes de protection ;
* certains événements de sécurité ;
* les indicateurs techniques et fonctionnels.

La documentation d'architecture de Zabbix présente le choix de l'outil et son rôle dans le laboratoire.

Les éléments techniques utilisés par Zabbix sont conservés dans le dossier :

```text
zabbix/
```

---

# 4. Documentation associée

La supervision est documentée à plusieurs niveaux.

### Architecture

```text
docs/02-Architecture/Zabbix/
```

Décrit le rôle de Zabbix, les actifs concernés, les risques et les décisions d'architecture.

### Monitoring

```text
docs/05-Monitoring/
```

Décrit la stratégie de supervision et son exploitation.

### Éléments techniques

```text
zabbix/
```

Contient les templates, items, triggers, UserParameters, tableaux de bord et autres éléments réellement utilisés dans le laboratoire.

---

# 5. Principes

La supervision repose notamment sur les principes suivants :

* superviser les actifs importants ;
* privilégier les informations utiles à l'exploitation ;
* éviter la collecte de métriques sans objectif ;
* associer les alertes à des situations nécessitant une action ;
* adapter la sévérité à l'impact réel ;
* limiter les faux positifs ;
* superviser les mécanismes de sécurité eux-mêmes ;
* conserver une cohérence entre documentation et configuration ;
* tester les mécanismes de supervision ;
* réévaluer régulièrement leur pertinence.

---

# 6. Limites

Zabbix ne remplace pas :

* un SIEM ;
* un EDR ;
* un antivirus ;
* un système de détection réseau ;
* une plateforme complète de réponse à incident.

La supervision constitue une source d'observation et d'alerte parmi les différents mécanismes du laboratoire.

---

# 7. Parcours de lecture

Il est recommandé de consulter les documents dans l'ordre suivant :

1. [Architecture du monitoring](01-Architecture-du-monitoring.md)
2. [Principes de supervision](02-Principes-de-supervision.md)
3. [Éléments supervisés](03-Elements-supervises.md)
4. [Sévérité et alertes](04-Severite-et-alertes.md)
5. [KPI techniques et fonctionnels](05-KPI-techniques-et-fonctionnels.md)
6. [Tableaux de bord](06-Tableaux-de-bord.md)
7. [Validation et diagnostic](07-Validation-et-diagnostic.md)

---

# 8. Relation avec les exercices

La supervision doit être mise en pratique.

Les exercices pourront notamment demander à l'apprenant :

* d'identifier une alerte ;
* d'analyser une métrique ;
* de rechercher la cause d'une anomalie ;
* de vérifier le fonctionnement d'une mesure de sécurité ;
* de construire ou modifier une supervision ;
* de valider le retour à l'état nominal.
