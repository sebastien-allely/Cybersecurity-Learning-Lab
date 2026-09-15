# 07 - Références

| Élément | Valeur |
| **Nom du document** | `07-References.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Architecture |
| **Objectif** | Référencer les sources utilisées pour concevoir et maintenir l'intégration de Fail2ban dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Documentation technique

Les références principales sont :

* documentation officielle Fail2ban ;
* documentation des distributions Linux utilisées dans le laboratoire ;
* documentation des services protégés ;
* documentation des mécanismes de filtrage utilisés par les actions Fail2ban.

---

# Références cybersécurité

La conception du laboratoire s'appuie également sur :

* **ANSSI** ;
* **NIST Cybersecurity Framework** ;
* **MITRE ATT&CK** ;
* **OWASP**, lorsque Fail2ban protège un service web.

Ces référentiels permettent de replacer Fail2ban dans une stratégie globale de réduction du risque.

---

# Références internes

La documentation opérationnelle associée à Fail2ban se trouve dans :

```text
docs/04-Protection/Fail2ban/
```

Les éléments d'automatisation sont notamment présents dans :

```text
automation/bash/fail2ban/
```

Cette organisation permet de distinguer :

* la justification et l'architecture ;
* la mise en œuvre opérationnelle ;
* les scripts et fichiers techniques.

---

# Veille

La configuration doit être réévaluée lors :

* d'une mise à jour majeure ;
* d'une modification du service protégé ;
* de la création d'un nouveau filtre ;
* d'une modification des jails ;
* d'une évolution de l'architecture ;
* de la découverte d'une vulnérabilité affectant Fail2ban ou son environnement.

Les références doivent être vérifiées régulièrement afin de maintenir la documentation du laboratoire à jour.
