# 05 - Mises à jour


| Élément | Valeur |
| **Nom du document** | `05-Mises-a-jour.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les mises à jour permettent de corriger des vulnérabilités, d'améliorer la stabilité du système et de maintenir la compatibilité avec les composants de l'infrastructure.

L'objectif n'est pas d'installer systématiquement la dernière version disponible, mais de maintenir un niveau de sécurité adapté aux risques identifiés tout en préservant la disponibilité des services.

---

# 2. Actifs concernés

Les mises à jour peuvent impacter :

- l'hyperviseur Proxmox VE ;
- le noyau Linux ;
- les services Proxmox ;
- les machines virtuelles hébergées ;
- le stockage ;
- le cluster (le cas échéant).

---

# 3. Risques identifiés

Une mauvaise gestion des mises à jour peut entraîner :

- l'exploitation d'une vulnérabilité connue ;
- une indisponibilité de l'hyperviseur ;
- une incompatibilité logicielle ;
- une interruption des machines virtuelles ;
- une perte de fonctionnalités.

À l'inverse, appliquer une mise à jour sans préparation peut provoquer une régression fonctionnelle ou une indisponibilité non maîtrisée.

---

# 4. Principes de conception

## Les mises à jour répondent à un besoin

Chaque mise à jour doit avoir une justification :

- correction de vulnérabilités ;
- correction de bogues ;
- amélioration de la stabilité ;
- évolution fonctionnelle nécessaire.

Une mise à jour ne doit pas être appliquée uniquement parce qu'une nouvelle version est disponible.

---

## La disponibilité reste prioritaire

La sécurité ne doit pas compromettre inutilement la disponibilité de l'infrastructure.

Lorsque cela est possible, les mises à jour sont planifiées pendant une période de maintenance.

---

## Les dépendances doivent être connues

Avant toute mise à jour, il convient d'identifier :

- les composants concernés ;
- les dépendances ;
- les impacts possibles sur les machines virtuelles ;
- les impacts sur les sauvegardes ;
- les impacts sur le cluster.

---

## Une stratégie de retour arrière doit exister

Avant toute opération importante, il convient de vérifier :

- qu'une sauvegarde récente est disponible ;
- que la restauration a déjà été testée ;
- qu'une procédure de retour arrière est documentée.

Une sauvegarde non testée ne constitue pas une garantie de reprise.

---

# 5. Décisions retenues

Le référentiel adopte les principes suivants :

- maintenir le système à jour ;
- appliquer en priorité les correctifs de sécurité ;
- documenter les mises à jour majeures ;
- planifier les interruptions de service ;
- vérifier le bon fonctionnement après chaque intervention.

---

# 6. Vérification

Après une mise à jour, les contrôles suivants doivent être réalisés :

- état des services Proxmox ;
- accès à l'interface Web ;
- fonctionnement des machines virtuelles ;
- état du stockage ;
- état du cluster (le cas échéant) ;
- consultation des journaux système ;
- vérification de l'absence d'erreurs critiques.

Une mise à jour n'est considérée comme terminée qu'après validation de ces contrôles.

---

# 7. Supervision

La supervision peut notamment permettre de détecter :

- un redémarrage inattendu de l'hyperviseur ;
- l'arrêt d'un service critique ;
- une indisponibilité de l'API Proxmox ;
- une dégradation des performances après mise à jour ;
- des erreurs répétées dans les journaux système.

L'objectif est de détecter rapidement une régression introduite par une mise à jour.

---

# 8. Bonnes pratiques de conception

Avant d'appliquer une mise à jour, il est recommandé de répondre aux questions suivantes :

- Pourquoi cette mise à jour est-elle nécessaire ?
- Corrige-t-elle une vulnérabilité identifiée ?
- Quels actifs seront impactés ?
- Une interruption de service est-elle attendue ?
- Une sauvegarde récente est-elle disponible ?
- La restauration a-t-elle déjà été testée ?
- Comment vérifier le succès de l'opération ?

Ces questions permettent d'intégrer la gestion des mises à jour dans une démarche de maîtrise des risques plutôt que dans une logique d'application systématique.

---

# 9. Conclusion

La gestion des mises à jour constitue un processus continu visant à maintenir un niveau de sécurité adapté tout en préservant la stabilité de l'infrastructure.

Elle ne consiste pas à installer systématiquement les dernières versions, mais à prendre des décisions éclairées fondées sur les risques, les impacts et les besoins opérationnels.

---

# Références

## Référentiels

- ANSSI – Recommandations de maintien en condition de sécurité.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.

## Guides techniques

- SOCLE – Stéphane Robert (gestion des mises à jour et maintien en condition de sécurité des systèmes Linux).
