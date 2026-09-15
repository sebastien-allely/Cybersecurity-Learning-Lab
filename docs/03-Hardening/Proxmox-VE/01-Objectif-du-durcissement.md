# 01 - Objectifs du durcissement


| Élément | Valeur |
| **Nom du document** | `01-Objectif-du-durcissement.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le durcissement (Hardening) consiste à réduire les risques pesant sur un système en supprimant les éléments inutiles, en limitant les possibilités d'attaque et en renforçant les mécanismes de sécurité.

Dans ce référentiel, le durcissement n'est jamais une accumulation de bonnes pratiques. Chaque mesure répond à un risque identifié lors de la phase de conception.

---

# 2. Pourquoi durcir Proxmox VE ?

Proxmox VE constitue le socle de l'infrastructure.

Une compromission de l'hyperviseur peut entraîner :

- la prise de contrôle de toutes les machines virtuelles ;
- la suppression ou l'altération des sauvegardes ;
- l'interruption des services critiques ;
- une compromission de l'ensemble du laboratoire.

Le niveau de protection attendu est donc supérieur à celui des autres composants de l'infrastructure.

---

# 3. Objectifs recherchés

Le durcissement poursuit les objectifs suivants :

- réduire la surface d'attaque ;
- limiter les privilèges accordés aux utilisateurs et aux services ;
- protéger les interfaces d'administration ;
- renforcer l'authentification ;
- améliorer la résilience du système ;
- faciliter la détection des incidents ;
- conserver une architecture simple à maintenir.

Chaque objectif est directement lié aux risques identifiés dans le document **03 - Analyse des risques**.

---

# 4. Principes retenus

Les mesures de durcissement appliquées dans ce référentiel respectent les principes suivants :

## Réduire plutôt qu'ajouter

Chaque fonctionnalité inutile augmente la surface d'attaque.

La première mesure de sécurité consiste donc à supprimer ce qui n'est pas nécessaire.

---

## Privilégier les mécanismes natifs

Lorsqu'une fonctionnalité native répond au besoin, elle est préférée à une solution tierce.

Cette approche permet de :

- réduire les dépendances ;
- simplifier la maintenance ;
- limiter la dette technique.

---

## Justifier chaque mesure

Aucune recommandation n'est retenue uniquement parce qu'elle est considérée comme une bonne pratique.

Chaque mesure doit répondre à une question simple :

> Quel risque cette mesure permet-elle de réduire ?

Si aucune réponse claire ne peut être apportée, la mesure n'est pas retenue.

---

## Conserver un système maintenable

Une mesure de sécurité difficile à maintenir devient rapidement inefficace.

Le référentiel privilégie des configurations :

- simples ;
- documentées ;
- reproductibles ;
- compatibles avec les évolutions futures de Proxmox VE.

---

# 5. Périmètre

Le durcissement présenté dans cette documentation concerne :

- le système Debian hébergeant Proxmox VE ;
- les interfaces d'administration ;
- les mécanismes d'authentification ;
- le stockage ;
- le réseau ;
- les services de l'hyperviseur.

Le durcissement des machines virtuelles est traité dans leur documentation respective.

---

# 6. Ce qui n'est pas couvert

Ne sont pas traités dans cette section :

- la sécurité physique ;
- les politiques organisationnelles ;
- la sécurité des applications hébergées ;
- les solutions EDR/XDR ;
- la sauvegarde ;
- la supervision.

Ces sujets disposent de leur propre documentation dans le référentiel.

---

# 7. Validation

Le durcissement est considéré comme efficace lorsqu'il permet :

- de réduire les risques identifiés ;
- de conserver les fonctionnalités attendues ;
- de faciliter la supervision ;
- de rester compatible avec les futures mises à jour.

Le succès d'un durcissement ne se mesure donc pas au nombre de paramètres modifiés, mais à sa capacité à réduire durablement les risques sans dégrader l'exploitation.

---

# Conclusion

Le durcissement constitue une étape de la conception de la sécurité et non une finalité.

Les chapitres suivants détaillent les mesures retenues, leur justification, leur méthode d'implémentation et leur mode de vérification.

---

# Références

## Référentiels

- ANSSI – Recommandations de sécurité relatives à l'administration sécurisée des systèmes.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.
- Documentation OpenSSH.

## Guides techniques

- SOCLE – Stéphane Robert (bonnes pratiques de sécurisation Linux).
