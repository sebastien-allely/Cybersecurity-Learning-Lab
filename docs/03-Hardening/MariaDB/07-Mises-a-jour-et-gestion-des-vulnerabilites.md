# 07 - Mises à jour et gestion des vulnérabilités


| Élément | Valeur |
| **Nom du document** | `07-Mises-a-jour-et-gestion-des-vulnerabilites.md` |
| **Technologie** | MariaDB |
| **Catégorie** | Hardening |
| **Objectif** | Définir les mesures de gestion des mises à jour et des vulnérabilités de MariaDB. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La sécurité de MariaDB ne dépend pas uniquement de sa configuration initiale.

L'apparition régulière de nouvelles vulnérabilités impose une politique de maintien en condition de sécurité fondée sur une veille active, des mises à jour maîtrisées et une réévaluation régulière des risques.

---

# 2. Actifs concernés

Les décisions présentées concernent notamment :

- le serveur MariaDB ;
- les moteurs de stockage (InnoDB, Aria...) ;
- les plugins installés ;
- les bibliothèques utilisées ;
- le système d'exploitation ;
- les applications dépendantes ;
- les sauvegardes.

---

# 3. Risques identifiés

Une politique de mise à jour insuffisante peut entraîner :

- l'exploitation de vulnérabilités connues ;
- une compromission des données ;
- une indisponibilité du service ;
- une augmentation de la dette technique ;
- une incompatibilité avec les recommandations de sécurité.

---

# 4. Principes de conception

## Utiliser une version supportée

Le référentiel retient exclusivement des versions bénéficiant d'un support de sécurité.

---

## Maîtriser les mises à jour

Chaque mise à jour constitue une modification du système.

Elle doit être :

- planifiée ;
- documentée ;
- testée lorsque cela est possible ;
- validée après son déploiement.

---

## Assurer une veille

Une veille de sécurité doit couvrir :

- MariaDB ;
- Debian ou Ubuntu ;
- OpenSSL ;
- les bibliothèques utilisées ;
- les recommandations du SOCLE de Stéphane Robert.

---

## Évaluer les vulnérabilités

Chaque vulnérabilité doit être analysée selon :

- son impact réel ;
- les composants concernés ;
- l'exposition du laboratoire ;
- les mesures compensatoires existantes.

---

# 5. Décisions retenues

Le référentiel retient les décisions suivantes :

- maintenir MariaDB dans une version supportée ;
- appliquer les correctifs de sécurité dans des délais adaptés à leur criticité ;
- documenter les mises à jour réalisées ;
- vérifier le fonctionnement des applications après chaque mise à jour ;
- réévaluer régulièrement les décisions de sécurité.

---

# 6. Vérification

Une revue régulière doit permettre de vérifier :

- la version de MariaDB ;
- les versions des composants associés ;
- les correctifs appliqués ;
- les composants arrivant en fin de support.

---

# 7. Supervision

Les événements suivants présentent une valeur opérationnelle :

- disponibilité d'une mise à jour critique ;
- échec d'une mise à jour ;
- indisponibilité du service après mise à jour ;
- vulnérabilité critique affectant MariaDB.

---

# 8. Bonnes pratiques

Avant toute mise à jour, il convient de répondre aux questions suivantes :

- Quel composant est concerné ?
- Quelle vulnérabilité est corrigée ?
- Quel impact sur GLPI01 ?
- Existe-t-il un retour arrière ?
- Les sauvegardes ont-elles été vérifiées ?

---

# 9. Conclusion

Le maintien à jour constitue une mesure essentielle de réduction du risque.

Le référentiel privilégie des mises à jour planifiées, documentées et cohérentes avec les recommandations des éditeurs et des référentiels utilisés.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- NIST Cybersecurity Framework.
- ISO/IEC 27002.

## Documentation officielle

- Documentation MariaDB.
- Documentation Debian.
- Documentation Ubuntu.

## Guides techniques

- SOCLE – Stéphane Robert (vérifié avant chaque mise à jour du présent document).

## Veille

Ce document devra être revu lors de toute évolution significative de MariaDB, des distributions Linux utilisées ou des recommandations du SOCLE.
