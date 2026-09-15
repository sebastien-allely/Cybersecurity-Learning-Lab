# 06 - Justification des décisions

| Élément | Valeur |
| **Nom du document** | `06-Justification-des-decisions.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Architecture |
| **Objectif** | Documenter les principes guidant la conception, la configuration et l'exploitation de Fail2ban dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Protection ciblée

Fail2ban doit être utilisé uniquement lorsque le risque et les événements observables justifient son activation.

Une jail n'est pas activée simplement parce qu'elle existe dans la documentation ou dans le paquet.

---

# Seuils et durées

Les paramètres tels que :

* `maxretry` ;
* `findtime` ;
* `bantime`

doivent être définis en fonction du service et du risque traité.

Ils doivent éviter de provoquer une réaction disproportionnée.

---

# Filtres personnalisés

Le laboratoire autorise la création de filtres personnalisés lorsque les filtres existants sont insuffisants.

Tout filtre personnalisé doit être :

* documenté ;
* testé ;
* associé à un service identifié ;
* vérifié après modification.

Les filtres ne doivent pas être développés uniquement sur la base d'une hypothèse : ils doivent correspondre aux événements réellement présents dans les journaux.

---

# Protection des configurations

Les fichiers de configuration doivent être **protégés et sauvegardés**.

Les modifications doivent être documentées afin de permettre :

* leur compréhension ;
* leur reproduction ;
* leur restauration ;
* leur audit.

---

# Supervision

Fail2ban doit être supervisé.

Le principe retenu est simple :

> Une protection de sécurité doit également être surveillée.

Une défaillance silencieuse de Fail2ban réduirait la protection attendue.

---

# Complémentarité avec CrowdSec

Fail2ban et CrowdSec peuvent répondre à des besoins similaires sur certains systèmes, mais ils ne doivent pas être considérés comme strictement équivalents.

Le laboratoire conserve les deux technologies comme outils distincts :

* Fail2ban : protection ciblée fondée sur les journaux et les jails ;
* CrowdSec : détection comportementale et mécanisme de décision plus large.

Le choix de l'un ou de l'autre doit être justifié par le contexte.

---

# Décision d'architecture

Fail2ban est retenu comme mécanisme de **protection locale ciblée**, léger et maîtrisable, venant compléter les autres mécanismes de sécurité du laboratoire.
