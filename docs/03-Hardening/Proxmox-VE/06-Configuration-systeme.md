# 06 - Configuration système


| Élément | Valeur |
| **Nom du document** | `06-Configuration-systeme.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La configuration système constitue le socle de fonctionnement de Proxmox VE.

Son durcissement vise à réduire les risques de compromission tout en garantissant la stabilité, la maintenabilité et la compatibilité avec les composants de l'infrastructure.

L'objectif n'est pas de modifier un maximum de paramètres, mais de conserver une configuration simple, documentée et justifiée.

---

# 2. Actifs concernés

Les décisions présentées dans ce document concernent principalement :

- le système Debian ;
- le noyau Linux ;
- les services Proxmox VE ;
- les services système ;
- les fichiers de configuration ;
- les journaux système.

---

# 3. Risques identifiés

Une configuration inadaptée peut entraîner :

- l'exploitation d'une fonctionnalité inutile ;
- une augmentation de la surface d'attaque ;
- une perte de stabilité ;
- une mauvaise traçabilité des événements ;
- une augmentation de la dette technique.

---

# 4. Principes de conception

## Conserver une configuration proche de l'éditeur

Les paramètres fournis par défaut constituent la base de référence.

Une modification ne doit être réalisée que si elle répond à un besoin clairement identifié.

L'objectif est de limiter les écarts avec la configuration officiellement supportée par Proxmox VE.

---

## Chaque modification doit être justifiée

Avant toute modification, il convient de répondre aux questions suivantes :

- Quel actif est concerné ?
- Quel risque est réduit ?
- Quel impact est attendu ?
- Comment vérifier que la modification est toujours valide après une mise à jour ?

Une modification non justifiée augmente le risque de dette technique.

---

## Favoriser les mécanismes natifs

Lorsqu'une fonctionnalité native répond au besoin, elle est privilégiée.

Cette approche permet :

- de limiter les dépendances ;
- de simplifier les mises à jour ;
- de réduire les risques d'incompatibilité.

---

## Documenter les écarts

Toute configuration différente de celle proposée par défaut doit être documentée.

Cette documentation doit permettre de comprendre :

- pourquoi la modification a été réalisée ;
- quel risque elle réduit ;
- comment revenir à la configuration d'origine si nécessaire.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- de supprimer les services inutiles après analyse ;
- de limiter les logiciels installés aux composants nécessaires ;
- de conserver une configuration compatible avec les recommandations officielles ;
- de documenter toute personnalisation du système ;
- de vérifier régulièrement la cohérence de la configuration.

---

# 6. Vérification

Une revue périodique doit permettre de contrôler :

- les services actifs ;
- les paquets installés ;
- les fichiers de configuration modifiés ;
- les comptes système ;
- les tâches planifiées ;
- les journaux système.

Toute différence par rapport à la configuration attendue doit être analysée.

---

# 7. Supervision

Les éléments suivants présentent un intérêt pour la supervision :

- arrêt d'un service critique ;
- modification d'un fichier de configuration sensible (si un mécanisme de contrôle d'intégrité est déployé, par exemple AIDE) ;
- erreurs répétées dans les journaux système ;
- saturation des ressources système pouvant révéler un dysfonctionnement.

Toutes les modifications de configuration n'ont pas vocation à générer une alerte. La supervision doit se concentrer sur les événements ayant une valeur opérationnelle.

---

# 8. Bonnes pratiques de conception

Avant de modifier un paramètre système, il convient de répondre aux questions suivantes :

- La modification est-elle recommandée par la documentation officielle ?
- Réduit-elle un risque identifié ?
- Introduit-elle une dépendance supplémentaire ?
- Peut-elle compliquer une future mise à jour ?
- Est-elle facilement compréhensible par un autre administrateur ?
- Comment sera-t-elle vérifiée après une mise à jour ?

Si ces questions ne trouvent pas de réponse satisfaisante, la modification doit être réévaluée.

---

# 9. Conclusion

Le durcissement de la configuration système ne consiste pas à multiplier les personnalisations.

Il consiste à maintenir une configuration simple, maîtrisée et documentée, répondant aux besoins de sécurité sans compromettre la stabilité ni la maintenabilité de l'hyperviseur.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ANSSI – Recommandations d'administration sécurisée.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.

## Guides techniques

- SOCLE – Stéphane Robert (durcissement des systèmes Linux).

## Veille

Toute nouvelle recommandation publiée par Proxmox VE ou Debian devra être analysée avant d'être intégrée au référentiel.
