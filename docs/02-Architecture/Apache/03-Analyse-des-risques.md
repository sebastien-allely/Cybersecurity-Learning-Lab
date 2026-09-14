# 03 - Analyse des risques


| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Architecture |
| **Objectif** | Analyser les risques associés à Apache HTTP Server et déterminer les mesures permettant de les réduire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La sécurisation d'un serveur Web ne consiste pas à appliquer systématiquement des recommandations de durcissement.

Elle consiste d'abord à comprendre :

- les actifs exposés ;
- les menaces susceptibles de les affecter ;
- les conséquences d'une compromission ;
- les mesures permettant de réduire les risques.

Cette analyse constitue le point de départ des décisions de sécurité présentées dans le reste du référentiel.

---

# 2. Contexte

Apache constitue le point d'entrée des applications Web publiées.

Selon son niveau d'exposition, il peut être accessible :

- uniquement depuis le réseau interne ;
- depuis un réseau d'administration ;
- depuis Internet.

Plus l'exposition est importante, plus la surface d'attaque augmente.

---

# 3. Menaces identifiées

Les principales menaces sont les suivantes :

## Compromission d'une application Web

Une vulnérabilité dans une application publiée peut permettre à un attaquant de compromettre le serveur ou d'accéder aux données.

---

## Exploitation d'une vulnérabilité Apache

Une vulnérabilité affectant Apache ou un module chargé peut permettre une élévation de privilèges, un déni de service ou une exécution de code.

---

## Mauvaise configuration

Une configuration inadaptée peut entraîner :

- l'exposition d'informations sensibles ;
- un accès non autorisé ;
- un affaiblissement des mécanismes de sécurité.

---

## Attaques sur les services HTTP/HTTPS

Un serveur Web peut être la cible de :

- scans automatisés ;
- tentatives d'exploitation ;
- attaques par force brute sur les interfaces d'administration ;
- dénis de service ;
- exploitation de mauvaises configurations.

---

## Compromission des certificats

La compromission ou l'expiration d'un certificat peut affecter :

- la confidentialité ;
- l'intégrité ;
- l'authenticité des communications.

---

# 4. Impacts

Une compromission peut entraîner :

- une indisponibilité des applications ;
- une fuite d'informations ;
- une modification des contenus publiés ;
- un point d'appui pour un déplacement latéral ;
- une perte de confiance dans les services.

---

# 5. Principes de réduction des risques

Le référentiel retient les principes suivants :

- réduire la surface d'attaque ;
- limiter les composants installés ;
- maintenir le serveur à jour ;
- protéger les communications ;
- superviser les événements pertinents ;
- documenter les décisions de sécurité.

---

# 6. Risques résiduels

Même correctement durci, Apache reste exposé à certains risques :

- vulnérabilités inconnues (zero-day) ;
- erreurs humaines ;
- compromission d'une application Web ;
- attaques par déni de service ;
- compromission d'un composant tiers.

Ces risques doivent être pris en compte dans la stratégie globale de sécurité.

---

# 7. Vérification

L'analyse des risques doit être réévaluée lors des événements suivants :

- publication d'une nouvelle application ;
- modification importante de l'architecture ;
- changement du niveau d'exposition ;
- découverte d'une vulnérabilité critique ;
- évolution des besoins métier.

---

# 8. Conclusion

La sécurisation d'Apache ne repose pas sur une liste de paramètres techniques.

Elle repose sur une compréhension des risques liés à son rôle de serveur Web, de son exposition et des actifs qu'il protège.

Les mesures de durcissement présentées dans la suite du référentiel auront pour objectif de réduire les risques identifiés dans cette analyse.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- EBIOS Risk Manager (ANSSI).
- NIST Cybersecurity Framework.
- ISO/IEC 27005 (gestion des risques liés à la sécurité de l'information).

## Documentation officielle

- Apache HTTP Server Documentation.

## Veille

L'analyse des risques devra être révisée lors de toute évolution significative de l'architecture, des applications publiées ou des menaces affectant Apache HTTP Server.
