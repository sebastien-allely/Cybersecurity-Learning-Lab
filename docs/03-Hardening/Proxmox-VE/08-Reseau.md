# 08 - Réseau


| Élément | Valeur |
| **Nom du document** | `08-Reseau.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le réseau constitue le principal vecteur d'interaction avec un hyperviseur.

Une architecture réseau inadaptée peut exposer inutilement des services d'administration, faciliter les déplacements latéraux d'un attaquant ou compromettre la disponibilité de l'infrastructure.

L'objectif est de réduire la surface d'attaque tout en maintenant un niveau de disponibilité compatible avec les besoins opérationnels.

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- les interfaces réseau de l'hyperviseur ;
- les bridges Proxmox VE ;
- les interfaces de management ;
- les réseaux des machines virtuelles ;
- les services réseau de l'hyperviseur ;
- les flux d'administration.

---

# 3. Risques identifiés

Une architecture réseau inadaptée peut entraîner :

- l'exposition de services sensibles ;
- une compromission de l'hyperviseur ;
- des déplacements latéraux entre réseaux ;
- une interception des flux ;
- une perte de disponibilité.

---

# 4. Principes de conception

## Le réseau est une frontière de sécurité

Le réseau ne doit pas uniquement transporter des données.

Il participe activement à la réduction de la surface d'attaque.

Chaque nouveau flux augmente potentiellement cette surface.

---

## Limiter les services exposés

Seuls les services nécessaires à l'administration et au fonctionnement de Proxmox VE doivent être accessibles.

Tout service inutile doit être supprimé ou désactivé après analyse.

---

## Séparer les usages

Lorsque l'architecture le permet, il est recommandé de distinguer :

- le réseau d'administration ;
- le trafic des machines virtuelles ;
- les flux de sauvegarde ;
- les flux de supervision ;
- les flux de réplication ou de cluster.

Cette séparation limite les impacts en cas de compromission.

---

## Contrôler les communications

Chaque flux réseau doit répondre à une nécessité opérationnelle.

Tout flux non justifié augmente la surface d'attaque et doit être remis en question.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- limiter les interfaces exposées ;
- documenter les flux réseau ;
- réduire les communications inutiles ;
- contrôler les accès d'administration ;
- privilégier une segmentation lorsque le contexte technique le permet ;
- documenter les exceptions.

---

# 6. Vérification

Les contrôles doivent notamment permettre de vérifier :

- les interfaces réseau actives ;
- les ports en écoute ;
- les services exposés ;
- les règles de filtrage ;
- les communications attendues entre les différents composants.

Toute exposition non justifiée doit être analysée.

---

# 7. Supervision

La supervision peut permettre de détecter :

- l'indisponibilité d'une interface réseau ;
- une augmentation anormale du trafic ;
- une perte de connectivité ;
- un changement d'adresse IP ;
- une indisponibilité de l'interface d'administration ;
- un comportement réseau inhabituel.

Les alertes doivent être limitées aux événements présentant une réelle valeur opérationnelle.

---

# 8. Bonnes pratiques de conception

Avant de créer un nouveau flux réseau, il convient de répondre aux questions suivantes :

- Quel actif communique ?
- Pourquoi cette communication est-elle nécessaire ?
- Quel risque apparaît si ce flux est autorisé ?
- Ce flux peut-il être limité ?
- Peut-il être segmenté ?
- Comment sera-t-il supervisé ?
- Est-il documenté ?

Une communication réseau non justifiée constitue une augmentation de la surface d'attaque.

---

# 9. Conclusion

La sécurisation du réseau ne repose pas uniquement sur des règles de filtrage.

Elle consiste avant tout à concevoir une architecture où chaque communication possède une justification, où chaque exposition est maîtrisée et où chaque flux peut être expliqué, contrôlé et supervisé.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.

## Guides techniques

- SOCLE – Stéphane Robert (durcissement réseau des systèmes Linux).

## Veille

Toute évolution des mécanismes réseau de Proxmox VE ou des recommandations officielles devra être analysée avant son intégration au référentiel.
