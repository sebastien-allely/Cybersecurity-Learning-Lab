# 01 - Justification de l'outil


| Élément | Valeur |
| **Nom du document** | `01-Justification-de-l-outil.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Avant de sécuriser un composant, il convient de justifier son existence dans l'infrastructure.

Cette justification permet de comprendre :

- le rôle du serveur ;
- les besoins auxquels il répond ;
- les impacts de son indisponibilité ;
- les risques liés à son exposition.

---

# 2. Présentation

Apache HTTP Server est un serveur Web Open Source développé par l'Apache Software Foundation.

Il permet de publier des applications Web et de fournir des services HTTP et HTTPS à destination des utilisateurs ou d'autres composants de l'infrastructure.

---

# 3. Pourquoi Apache ?

Le choix d'Apache repose sur plusieurs critères.

## Maturité

Apache est l'un des serveurs Web les plus utilisés au monde.

Son développement est actif et bénéficie d'une importante communauté.

---

## Stabilité

Apache est reconnu pour sa robustesse dans des environnements de production.

Il s'intègre naturellement aux distributions Linux utilisées dans le référentiel.

---

## Compatibilité

Apache est compatible avec :

- PHP ;
- TLS ;
- LDAP ;
- Reverse Proxy ;
- Virtual Hosts ;
- HTTP/2 (et les versions ultérieures supportées).

Cette polyvalence permet de répondre à de nombreux besoins sans ajouter de composants inutiles.

---

## Documentation

Apache bénéficie :

- d'une documentation officielle complète ;
- d'une communauté très active ;
- de nombreux retours d'expérience.

Cette richesse documentaire facilite sa maintenance.

---

# 4. Cas d'usage dans le laboratoire

Dans cette infrastructure, Apache est utilisé principalement pour publier :

- GLPI01 ;
- les interfaces Web nécessaires à l'administration de certains services.

Il ne constitue pas une plateforme d'hébergement généraliste.

---

# 5. Actifs protégés

Apache participe directement à la protection de plusieurs actifs :

- applications Web ;
- authentification des utilisateurs ;
- données échangées via HTTPS ;
- disponibilité des services publiés.

---

# 6. Limites

Apache ne constitue pas un mécanisme de sécurité à lui seul.

Il ne remplace pas :

- un pare-feu ;
- une authentification forte ;
- un WAF ;
- une supervision ;
- une stratégie de sauvegarde.

Sa sécurisation doit être intégrée dans une démarche globale.

---

# 7. Pourquoi ne pas avoir retenu une autre solution ?

Le choix d'un serveur Web dépend du contexte technique.

D'autres solutions telles que Nginx ou Caddy répondent également à des besoins similaires.

Le présent référentiel ne cherche pas à démontrer qu'Apache est supérieur à ces solutions.

Il justifie uniquement pourquoi Apache répond aux besoins identifiés dans cette infrastructure.

---

# 8. Conclusion

Apache constitue un composant mature, stable et largement documenté permettant de publier des services Web de manière fiable.

Son intégration dans le référentiel est motivée par son rôle dans l'architecture et non par sa popularité.

---

# Références

## Documentation officielle

- Apache HTTP Server Documentation.

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.

## Veille

Toute évolution majeure d'Apache ou de son modèle de sécurité devra être analysée avant d'être intégrée au référentiel.
