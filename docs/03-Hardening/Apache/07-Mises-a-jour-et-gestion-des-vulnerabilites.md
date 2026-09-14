# 07 - Mises à jour et gestion des vulnérabilités


| Élément | Valeur |
| **Nom du document** | `07-Mises-a-jour-et-gestion-des-vulnerabilites.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Définir les mesures de gestion des mises à jour et des vulnérabilités d'Apache HTTP Server. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La sécurité d'un serveur Web ne repose pas uniquement sur sa configuration initiale.

L'apparition régulière de nouvelles vulnérabilités impose une veille continue, une politique de mise à jour maîtrisée et une évaluation permanente des risques.

L'objectif de ce document est de définir les principes permettant de maintenir Apache dans un état de sécurité satisfaisant tout au long de son cycle de vie.

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- Apache HTTP Server ;
- les modules Apache ;
- OpenSSL et les bibliothèques cryptographiques ;
- les dépendances logicielles ;
- le système d'exploitation ;
- les applications publiées.

---

# 3. Risques identifiés

Une politique de mise à jour insuffisante peut entraîner :

- l'exploitation de vulnérabilités connues ;
- une compromission du serveur ;
- une interruption de service ;
- une incompatibilité avec les recommandations de sécurité ;
- une augmentation de la dette technique.

---

# 4. Principes de conception

## Maintenir les composants supportés

Le référentiel retient exclusivement des versions bénéficiant d'un support de sécurité.

L'utilisation de composants en fin de vie (End of Life) augmente significativement le niveau de risque.

---

## Mettre à jour de manière maîtrisée

Une mise à jour constitue une modification du système.

Elle doit être :

- préparée ;
- testée lorsque cela est possible ;
- documentée ;
- vérifiée après son déploiement.

---

## Assurer une veille de sécurité

La surveillance des publications de sécurité permet d'anticiper les mesures correctives.

La veille doit couvrir :

- Apache HTTP Server ;
- les modules utilisés ;
- OpenSSL ;
- Debian ou Ubuntu selon la distribution retenue.

---

## Évaluer les vulnérabilités

Toutes les vulnérabilités n'ont pas le même impact.

Chaque publication doit être analysée au regard :

- de l'exposition réelle du serveur ;
- des modules utilisés ;
- des fonctionnalités concernées ;
- des actifs protégés.

---

# 5. Décisions retenues

Le référentiel retient les décisions suivantes :

- utiliser une version supportée d'Apache ;
- maintenir le système d'exploitation à jour ;
- suivre les bulletins de sécurité des éditeurs ;
- documenter les mises à jour réalisées ;
- vérifier le bon fonctionnement des applications après chaque mise à jour ;
- planifier les mises à jour dans le cadre du maintien en condition de sécurité.

---

# 6. Vérification

Une revue régulière doit permettre de vérifier :

- la version d'Apache ;
- la version des modules installés ;
- les mises à jour de sécurité appliquées ;
- les composants arrivant en fin de support ;
- la conformité avec la politique de maintenance.

---

# 7. Supervision

Les éléments suivants présentent une valeur opérationnelle :

- détection d'une version obsolète ;
- présence d'un composant en fin de support ;
- échec d'une mise à jour ;
- indisponibilité du service après une mise à jour ;
- vulnérabilité critique affectant un composant utilisé.

---

# 8. Bonnes pratiques de conception

Avant d'appliquer une mise à jour, il convient de répondre aux questions suivantes :

- Quel composant est concerné ?
- Quelle vulnérabilité est corrigée ?
- Le laboratoire est-il réellement exposé ?
- Existe-t-il un impact potentiel sur les applications publiées ?
- Un retour arrière est-il possible en cas d'échec ?

---

# 9. Conclusion

Le maintien à jour constitue l'une des mesures les plus efficaces pour réduire le risque d'exploitation de vulnérabilités connues.

Le référentiel privilégie une politique de mise à jour maîtrisée, documentée et adaptée au contexte de l'infrastructure.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27002.

## Documentation officielle

- Apache HTTP Server Documentation.
- Documentation Debian.
- Documentation Ubuntu.

## Guides techniques

- SOCLE – Stéphane Robert (gestion des mises à jour et maintien en condition de sécurité).

## Veille

La veille de sécurité devra couvrir les annonces des éditeurs, les bulletins de sécurité des distributions Linux et les référentiels utilisés par le projet.
