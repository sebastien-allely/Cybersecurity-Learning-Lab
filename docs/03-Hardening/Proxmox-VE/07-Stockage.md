# 07 - Stockage


| Élément | Valeur |
| **Nom du document** | `07-Stockage.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le stockage constitue un actif critique de l'hyperviseur.

Il héberge notamment :

- les machines virtuelles ;
- les conteneurs (le cas échéant) ;
- les images ISO ;
- les sauvegardes locales ;
- les fichiers de configuration.

Une défaillance ou une compromission du stockage peut entraîner une perte totale ou partielle de l'infrastructure.

Le durcissement du stockage vise à limiter ces risques tout en garantissant la disponibilité des services.

---

# 2. Actifs concernés

Cette réflexion concerne notamment :

- les volumes de stockage Proxmox ;
- les disques NVMe, SSD ou HDD ;
- les systèmes de fichiers ;
- les stockages réseau (NFS, SMB/CIFS, iSCSI...) ;
- les sauvegardes locales.

---

# 3. Risques identifiés

Le stockage peut être affecté par :

- une défaillance matérielle ;
- une saturation de l'espace disque ;
- une corruption des données ;
- une suppression accidentelle ;
- une compromission de l'hyperviseur ;
- une erreur de configuration.

Les conséquences peuvent aller jusqu'à l'arrêt complet de l'infrastructure.

---

# 4. Principes de conception

## Le stockage est un actif critique

Le stockage ne doit jamais être considéré comme un simple support technique.

Il constitue l'un des actifs les plus sensibles de l'infrastructure.

---

## La disponibilité est prioritaire

Les décisions retenues doivent limiter les interruptions de service.

Avant toute modification importante, il convient de vérifier :

- la disponibilité d'une sauvegarde récente ;
- la procédure de restauration ;
- l'impact potentiel sur les machines virtuelles.

---

## Les performances ne doivent pas compromettre la sécurité

Une optimisation des performances ne doit pas réduire :

- la résilience ;
- la traçabilité ;
- la capacité de restauration.

---

## Les capacités doivent être supervisées

Une saturation du stockage représente un risque opérationnel.

Les capacités disponibles doivent donc être suivies régulièrement.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- séparer les différents usages du stockage lorsque cela est pertinent ;
- surveiller l'état de santé des supports physiques ;
- documenter chaque espace de stockage ;
- surveiller l'espace disponible ;
- tester régulièrement les restaurations ;
- protéger les sauvegardes contre une suppression accidentelle.

---

# 6. Vérification

Les contrôles portent notamment sur :

- l'état SMART/NVMe des supports ;
- la capacité disponible ;
- la cohérence des systèmes de fichiers ;
- l'accessibilité des stockages réseau ;
- la réussite des sauvegardes ;
- la capacité de restauration.

Une sauvegarde non restaurable ne doit pas être considérée comme valide.

---

# 7. Supervision

Les éléments suivants présentent une forte valeur opérationnelle :

- état de santé des SSD/NVMe ;
- température des supports ;
- erreurs matérielles ;
- espace disque disponible ;
- indisponibilité d'un datastore ;
- échec d'une sauvegarde ;
- temps anormalement élevé d'une opération de sauvegarde.

Les seuils doivent être définis en fonction du contexte de l'infrastructure.

---

# 8. Bonnes pratiques de conception

Avant d'ajouter ou de modifier un stockage, il convient de répondre aux questions suivantes :

- Quel actif ce stockage héberge-t-il ?
- Quelle serait la conséquence de sa perte ?
- Dispose-t-il d'une sauvegarde ?
- Une restauration a-t-elle déjà été testée ?
- Comment son état sera-t-il supervisé ?
- Les performances répondent-elles aux besoins ?
- Existe-t-il un risque de saturation à moyen terme ?

Ces questions permettent de concevoir un stockage adapté aux besoins réels plutôt qu'à une configuration par défaut.

---

# 9. Conclusion

Le stockage constitue un élément central de la sécurité de l'hyperviseur.

Sa conception ne doit pas uniquement répondre à des contraintes de capacité ou de performance, mais également garantir la disponibilité, l'intégrité et la possibilité de restaurer les données en cas d'incident.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.

## Guides techniques

- SOCLE – Stéphane Robert (gestion du stockage et supervision des systèmes Linux).

## Veille

Toute évolution concernant les systèmes de fichiers, les mécanismes de stockage ou les recommandations de Proxmox VE devra être analysée avant d'être intégrée au référentiel.
