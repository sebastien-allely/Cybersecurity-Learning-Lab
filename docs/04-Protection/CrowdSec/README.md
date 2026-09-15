# CrowdSec — Scénarios et remédiation

| Élément                           | Valeur                                                                                                                          |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                                                     |
| **Technologie**                   | CrowdSec                                                                                                                        |
| **Catégorie**                     | Protection                                                                                                                      |
| **Objectif**                      | Documenter le fonctionnement des scénarios de détection CrowdSec et des mécanismes de remédiation utilisés dans le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                                |
| **Version**                       | 1.0                                                                                                                             |
| **Date de dernière modification** | 05/08/2026                                                                                                                      |

---

## 1. Objectif

CrowdSec constitue un mécanisme de détection et de réponse destiné à identifier des comportements considérés comme malveillants à partir des journaux produits par les systèmes et applications du laboratoire.

Son rôle ne se limite pas à détecter une tentative d'attaque.

La chaîne complète est :

```text
Journal
   ↓
Acquisition
   ↓
Parsing
   ↓
Scénario
   ↓
Détection
   ↓
Décision
   ↓
Remédiation
   ↓
Vérification
   ↓
Supervision
```

Cette organisation permet de distinguer clairement :

* la source de l'événement ;
* son interprétation ;
* la logique de détection ;
* la décision de sécurité ;
* l'action de remédiation ;
* la supervision du résultat.

---

## 2. Scénarios

Un scénario CrowdSec décrit une séquence d'événements correspondant à un comportement donné.

Un scénario ne doit donc pas être considéré comme une simple règle de filtrage.

Il permet notamment de rechercher :

* une répétition d'échecs d'authentification ;
* une succession de requêtes anormales ;
* un comportement correspondant à une attaque connue ;
* une fréquence d'événements incompatible avec un usage normal.

Le scénario transforme les événements issus des journaux en signal de sécurité exploitable.

---

## 3. Remédiation

Lorsqu'un scénario produit une détection, CrowdSec peut générer une décision.

La décision constitue le résultat exploitable par un mécanisme de remédiation.

La chaîne logique est donc :

```text
Événement
    ↓
Scénario
    ↓
Détection
    ↓
Décision
    ↓
Bouncer / mécanisme de remédiation
    ↓
Blocage ou autre action
```

La détection et le blocage sont volontairement considérés comme deux fonctions distinctes.

Cette séparation facilite l'analyse du fonctionnement et permet notamment de vérifier si une détection produit effectivement une action de protection.

---

## 4. Positionnement dans le laboratoire

CrowdSec est utilisé sur plusieurs composants du laboratoire.

Les composants concernés doivent être documentés individuellement dans leur documentation d'architecture et de hardening.

Le présent document décrit le mécanisme général.

Les configurations propres à chaque système doivent rester associées au composant concerné afin d'éviter de mélanger :

* la logique de détection ;
* la configuration du système ;
* la configuration réseau ;
* la configuration de supervision.

---

## 5. Supervision

La présence de CrowdSec ne constitue pas en elle-même une garantie de sécurité.

Le laboratoire supervise notamment l'état du service.

Une panne de CrowdSec doit être considérée comme un événement de sécurité, car elle peut entraîner une perte de capacité de détection ou de protection.

La supervision doit donc permettre de distinguer :

* service opérationnel ;
* service arrêté ;
* erreur de fonctionnement ;
* problème de communication avec la LAPI ;
* anomalie de fonctionnement du mécanisme de protection.

---

## 6. Vérification

Chaque mécanisme de détection ou de remédiation doit être vérifiable.

La validation doit notamment permettre de répondre aux questions suivantes :

* l'événement est-il correctement journalisé ?
* le parser identifie-t-il correctement l'événement ?
* le scénario déclenche-t-il la détection attendue ?
* une décision est-elle créée ?
* le mécanisme de remédiation applique-t-il cette décision ?
* l'événement est-il visible dans la supervision ?
* le comportement normal du service reste-t-il fonctionnel ?

---

## 7. Limites

CrowdSec n'est pas un EDR et ne constitue pas une solution complète de détection comportementale sur les postes.

Il dépend notamment :

* de la qualité des journaux ;
* des parsers utilisés ;
* des scénarios activés ;
* de la disponibilité du service ;
* de la configuration du mécanisme de remédiation.

Une absence de détection ne signifie donc pas nécessairement qu'aucune attaque n'a eu lieu.

---

## 8. Documentation associée

La documentation de CrowdSec doit être lue conjointement avec :

* la documentation d'architecture ;
* la documentation de hardening ;
* les scénarios d'exercices ;
* la documentation de supervision Zabbix.

L'objectif pédagogique est de permettre à l'apprenant de comprendre la chaîne complète **événement → détection → décision → remédiation → supervision**.
