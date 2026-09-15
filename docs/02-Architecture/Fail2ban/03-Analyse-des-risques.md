# 03 - Analyse des risques

| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les risques auxquels Fail2ban contribue à répondre et les risques introduits par son fonctionnement. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Risques traités

Fail2ban contribue principalement à réduire les risques associés aux tentatives répétées détectables dans les journaux.

| Risque                                    | Contribution                  |
| ----------------------------------------- | ----------------------------- |
| Brute force SSH                           | Détection et bannissement     |
| Tentatives répétées d'authentification    | Réaction automatique          |
| Comportements hostiles détectables        | Application d'une action      |
| Attaques visant certains services exposés | Protection adaptée au service |

---

# Risques non couverts

Fail2ban ne permet pas de traiter seul :

* une compromission utilisant des identifiants valides ;
* une vulnérabilité applicative ne produisant pas de motif détectable ;
* une attaque ne générant pas les événements attendus ;
* une compromission locale ;
* une attaque nécessitant une analyse comportementale avancée.

---

# Risques propres à Fail2ban

### Faux positifs

Un utilisateur légitime peut atteindre le seuil de déclenchement et être temporairement bloqué.

### Faux négatifs

Un comportement malveillant non couvert par un filtre peut ne pas provoquer de bannissement.

### Défaillance du service

Un Fail2ban arrêté ne peut plus appliquer les protections prévues.

### Mauvaise configuration

Une jail ou un filtre incorrect peut produire une protection inefficace ou provoquer des blocages injustifiés.

---

# Mesures de réduction

Les risques sont réduits par :

* la supervision ;
* la validation des filtres ;
* l'utilisation de seuils adaptés ;
* la documentation des jails ;
* les tests ;
* la sauvegarde des configurations ;
* la maintenance régulière.

Fail2ban doit donc être considéré comme une mesure de réduction du risque et non comme une garantie de sécurité.
