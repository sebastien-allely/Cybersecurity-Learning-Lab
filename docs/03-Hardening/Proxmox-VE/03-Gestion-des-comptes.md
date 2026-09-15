# 03 - Gestion des comptes


| Élément | Valeur |
| **Nom du document** | `03-Gestion-des-comptes.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La sécurité d'un système repose en grande partie sur la maîtrise des identités disposant d'un accès à l'administration.

L'objectif n'est pas de multiplier les mécanismes d'authentification, mais de garantir que chaque compte possède uniquement les droits nécessaires à sa mission.

La gestion des comptes applique le principe du moindre privilège afin de limiter les conséquences d'une compromission.

---

# 2. Risques traités

Une mauvaise gestion des comptes peut conduire notamment à :

- une compromission de l'hyperviseur ;
- une élévation de privilèges ;
- une utilisation non tracée des droits administrateur ;
- une difficulté d'attribution des actions réalisées ;
- une augmentation de la surface d'attaque.

---

# 3. Principes de conception

## Chaque compte doit avoir une justification

La première question n'est pas :

> Comment créer un compte ?

mais :

> Pourquoi ce compte doit-il exister ?

Un compte sans justification métier ou technique ne doit pas être créé.

---

## Un compte correspond à une responsabilité

Les comptes nominatifs sont privilégiés.

Ils permettent :

- d'assurer la traçabilité des actions ;
- de faciliter les audits ;
- d'identifier rapidement l'origine d'une opération d'administration.

Les comptes partagés sont évités autant que possible.

---

## Les privilèges sont limités

Un utilisateur ne reçoit que les droits nécessaires.

Les privilèges supplémentaires ne sont accordés que lorsqu'ils répondent à un besoin clairement identifié.

---

## Les droits doivent être révisés

Les besoins évoluent.

Les privilèges doivent donc être réévalués régulièrement afin d'éviter l'accumulation de droits inutiles.

---

# 4. Questions de conception

Avant toute création d'un compte, les questions suivantes doivent être étudiées.

## Pourquoi ce compte est-il nécessaire ?

Quel besoin fonctionnel ou technique justifie son existence ?

---

## Quel actif doit-il administrer ?

Le compte intervient-il sur :

- l'hyperviseur ;
- les machines virtuelles ;
- le stockage ;
- le réseau ;
- les sauvegardes ?

---

## Quel est son niveau de criticité ?

Une compromission de ce compte permettrait-elle :

- d'arrêter des machines virtuelles ;
- de supprimer des sauvegardes ;
- de modifier la configuration réseau ;
- d'obtenir un accès complet à l'infrastructure ?

---

## Quels privilèges sont réellement nécessaires ?

Le principe retenu est :

> minimum de privilèges, maximum de traçabilité.

---

## Comment ce compte sera-t-il supervisé ?

Les événements suivants peuvent être surveillés :

- tentative d'authentification ;
- échec d'authentification ;
- élévation de privilège ;
- suppression ;
- création ;
- modification.

---

# 5. Mesures retenues

Le référentiel recommande notamment :

- privilégier les comptes nominatifs ;
- limiter le nombre de comptes administrateurs ;
- supprimer les comptes inutilisés ;
- documenter chaque compte privilégié ;
- revoir régulièrement les privilèges.

Ces mesures devront être adaptées au contexte de l'infrastructure.

---

# 6. Vérification

Une revue périodique doit permettre de vérifier :

- la liste des comptes existants ;
- leur justification ;
- leurs privilèges ;
- leur dernière utilisation ;
- leur appartenance aux groupes d'administration.

Toute anomalie doit être analysée avant correction.

---

# 7. Supervision

La supervision peut porter sur :

- les échecs d'authentification ;
- les créations de comptes ;
- les suppressions ;
- les modifications de privilèges ;
- les connexions administrateur inhabituelles.

Les alertes doivent être conçues de manière à limiter les faux positifs et à conserver une forte valeur opérationnelle.

---

# Conclusion

La gestion des comptes ne consiste pas uniquement à créer des utilisateurs.

Elle consiste à concevoir un modèle d'administration où chaque identité possède une justification, des privilèges adaptés et une traçabilité permettant d'assurer la sécurité de l'infrastructure.

---

# Références

## Référentiels

- ANSSI – Guide d'administration sécurisée.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.
- Documentation PAM.

## Guides techniques

- SOCLE – Stéphane Robert (gestion des comptes et principe du moindre privilège).
