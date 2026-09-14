# 03 - TLS / HTTPS


| Élément | Valeur |
| **Nom du document** | `03-TLS-HTTPS.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Définir les principes de sécurisation des communications HTTP et HTTPS publiées par Apache HTTP Server. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les communications entre un client et un serveur Web peuvent transporter des informations sensibles.

L'objectif du protocole TLS est d'assurer :

- la confidentialité ;
- l'intégrité ;
- l'authenticité des échanges.

Le présent document définit les principes guidant la sécurisation des communications publiées par Apache.

---

# 2. Actifs concernés

Les décisions concernent notamment :

- les certificats TLS ;
- les clés privées ;
- les Virtual Hosts HTTPS ;
- les clients accédant aux applications ;
- les applications publiées.

---

# 3. Risques identifiés

Une mauvaise configuration TLS peut entraîner :

- l'interception des communications ;
- l'altération des données échangées ;
- l'usurpation du serveur ;
- l'utilisation de mécanismes cryptographiques obsolètes ;
- une perte de confiance des utilisateurs.

---

# 4. Principes de conception

## Chiffrer les communications

Les applications publiées doivent utiliser HTTPS lorsqu'elles transportent des informations nécessitant confidentialité ou intégrité.

Le chiffrement réduit les risques d'interception et de modification des données.

---

## Protéger les clés privées

Les clés privées constituent des actifs critiques.

Leur accès doit être limité aux seuls composants autorisés.

Une compromission d'une clé privée compromet la confiance accordée au certificat.

---

## Utiliser des mécanismes cryptographiques maintenus

Les protocoles, suites cryptographiques et mécanismes de chiffrement doivent rester compatibles avec les recommandations actuelles des éditeurs et des référentiels de sécurité.

Les mécanismes obsolètes doivent être retirés lorsqu'ils ne sont plus nécessaires.

---

## Gérer le cycle de vie des certificats

Les certificats doivent être :

- suivis ;
- renouvelés avant expiration ;
- remplacés lorsqu'ils deviennent obsolètes ou compromis.

---

# 5. Décisions retenues

Le référentiel recommande notamment :

- privilégier HTTPS pour les applications publiées ;
- protéger les certificats et les clés privées ;
- maintenir les paramètres TLS conformes aux recommandations officielles ;
- documenter les certificats utilisés ;
- superviser leur date d'expiration.

Les paramètres cryptographiques précis relèvent de l'implémentation et devront être adaptés aux recommandations en vigueur.

---

# 6. Vérification

Une revue périodique doit permettre de vérifier :

- la validité des certificats ;
- la protection des clés privées ;
- la conformité de la configuration TLS ;
- la cohérence des Virtual Hosts HTTPS ;
- l'absence de mécanismes cryptographiques obsolètes.

---

# 7. Supervision

Les événements suivants présentent une valeur opérationnelle :

- expiration prochaine d'un certificat ;
- certificat expiré ;
- échec du chargement d'un certificat ;
- indisponibilité du service HTTPS ;
- erreur TLS répétée.

Les alertes doivent permettre une intervention avant que le service ne soit impacté.

---

# 8. Bonnes pratiques de conception

Avant de publier un nouveau service HTTPS, il convient de répondre aux questions suivantes :

- Les échanges nécessitent-ils une protection ?
- Le certificat est-il valide ?
- Les clés privées sont-elles protégées ?
- La configuration suit-elle les recommandations officielles ?
- Le renouvellement du certificat est-il documenté ?
- Son expiration est-elle supervisée ?

---

# 9. Conclusion

La sécurisation des communications ne repose pas uniquement sur l'activation de HTTPS.

Elle implique une gestion rigoureuse des certificats, des clés privées et des paramètres cryptographiques afin de garantir la confidentialité, l'intégrité et l'authenticité des échanges.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- ANSSI – Recommandations cryptographiques.
- NIST Cybersecurity Framework.

## Documentation officielle

- Apache HTTP Server Documentation.
- OpenSSL Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (configuration TLS des services Linux).

## Veille

Les paramètres TLS devront être réévalués régulièrement afin de rester conformes aux recommandations des éditeurs et des autorités de sécurité.
