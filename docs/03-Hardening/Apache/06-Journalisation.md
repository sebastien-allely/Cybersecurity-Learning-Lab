# 06 - Journalisation


| Élément | Valeur |
| **Nom du document** | `06-Journalisation.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La journalisation permet de détecter, comprendre et analyser les événements affectant Apache HTTP Server.

Les journaux constituent une source essentielle pour :

- la supervision ;
- la détection d'incidents ;
- les investigations ;
- les audits de sécurité.

Ils participent directement à la capacité de réaction de l'administrateur.

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- les journaux d'accès ;
- les journaux d'erreurs ;
- les journaux TLS ;
- les événements d'authentification ;
- les événements système liés au service Apache.

---

# 3. Risques identifiés

Une journalisation insuffisante peut entraîner :

- une impossibilité d'analyser un incident ;
- une détection tardive d'une compromission ;
- une perte de traçabilité ;
- une incapacité à produire des preuves techniques ;
- une difficulté à corréler plusieurs événements.

---

# 4. Principes de conception

## Journaliser les événements utiles

Tous les événements ne présentent pas un intérêt opérationnel.

La journalisation doit permettre d'obtenir une information exploitable tout en limitant le bruit.

---

## Garantir l'intégrité des journaux

Les journaux doivent être protégés contre les modifications non autorisées.

Ils constituent des éléments de preuve lors d'une investigation.

---

## Adapter le niveau de journalisation

Le niveau de journalisation doit être suffisant pour détecter les incidents sans générer un volume excessif de données.

---

## Centraliser les journaux lorsque cela est pertinent

Lorsque l'infrastructure le permet, les journaux peuvent être centralisés afin de faciliter leur exploitation et leur corrélation.

---

## Conserver les journaux

Les journaux doivent être conservés conformément aux besoins opérationnels et aux politiques de rétention définies pour l'infrastructure.

---

# 5. Décisions retenues

Le référentiel retient les décisions suivantes :

- activer les journaux d'accès et d'erreurs ;
- conserver un niveau de journalisation adapté aux besoins opérationnels ;
- protéger les fichiers de journaux contre toute modification non autorisée ;
- mettre en place une rotation des journaux ;
- centraliser les journaux lorsque cela présente un intérêt opérationnel ;
- superviser les anomalies de journalisation.

---

# 6. Vérification

Une revue périodique doit permettre de vérifier :

- que les journaux sont produits ;
- que leur contenu est exploitable ;
- que leur rotation fonctionne correctement ;
- que leur conservation respecte la politique définie ;
- qu'aucune interruption de journalisation n'est observée.

---

# 7. Supervision

Les événements suivants présentent une valeur opérationnelle :

- arrêt de la journalisation ;
- erreur d'écriture dans les journaux ;
- rotation en échec ;
- croissance anormale des journaux ;
- disparition d'un journal attendu.

Ces événements doivent être intégrés à la supervision afin de détecter rapidement toute perte de visibilité.

---

# 8. Bonnes pratiques de conception

Avant d'ajouter un nouveau journal, il convient de répondre aux questions suivantes :

- Quel risque permettra-t-il de détecter ?
- Sera-t-il effectivement consulté ?
- Peut-il être corrélé avec d'autres journaux ?
- Génère-t-il un volume acceptable ?
- Qui sera responsable de son exploitation ?

---

# 9. Conclusion

Une journalisation pertinente constitue un prérequis à toute stratégie de supervision et de réponse aux incidents.

Le référentiel privilégie une journalisation utile, exploitable et maintenable plutôt qu'une collecte exhaustive d'événements.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27002.

## Documentation officielle

- Apache HTTP Server Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (journalisation des services Linux et supervision).

## Veille

Les mécanismes de journalisation devront être réévalués lors de toute évolution d'Apache ou de l'architecture de supervision.
