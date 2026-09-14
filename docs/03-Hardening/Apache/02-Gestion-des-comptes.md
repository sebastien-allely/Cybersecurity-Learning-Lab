# 02 - Gestion des comptes


| Élément | Valeur |
| **Nom du document** | `02-Gestion-des-comptes.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La gestion des comptes constitue un élément fondamental de la sécurité d'un serveur Web.

L'objectif est de limiter les privilèges accordés au serveur Apache et aux administrateurs afin de réduire l'impact potentiel d'une compromission.

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- le compte système exécutant Apache ;
- les comptes administrateurs du serveur ;
- les mécanismes d'authentification ;
- les fichiers contenant des informations d'authentification.

---

# 3. Risques identifiés

Une gestion inadaptée des comptes peut entraîner :

- une élévation de privilèges ;
- une compromission du serveur Web ;
- un accès non autorisé aux applications publiées ;
- une modification non maîtrisée de la configuration ;
- une perte de traçabilité des actions d'administration.

---

# 4. Principes de conception

## Appliquer le principe du moindre privilège

Apache doit fonctionner avec les droits strictement nécessaires.

Le compte de service ne doit jamais disposer de privilèges administrateur.

---

## Séparer les comptes

Les comptes de service doivent être distincts des comptes d'administration.

Chaque compte doit avoir un usage clairement défini.

---

## Limiter les privilèges administratifs

Les privilèges élevés doivent être réservés aux opérations d'administration.

Les tâches courantes doivent être réalisées avec des comptes ne disposant pas de privilèges excessifs.

---

## Garantir la traçabilité

Les actions d'administration doivent pouvoir être attribuées à un utilisateur identifié.

L'utilisation de comptes partagés doit être évitée.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- utiliser le compte de service prévu par la distribution ;
- ne jamais exécuter Apache avec le compte `root` ;
- limiter les droits sur les fichiers de configuration ;
- protéger les fichiers contenant des secrets ;
- documenter les comptes disposant de privilèges élevés ;
- supprimer les comptes devenus inutiles.

---

# 6. Vérification

Une revue périodique doit permettre de vérifier :

- le compte utilisé par Apache ;
- les droits associés à ce compte ;
- les comptes administrateurs actifs ;
- les permissions des fichiers sensibles ;
- la cohérence des mécanismes d'authentification.

Toute anomalie doit être analysée avant mise en production.

---

# 7. Supervision

Les événements suivants présentent une valeur opérationnelle :

- modification des droits sur les fichiers sensibles (si un contrôle d'intégrité est déployé) ;
- changement du compte exécutant Apache ;
- échec répété d'authentification sur une interface protégée ;
- création ou suppression d'un compte d'administration.

Ces événements doivent être corrélés avec les journaux système afin de distinguer une opération légitime d'une activité malveillante.

---

# 8. Bonnes pratiques de conception

Avant de créer ou de modifier un compte, il convient de répondre aux questions suivantes :

- Quel est son rôle ?
- Quels privilèges sont réellement nécessaires ?
- Qui est responsable de ce compte ?
- Comment son utilisation sera-t-elle auditée ?
- Comment sera-t-il supprimé lorsqu'il ne sera plus nécessaire ?

Une réponse incomplète à ces questions doit conduire à réévaluer la création ou la modification du compte.

---

# 9. Conclusion

Une gestion rigoureuse des comptes réduit les conséquences d'une compromission et améliore la traçabilité des actions d'administration.

Le respect du principe du moindre privilège constitue l'un des fondements du durcissement d'Apache HTTP Server.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ANSSI – Recommandations relatives aux comptes à privilèges.
- NIST Cybersecurity Framework.
- ISO/IEC 27001.

## Documentation officielle

- Documentation officielle Apache HTTP Server.
- Documentation Debian.

## Guides techniques

- SOCLE – Stéphane Robert (gestion des comptes, des privilèges et durcissement Linux).

## Veille

Toute évolution des mécanismes d'authentification ou de gestion des privilèges devra être évaluée avant son intégration au référentiel.
