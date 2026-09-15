# 11 - Maintenance


| Élément | Valeur |
| **Nom du document** | `11-Maintenance.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le durcissement d'un hyperviseur n'est pas une action ponctuelle réalisée lors de son installation.

La sécurité doit être maintenue tout au long du cycle de vie de l'infrastructure afin de garantir que les mesures retenues restent adaptées aux risques identifiés.

La maintenance participe au maintien en condition de sécurité (MCS) et au maintien en condition opérationnelle (MCO).

---

# 2. Actifs concernés

La maintenance concerne notamment :

- l'hyperviseur Proxmox VE ;
- les services système ;
- les services Proxmox ;
- les machines virtuelles ;
- le stockage ;
- les sauvegardes ;
- la supervision ;
- la documentation.

---

# 3. Risques identifiés

Une absence de maintenance peut entraîner :

- une augmentation de la surface d'attaque ;
- une accumulation de vulnérabilités ;
- une dégradation des performances ;
- une dérive de configuration ;
- une perte de disponibilité ;
- une augmentation de la dette technique.

---

# 4. Principes de conception

## La maintenance est un processus continu

La sécurité ne doit jamais être considérée comme acquise.

Chaque évolution de l'infrastructure peut modifier les risques précédemment identifiés.

---

## Les vérifications doivent être planifiées

Les opérations de maintenance doivent être réalisées selon une fréquence définie.

L'objectif est d'éviter que les contrôles ne dépendent uniquement de la disponibilité de l'administrateur.

---

## La documentation doit évoluer avec l'infrastructure

Toute modification importante doit être répercutée dans la documentation.

Une documentation obsolète augmente le risque d'erreur lors des opérations d'exploitation ou de reprise.

---

## Les décisions doivent être réévaluées

Les choix réalisés lors du déploiement doivent être réexaminés régulièrement afin de vérifier qu'ils répondent toujours aux besoins de l'infrastructure.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- maintenir le système à jour ;
- vérifier régulièrement les journaux système ;
- contrôler l'état du stockage ;
- vérifier les sauvegardes ;
- tester périodiquement les restaurations ;
- réviser les comptes disposant de privilèges ;
- contrôler les règles de supervision ;
- maintenir la documentation à jour.

---

# 6. Vérification

La maintenance doit notamment permettre de vérifier :

- le bon fonctionnement des services ;
- la cohérence des configurations ;
- la disponibilité des sauvegardes ;
- la validité des procédures documentées ;
- la pertinence des alertes de supervision ;
- l'absence de dérive de configuration.

---

# 7. Supervision

La supervision contribue à la maintenance en détectant notamment :

- l'arrêt d'un service critique ;
- une dégradation matérielle ;
- une saturation des ressources ;
- un échec de sauvegarde ;
- une indisponibilité d'un composant essentiel.

Les événements observés doivent être analysés afin d'adapter, si nécessaire, les décisions de sécurité.

---

# 8. Bonnes pratiques de conception

Avant de considérer une infrastructure comme maintenue, il convient de répondre aux questions suivantes :

- Les mises à jour sont-elles maîtrisées ?
- Les sauvegardes sont-elles toujours restaurables ?
- Les journaux sont-ils régulièrement analysés ?
- Les alertes restent-elles pertinentes ?
- Les comptes à privilèges sont-ils toujours justifiés ?
- La documentation reflète-t-elle l'état réel de l'infrastructure ?
- Les risques identifiés lors de la conception sont-ils toujours d'actualité ?

Ces questions permettent de maintenir une infrastructure cohérente avec les objectifs de sécurité définis lors de sa conception.

---

# 9. Conclusion

La maintenance constitue la continuité logique du durcissement.

Elle garantit que les décisions prises lors de la conception restent pertinentes malgré les évolutions techniques, les nouvelles vulnérabilités et les changements de contexte.

Une infrastructure sécurisée est avant tout une infrastructure régulièrement contrôlée, documentée et réévaluée.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ANSSI – Maintien en condition de sécurité (MCS).
- NIST Cybersecurity Framework.
- ISO/IEC 27001.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.

## Guides techniques

- SOCLE – Stéphane Robert (maintien en condition de sécurité des systèmes Linux).

## Veille

Les procédures de maintenance doivent être réévaluées régulièrement afin de tenir compte des évolutions de Proxmox VE, de Debian et des nouveaux risques identifiés.
