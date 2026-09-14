# 05 - Authentification et contrôle d'accès


| Élément | Valeur |
| **Nom du document** | `05-Authentification-et-controle-d-acces.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Apache constitue le point d'entrée des applications Web qu'il publie.

Le contrôle d'accès vise à garantir que seules les entités autorisées puissent accéder aux ressources exposées.

Les mécanismes retenus doivent protéger les actifs identifiés sans complexifier inutilement l'exploitation du serveur.

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- les interfaces d'administration ;
- les applications publiées ;
- les ressources protégées ;
- les mécanismes d'authentification ;
- les annuaires d'authentification (LDAP, Active Directory) lorsqu'ils sont utilisés.

---

# 3. Risques identifiés

Une gestion insuffisante des accès peut entraîner :

- un accès non autorisé aux applications ;
- une élévation de privilèges ;
- une compromission des données publiées ;
- une modification non autorisée de la configuration ;
- une perte de confidentialité.

---

# 4. Principes de conception

## Authentifier uniquement lorsque cela est nécessaire

L'authentification doit protéger les ressources sensibles.

Les contenus publics ne doivent pas être protégés inutilement.

---

## Appliquer le principe du moindre privilège

Les utilisateurs ne disposent que des autorisations nécessaires à leurs missions.

Les privilèges excessifs augmentent les conséquences d'une compromission.

---

## Centraliser l'authentification

Lorsque l'infrastructure dispose déjà d'un annuaire (LDAP ou Active Directory), celui-ci doit être privilégié afin de limiter la multiplication des bases d'identités.

---

## Limiter l'exposition des interfaces d'administration

Les interfaces d'administration doivent être accessibles uniquement aux personnes autorisées.

Lorsque cela est possible, leur accès doit être restreint au réseau d'administration.

---

## Journaliser les opérations sensibles

Les authentifications, refus d'accès et opérations d'administration doivent être journalisés afin de faciliter les investigations.

---

# 5. Décisions retenues

Le référentiel retient les décisions suivantes :

- protéger les interfaces d'administration ;
- privilégier une authentification centralisée lorsque cela est possible ;
- limiter les privilèges des utilisateurs ;
- restreindre les accès administratifs aux réseaux autorisés ;
- supprimer les mécanismes d'authentification devenus inutiles ;
- documenter toute exception.

---

# 6. Vérification

Une revue périodique doit permettre de vérifier :

- les ressources protégées ;
- les mécanismes d'authentification utilisés ;
- les privilèges accordés ;
- les comptes disposant d'un accès administratif ;
- les restrictions d'accès réseau.

Toute dérive doit être analysée avant sa mise en production.

---

# 7. Supervision

Les événements suivants présentent une valeur opérationnelle :

- échecs répétés d'authentification ;
- succès d'authentification sur une interface d'administration ;
- modification des mécanismes d'authentification ;
- modification des règles de contrôle d'accès ;
- accès refusés sur des ressources protégées.

Les alertes doivent être corrélées avec les journaux système afin de distinguer une activité légitime d'une tentative de compromission.

---

# 8. Bonnes pratiques de conception

Avant d'introduire un nouveau mécanisme d'authentification, il convient de répondre aux questions suivantes :

- Quel risque est-il destiné à réduire ?
- Existe-t-il déjà un mécanisme équivalent ?
- Qui administrera cette solution ?
- Comment sera-t-elle supervisée ?
- Quelle sera sa procédure de maintenance ?
- Comment sera-t-elle retirée lorsqu'elle ne sera plus nécessaire ?

---

# 9. Conclusion

L'authentification et le contrôle d'accès constituent des mécanismes essentiels de protection des applications publiées.

Ils doivent être conçus de manière à protéger les actifs identifiés tout en restant simples à administrer, à superviser et à maintenir.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ANSSI – Recommandations relatives aux comptes à privilèges.
- NIST Cybersecurity Framework.
- ISO/IEC 27001.

## Documentation officielle

- Apache HTTP Server Documentation.
- Documentation LDAP.
- Documentation Microsoft Active Directory.

## Guides techniques

- SOCLE – Stéphane Robert (authentification, contrôle d'accès et durcissement des services Linux).

## Veille

Toute évolution des mécanismes d'authentification ou des contrôles d'accès devra faire l'objet d'une analyse avant son intégration au référentiel.
