# 09 - Sauvegardes


| Élément | Valeur |
| **Nom du document** | `09-Sauvegardes.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les sauvegardes constituent l'une des dernières lignes de défense d'une infrastructure.

Leur objectif est de permettre la restauration des services après une défaillance matérielle, une erreur humaine, une corruption de données ou une compromission.

Une sauvegarde non restaurable ne répond pas à cet objectif.

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- les machines virtuelles ;
- les fichiers de configuration de Proxmox VE ;
- les sauvegardes locales ;
- les sauvegardes distantes ;
- les supports de stockage utilisés pour les sauvegardes.

---

# 3. Risques identifiés

Une stratégie de sauvegarde inadaptée peut entraîner :

- une perte définitive de données ;
- une indisponibilité prolongée des services ;
- l'impossibilité de restaurer une machine virtuelle ;
- la compromission simultanée des données de production et des sauvegardes ;
- un allongement significatif du délai de reprise.

---

# 4. Principes de conception

## Les sauvegardes protègent les actifs critiques

Chaque actif identifié lors de l'analyse des risques doit faire l'objet d'une réflexion sur sa sauvegarde.

La fréquence des sauvegardes dépend de la criticité de l'actif et des besoins opérationnels.

---

## Une sauvegarde n'a de valeur que si elle peut être restaurée

La réussite d'une tâche de sauvegarde ne garantit pas que les données pourront être restaurées.

Des tests de restauration doivent être réalisés régulièrement afin de valider l'intégrité des sauvegardes et la procédure de reprise.

---

## Les sauvegardes doivent être protégées

Les sauvegardes constituent elles-mêmes des actifs critiques.

Elles doivent être protégées contre :

- les suppressions accidentelles ;
- les erreurs de manipulation ;
- les défaillances matérielles ;
- les compromissions.

---

## Les sauvegardes doivent être documentées

La stratégie de sauvegarde doit préciser :

- les actifs sauvegardés ;
- la fréquence des sauvegardes ;
- les supports utilisés ;
- la politique de rétention ;
- les responsabilités ;
- la procédure de restauration.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- identifier les actifs devant être sauvegardés ;
- définir une fréquence adaptée à leur criticité ;
- conserver plusieurs points de restauration ;
- documenter la stratégie de rétention ;
- tester régulièrement les restaurations ;
- superviser les opérations de sauvegarde.

---

# 6. Vérification

Les contrôles doivent notamment permettre de vérifier :

- la réussite des sauvegardes ;
- la disponibilité des supports ;
- la cohérence de la politique de rétention ;
- la possibilité de restaurer les sauvegardes ;
- la documentation des procédures de reprise.

Une stratégie de sauvegarde n'est considérée comme maîtrisée que si des restaurations ont été réalisées avec succès.

---

# 7. Supervision

La supervision peut permettre de détecter :

- un échec de sauvegarde ;
- une sauvegarde incomplète ;
- une indisponibilité du stockage de sauvegarde ;
- un dépassement de la durée habituelle d'une sauvegarde ;
- une absence de sauvegarde récente.

Les alertes doivent permettre une intervention avant qu'un incident ne compromette la capacité de restauration.

---

# 8. Bonnes pratiques de conception

Avant de définir une stratégie de sauvegarde, il convient de répondre aux questions suivantes :

- Quels actifs doivent être sauvegardés ?
- Quelle est leur criticité ?
- Quelle perte de données est acceptable ?
- Quel délai de restauration est acceptable ?
- Les sauvegardes sont-elles stockées sur un support distinct ?
- La politique de rétention est-elle adaptée ?
- Des restaurations ont-elles déjà été testées ?
- Comment la réussite des sauvegardes sera-t-elle supervisée ?

Ces questions permettent de concevoir une stratégie de sauvegarde répondant aux besoins réels de l'infrastructure.

---

# 9. Conclusion

Les sauvegardes constituent une mesure essentielle de résilience.

Leur efficacité ne dépend pas uniquement de leur exécution, mais également de leur protection, de leur supervision et de la capacité démontrée à restaurer les données lorsqu'un incident survient.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27001 (gestion de la continuité d'activité et protection des informations).

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Proxmox Backup Server (lorsqu'il est utilisé).

## Guides techniques

- SOCLE – Stéphane Robert (sauvegarde, maintien en condition de sécurité et reprise).

## Veille

Toute évolution des mécanismes de sauvegarde de Proxmox VE ou des recommandations officielles devra être analysée avant son intégration au référentiel.
