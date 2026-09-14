# 03 - Analyse des menaces

| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-menaces.md` |
| **Technologie** | Méthode de conception |
| **Catégorie** | Méthodologie |
| **Objectif** | Définir la démarche permettant d'identifier les menaces pertinentes pour les actifs du laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Principe

Une menace représente un événement ou un acteur susceptible d'exploiter une vulnérabilité ou une faiblesse et de produire un impact sur un actif.

L'analyse doit rester liée au contexte réel du laboratoire.

---

# Sources de menace

Les menaces peuvent notamment provenir :

* d'un attaquant externe ;
* d'un utilisateur disposant d'un accès légitime ;
* d'un compte compromis ;
* d'une mauvaise configuration ;
* d'une vulnérabilité logicielle ;
* d'une erreur humaine ;
* d'une défaillance matérielle ;
* d'une défaillance logicielle.

---

# Méthode

Pour chaque actif :

1. identifier les services et interfaces ;
2. identifier les données manipulées ;
3. identifier les dépendances ;
4. identifier les vulnérabilités potentielles ;
5. identifier les scénarios de compromission ;
6. déterminer les impacts possibles.

---

# Exemples

Pour un serveur web :

```text
Exposition HTTP/HTTPS
        ↓
Vulnérabilité applicative
        ↓
Compromission du service
        ↓
Accès aux données
        ↓
Impact sur l'intégrité ou la confidentialité
```

Pour un service d'administration :

```text
Service exposé
        ↓
Brute force
        ↓
Compromission d'identifiants
        ↓
Accès privilégié
        ↓
Compromission de l'actif
```

---

# Référentiels

L'analyse peut s'appuyer notamment sur :

* MITRE ATT&CK ;
* OWASP ;
* ANSSI ;
* NIST.

Ces référentiels fournissent des connaissances complémentaires mais ne remplacent pas l'analyse du contexte réel du laboratoire.
