# 03 - Analyse des risques

| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | CrowdSec |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les risques auxquels CrowdSec répond et les risques liés à son propre fonctionnement dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Risques traités

CrowdSec contribue principalement à réduire les risques associés aux comportements malveillants détectables dans les journaux.

| Risque                                            | Contribution de CrowdSec                             |
| ------------------------------------------------- | ---------------------------------------------------- |
| Tentatives répétées d'authentification            | Détection et décision de blocage selon les scénarios |
| Brute force                                       | Détection comportementale                            |
| Scan ou comportement hostile détectable           | Analyse des événements et scénarios adaptés          |
| Abus d'un service exposé                          | Détection des comportements observables              |
| Répétition d'attaques provenant d'une même source | Centralisation des décisions et remédiation          |

CrowdSec ne couvre cependant que les comportements pouvant être observés et correctement interprétés par sa configuration.

---

# Risques propres à CrowdSec

L'utilisation de CrowdSec introduit également ses propres risques.

### Faux positifs

Une décision incorrecte peut bloquer une source légitime.

Le laboratoire doit donc privilégier une configuration contrôlée et vérifiable.

### Faux négatifs

Un comportement malveillant qui ne correspond à aucun scénario ou qui n'est pas correctement journalisé peut ne pas être détecté.

### Défaillance du service

Si CrowdSec est arrêté ou fonctionne incorrectement, la capacité de détection et de réaction peut être réduite.

### Mauvaise configuration

Une mauvaise configuration des parsers, scénarios ou décisions peut provoquer une détection incorrecte.

### Dépendance aux journaux

Sans événements exploitables, CrowdSec ne peut pas effectuer correctement son analyse.

---

# Niveau de criticité

CrowdSec constitue une **mesure de sécurité importante**, mais sa défaillance ne doit pas provoquer directement une indisponibilité des services protégés.

Le dispositif doit donc être conçu comme une couche complémentaire et non comme un point de dépendance unique.

---

# Mesures de réduction des risques

Les mesures retenues comprennent notamment :

* supervision du service CrowdSec ;
* supervision de la LAPI ;
* contrôle des décisions ;
* contrôle des journaux ;
* validation des scénarios ;
* limitation des privilèges ;
* sauvegarde des configurations ;
* tests après modification de la configuration.
