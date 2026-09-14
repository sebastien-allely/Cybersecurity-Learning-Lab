# 05 - Événements observables


| Élément | Valeur |
| **Nom du document** | `06-Justification-des-decisions.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Tous les événements produits par Apache n'ont pas vocation à être supervisés.

L'objectif est d'identifier uniquement ceux permettant :

- de détecter une défaillance ;
- d'identifier une tentative de compromission ;
- de constater une dérive de fonctionnement ;
- de faciliter l'analyse d'un incident.

Cette sélection permet de limiter les faux positifs et de concentrer la supervision sur les événements réellement utiles.

---

# 2. Principes de conception

Un événement est considéré comme observable lorsqu'il répond aux critères suivants :

- il est produit de manière fiable ;
- il est exploitable par un outil de supervision ou un SIEM ;
- il possède une valeur opérationnelle ;
- il permet une prise de décision.

Un événement ne répondant pas à ces critères ne doit pas être intégré au référentiel.

---

# 3. Événements liés à la disponibilité

Les événements suivants permettent de vérifier la disponibilité du serveur :

- arrêt du service Apache ;
- redémarrage inattendu ;
- échec de démarrage ;
- indisponibilité du port HTTPS ;
- indisponibilité du site publié.

Ces événements doivent être considérés comme prioritaires.

---

# 4. Événements liés à la sécurité

Les événements suivants peuvent traduire une activité malveillante ou une mauvaise configuration :

- erreurs d'authentification répétées sur une interface protégée ;
- accès répétés à des ressources inexistantes (404) pouvant traduire une phase de reconnaissance ;
- requêtes bloquées par un mécanisme de protection (le cas échéant) ;
- tentatives d'accès à des répertoires sensibles ;
- erreurs TLS répétées ;
- modifications inattendues des fichiers de configuration (si un contrôle d'intégrité est déployé).

Ces événements doivent être analysés dans leur contexte afin d'éviter les faux positifs.

---

# 5. Événements liés aux performances

Une dégradation des performances peut révéler :

- une surcharge ;
- un dysfonctionnement applicatif ;
- une attaque par déni de service ;
- une saturation des ressources.

Les indicateurs suivants peuvent être observés :

- augmentation anormale du nombre de connexions ;
- temps de réponse inhabituel ;
- saturation CPU ;
- saturation mémoire.

---

# 6. Événements liés aux certificats

Les certificats TLS doivent faire l'objet d'une surveillance particulière.

Les événements pertinents comprennent notamment :

- expiration prochaine d'un certificat ;
- certificat expiré ;
- certificat invalide ;
- échec de chargement d'un certificat.

---

# 7. Critères de sélection

Avant d'ajouter un nouvel événement au référentiel, il convient de répondre aux questions suivantes :

- Quel risque permet-il de détecter ?
- Une action peut-elle être entreprise ?
- L'événement est-il reproductible ?
- Le taux de faux positifs est-il acceptable ?
- Existe-t-il déjà un événement équivalent ?

Si la réponse à ces questions est négative, l'événement ne doit pas être retenu.

---

# 8. Vérification

Une revue régulière doit permettre de vérifier :

- que les événements retenus restent disponibles ;
- qu'ils correspondent toujours aux risques identifiés ;
- qu'ils ne génèrent pas d'alertes inutiles ;
- qu'ils permettent effectivement une réaction opérationnelle.

---

# 9. Conclusion

L'observation des événements constitue le lien entre la conception de la sécurité et la supervision.

Le référentiel ne cherche pas à collecter un maximum d'informations, mais à identifier les événements permettant de détecter rapidement un incident ou une dérive de fonctionnement.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- MITRE ATT&CK (phases de reconnaissance et d'exploitation).

## Documentation officielle

- Apache HTTP Server Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (journalisation, supervision et durcissement des services Linux).

## Veille

Les événements observés devront être réévalués lors de l'ajout de nouveaux modules, de nouvelles applications publiées ou de nouvelles capacités de journalisation.
