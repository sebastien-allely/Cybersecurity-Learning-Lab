# 08 - Supervision


| Élément | Valeur |
| **Nom du document** | `08-Supervision.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La supervision permet de détecter rapidement une défaillance, une dérive de configuration ou un événement de sécurité affectant Apache HTTP Server.

Le référentiel privilégie une supervision orientée risque.

Chaque indicateur supervisé doit permettre une prise de décision opérationnelle.

---

# 2. Actifs concernés

La supervision concerne notamment :

- le service Apache ;
- les applications publiées ;
- les certificats TLS ;
- les journaux ;
- les fichiers de configuration ;
- les ressources système nécessaires au fonctionnement d'Apache.

---

# 3. Risques identifiés

Une supervision inadaptée peut entraîner :

- une détection tardive d'une indisponibilité ;
- une perte de visibilité sur les événements de sécurité ;
- une augmentation des faux positifs ;
- une fatigue des administrateurs liée à un excès d'alertes ;
- une incapacité à réagir rapidement.

---

# 4. Principes de conception

## Superviser uniquement les éléments critiques

Un indicateur doit répondre à une question opérationnelle.

L'accumulation de métriques sans objectif augmente le bruit et réduit l'efficacité de la supervision.

---

## Détecter les défaillances avant leurs conséquences

Les alertes doivent permettre une intervention avant que les utilisateurs ne soient impactés.

La supervision doit être proactive autant que possible.

---

## Limiter les faux positifs

Une alerte injustifiée réduit progressivement la confiance accordée à la supervision.

Les seuils retenus doivent être adaptés au contexte réel de l'infrastructure.

---

## Corréler les événements

Un événement isolé possède rarement une valeur suffisante.

La corrélation entre plusieurs événements permet une meilleure qualification des incidents.

---

# 5. Décisions retenues

Le référentiel retient les décisions suivantes :

- superviser la disponibilité du service Apache ;
- superviser la disponibilité des applications publiées ;
- superviser l'expiration des certificats TLS ;
- superviser les erreurs critiques du service ;
- superviser les modifications des fichiers de configuration (AIDE ou équivalent) ;
- superviser l'espace disque utilisé par les journaux ;
- superviser les ressources système nécessaires au fonctionnement du serveur Web.

Les indicateurs retenus doivent toujours pouvoir être associés à un risque identifié.

---

# 6. Vérification

Une revue régulière doit permettre de vérifier :

- que les éléments supervisés restent pertinents ;
- que les seuils d'alerte sont adaptés ;
- que les alertes permettent une action concrète ;
- que les faux positifs restent limités ;
- que les dépendances entre alertes sont correctement définies.

---

# 7. Supervision des mécanismes de supervision

Le référentiel retient également la supervision des mécanismes eux-mêmes.

Cela comprend notamment :

- la disponibilité de l'agent de supervision ;
- la remontée correcte des données ;
- l'exécution des contrôles planifiés ;
- la disponibilité du serveur de supervision.

Une supervision indisponible ne permet plus de garantir la détection des incidents.

---

# 8. Bonnes pratiques de conception

Avant d'ajouter un nouvel indicateur, il convient de répondre aux questions suivantes :

- Quel risque permet-il de détecter ?
- Quelle décision permettra-t-il de prendre ?
- Génère-t-il des faux positifs ?
- Existe-t-il déjà un indicateur équivalent ?
- Peut-il être corrélé avec d'autres événements ?
- Quel sera son coût d'exploitation ?

Si aucune réponse opérationnelle n'est apportée, l'indicateur ne doit pas être intégré au référentiel.

---

# 9. Conclusion

La supervision constitue un moyen de confirmer que les décisions de sécurité restent efficaces dans le temps.

Le référentiel privilégie une supervision ciblée, justifiée et exploitable plutôt qu'une collecte exhaustive de métriques.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27002.

## Documentation officielle

- Apache HTTP Server Documentation.
- Documentation ZABBIX01.

## Guides techniques

- SOCLE – Stéphane Robert (supervision et maintien en condition de sécurité).

## Veille

Les indicateurs de supervision devront être réévalués lors de toute évolution de l'architecture, des applications publiées ou des outils de supervision.
