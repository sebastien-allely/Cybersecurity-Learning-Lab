# 06 - Journalisation


| Élément | Valeur |
| **Nom du document** | `06-Journalisation.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La journalisation permet de conserver une trace des événements significatifs affectant MariaDB.

Elle facilite la détection d'incidents, les investigations et les audits.

---

# 2. Risques identifiés

Une journalisation insuffisante peut entraîner :

- une absence de traçabilité ;
- une détection tardive d'un incident ;
- des difficultés d'investigation ;
- une perte d'informations utiles à l'analyse.

---

# 3. Principes de conception

Le référentiel retient les principes suivants :

- journaliser uniquement les événements utiles ;
- limiter les journaux inutiles afin de réduire le bruit ;
- protéger les journaux contre toute modification non autorisée ;
- conserver une durée de rétention adaptée aux besoins du laboratoire.

---

# 4. Décisions retenues

Le référentiel recommande :

- journaliser les démarrages et arrêts du service ;
- journaliser les erreurs critiques ;
- journaliser les connexions administratives ;
- journaliser les modifications de privilèges ;
- protéger les journaux contre la suppression ou l'altération.

---

# 5. Vérification

Une revue régulière doit permettre de vérifier :

- la génération correcte des journaux ;
- leur intégrité ;
- leur rotation ;
- leur disponibilité.

---

# 6. Supervision

Les événements suivants doivent être détectés :

- arrêt de la journalisation ;
- saturation de l'espace disque ;
- disparition d'un journal ;
- erreurs critiques répétées.

---

# 7. Conclusion

Une journalisation pertinente améliore la capacité à détecter, comprendre et traiter les incidents de sécurité.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ISO/IEC 27002.

## Documentation officielle

- MariaDB Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (journalisation et supervision des systèmes Linux).
