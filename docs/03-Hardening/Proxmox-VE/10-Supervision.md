# 10 - Supervision


| Élément | Valeur |
| **Nom du document** | `10-Supervision.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La supervision permet de vérifier que les mesures de sécurité retenues restent efficaces dans le temps.

Elle ne consiste pas à collecter le plus grand nombre de métriques possible, mais à surveiller les événements apportant une réelle valeur opérationnelle.

Une supervision efficace doit permettre de détecter rapidement une défaillance, une dérive ou un comportement anormal.

---

# 2. Actifs concernés

La supervision concerne notamment :

- l'hyperviseur Proxmox VE ;
- les services critiques ;
- les machines virtuelles ;
- le stockage ;
- les interfaces réseau ;
- les sauvegardes ;
- le cluster (le cas échéant).

---

# 3. Risques identifiés

Une supervision inadaptée peut entraîner :

- une détection tardive d'un incident ;
- une perte de disponibilité ;
- une multiplication des faux positifs ;
- une fatigue d'alerte ;
- une perte de confiance dans le système de supervision.

Une alerte inutile possède un coût opérationnel.

---

# 4. Principes de conception

## Superviser uniquement ce qui possède une valeur opérationnelle

Chaque élément supervisé doit répondre à une question simple :

> **Quelle décision pourra être prise si cette alerte apparaît ?**

Si aucune action n'est possible, la supervision doit être remise en question.

---

## Privilégier les événements plutôt que les métriques

Une métrique n'a d'intérêt que si elle permet :

- de détecter une dérive ;
- d'anticiper une panne ;
- de confirmer une compromission.

Collecter une information uniquement parce qu'elle est disponible augmente inutilement la charge de supervision.

---

## Réduire les faux positifs

Une alerte doit être crédible.

Les seuils doivent être définis de manière à limiter les alertes sans valeur opérationnelle.

Une supervision ignorée devient inefficace.

---

## Superviser les actifs critiques en priorité

La supervision doit refléter la criticité de l'infrastructure.

Les actifs les plus critiques doivent être supervisés avant les éléments secondaires.

---

# 5. Décisions retenues

Les éléments suivants sont considérés comme prioritaires :

## Niveau 1 — Disponibilité de l'hyperviseur

- disponibilité de l'agent de supervision ;
- disponibilité de l'API Proxmox ;
- disponibilité des services critiques.

---

## Niveau 2 — Disponibilité des machines virtuelles

- état des machines virtuelles critiques ;
- disponibilité des services hébergés.

---

## Niveau 3 — Santé du stockage

- état SMART/NVMe ;
- température des supports ;
- erreurs matérielles ;
- espace disponible.

---

## Niveau 4 — Ressources système

- charge CPU ;
- mémoire disponible ;
- occupation des systèmes de fichiers.

---

## Niveau 5 — Cluster

Lorsque l'infrastructure utilise un cluster :

- quorum ;
- nombre de nœuds ;
- état de synchronisation.

---

## Niveau 6 — Sauvegardes

- réussite des sauvegardes ;
- ancienneté de la dernière sauvegarde valide ;
- disponibilité du stockage de sauvegarde.

---

# 6. Vérification

Une revue périodique doit permettre de vérifier :

- que les éléments supervisés correspondent toujours aux actifs critiques ;
- que les seuils restent adaptés ;
- que les alertes produites sont pertinentes ;
- que les événements importants sont effectivement détectés.

---

# 7. Critères de qualité

Une supervision est considérée comme efficace lorsqu'elle :

- détecte les incidents importants ;
- limite les faux positifs ;
- reste compréhensible ;
- peut être maintenue facilement ;
- accompagne les décisions d'exploitation.

---

# 8. Bonnes pratiques de conception

Avant d'ajouter une nouvelle métrique, il convient de répondre aux questions suivantes :

- Quel actif est concerné ?
- Quel risque cherche-t-on à détecter ?
- Cet événement est-il réellement observable ?
- Une alerte permettra-t-elle une action ?
- Existe-t-il déjà un indicateur équivalent ?
- Cette supervision risque-t-elle de générer des faux positifs ?
- La métrique restera-t-elle pertinente lors d'une montée de version ?

Une métrique sans objectif opérationnel ne doit pas être intégrée.

---

# 9. Conclusion

La supervision ne mesure pas la quantité d'informations collectées.

Elle mesure la capacité à détecter rapidement les événements ayant un impact sur la disponibilité, la sécurité ou l'exploitation de l'infrastructure.

Une supervision pertinente est sélective, justifiée et directement exploitable par l'équipe d'administration.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27001 (surveillance, amélioration continue et maîtrise des risques).

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation officielle ZABBIX01.

## Guides techniques

- SOCLE – Stéphane Robert (supervision des systèmes Linux).

## Veille

Les indicateurs supervisés doivent être réévalués régulièrement afin de rester cohérents avec les évolutions de l'infrastructure et les nouveaux risques identifiés.
