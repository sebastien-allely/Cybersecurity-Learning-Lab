# 07 - Références

| Élément | Valeur |
| **Nom du document** | `07-References.md` |
| **Technologie** | CrowdSec |
| **Catégorie** | Architecture |
| **Objectif** | Référencer les sources utilisées pour la conception et l'intégration de CrowdSec dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Documentation et sources techniques

Les références doivent être utilisées pour vérifier les évolutions de CrowdSec, de ses composants et de ses mécanismes de configuration.

* Documentation officielle CrowdSec — architecture, installation et fonctionnement.
* Documentation officielle CrowdSec — Local API (LAPI).
* Documentation officielle CrowdSec — parsers et scénarios.
* Documentation officielle CrowdSec — décisions et remédiation.
* Documentation officielle CrowdSec — supervision et maintenance.

---

# Référentiels de cybersécurité

La conception du laboratoire s'appuie également sur des référentiels généraux de cybersécurité, notamment :

* **ANSSI** — recommandations relatives à la sécurité des systèmes d'information ;
* **NIST Cybersecurity Framework** ;
* **MITRE ATT&CK** ;
* **OWASP**, lorsque les services surveillés concernent des applications ou services web.

Ces référentiels permettent de replacer CrowdSec dans une démarche globale de gestion des risques et de défense en profondeur.

---

# Références internes au laboratoire

Les documents suivants doivent être considérés conjointement avec cette documentation :

```text
docs/01-Methode-de-conception/
docs/02-Architecture/
docs/03-Hardening/
docs/05-Monitoring/
docs/06-Incident-Response/
```

La documentation spécifique à CrowdSec doit rester cohérente avec les choix d'architecture, de supervision et de réponse à incident du laboratoire.

---

# Principe de veille

CrowdSec évoluant régulièrement, les recommandations et configurations doivent être réévaluées lors :

* d'une mise à jour majeure ;
* d'une modification de l'architecture ;
* de l'ajout d'un nouveau service surveillé ;
* d'une modification des scénarios ;
* d'une modification des mécanismes de remédiation ;
* de l'apparition d'une vulnérabilité affectant CrowdSec ou l'un de ses composants.
