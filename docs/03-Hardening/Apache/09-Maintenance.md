# 09 - Maintenance


| Élément | Valeur |
| **Nom du document** | `09-Maintenance.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le durcissement d'un serveur Apache ne constitue pas une action ponctuelle.

Les décisions de sécurité doivent être maintenues dans le temps afin de conserver leur efficacité malgré les évolutions du système, des applications et des menaces.

La maintenance contribue directement au maintien en condition opérationnelle (MCO) et au maintien en condition de sécurité (MCS).

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- Apache HTTP Server ;
- les modules installés ;
- les fichiers de configuration ;
- les certificats TLS ;
- les Virtual Hosts ;
- les journaux ;
- les mécanismes de supervision.

---

# 3. Risques identifiés

Une maintenance insuffisante peut entraîner :

- une dérive de configuration ;
- une augmentation de la dette technique ;
- une perte de conformité avec le référentiel ;
- une indisponibilité du service ;
- une augmentation de la surface d'attaque.

---

# 4. Principes de conception

## Maintenir une configuration documentée

Toute modification doit être documentée.

Une configuration non documentée devient rapidement difficile à maintenir.

---

## Contrôler les modifications

Les évolutions doivent être planifiées et validées.

Chaque modification doit pouvoir être justifiée.

---

## Vérifier régulièrement la conformité

La configuration réelle doit rester conforme aux décisions retenues par le référentiel.

Toute dérive doit être analysée.

---

## Réduire la dette technique

Les composants devenus inutiles doivent être supprimés.

Les configurations obsolètes doivent être révisées.

Les exceptions doivent être limitées et documentées.

---

## Préparer les évolutions

Les évolutions d'Apache, du système d'exploitation ou des applications publiées doivent être anticipées afin de limiter leur impact sur la sécurité.

---

# 5. Décisions retenues

Le référentiel retient les décisions suivantes :

- documenter toute modification de configuration ;
- réviser régulièrement les Virtual Hosts ;
- supprimer les modules devenus inutiles ;
- contrôler périodiquement les certificats TLS ;
- vérifier la cohérence des règles de sécurité ;
- réaliser une revue régulière des journaux et des indicateurs de supervision ;
- maintenir une documentation technique à jour.

---

# 6. Vérification

Une revue périodique doit permettre de vérifier :

- la conformité de la configuration Apache ;
- les modules activés ;
- les certificats utilisés ;
- les Virtual Hosts publiés ;
- les mécanismes d'authentification ;
- les décisions de sécurité documentées.

---

# 7. Supervision

Les éléments suivants présentent une valeur opérationnelle :

- modification inattendue des fichiers de configuration ;
- ajout d'un nouveau Virtual Host ;
- chargement d'un nouveau module ;
- échec d'un redémarrage d'Apache après modification ;
- dérive détectée par un contrôle d'intégrité.

Ces événements doivent permettre de détecter rapidement toute évolution non maîtrisée.

---

# 8. Bonnes pratiques de conception

Avant d'effectuer une modification, il convient de répondre aux questions suivantes :

- Pourquoi cette modification est-elle nécessaire ?
- Quel risque réduit-elle ou introduit-elle ?
- Est-elle documentée ?
- Est-elle compatible avec le référentiel ?
- Peut-elle être supervisée ?
- Existe-t-il une procédure de retour arrière ?

---

# 9. Conclusion

La maintenance garantit la pérennité des décisions de sécurité.

Le référentiel considère qu'une mesure de sécurité n'est efficace que si elle reste comprise, documentée, vérifiée et maintenue tout au long du cycle de vie du serveur.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27002.

## Documentation officielle

- Documentation officielle Apache HTTP Server.

## Guides techniques

- SOCLE – Stéphane Robert (maintien en condition de sécurité et durcissement des services Linux).

## Veille

Les procédures de maintenance devront être réévaluées lors de chaque évolution majeure d'Apache, du système d'exploitation ou de l'architecture de supervision.
