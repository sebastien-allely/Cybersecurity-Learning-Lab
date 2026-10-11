# Checklist qualité documentaire

| Élément | Valeur |
|---|---|
| **Nom du document** | `Documentation-Quality-Checklist.md` |
| **Technologie** | Qualité documentaire |
| **Catégorie** | Gestion du projet |
| **Objectif** | Fournir une liste de vérification applicable avant publication ou modification importante d'un document. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Utilisation

Utiliser cette checklist avant de demander la revue d'une documentation nouvelle ou modifiée. Les éléments non applicables peuvent être indiqués comme tels avec une justification.

## 2. Structure et cohérence

- [ ] Le document répond à un objectif explicite et identifié.
- [ ] Les sept champs de métadonnées obligatoires sont présents.
- [ ] Le titre interne, le nom du fichier et le contenu correspondent.
- [ ] La structure est adaptée au type de document et suit le guide de rédaction.
- [ ] Les liens internes, ancres et références croisées sont corrects.
- [ ] Les termes techniques et noms de produits sont utilisés de manière cohérente.
- [ ] Les informations redondantes ont été évitées ou reliées au document de référence.

## 3. Exactitude technique

- [ ] Les faits vérifiés sont distingués des recommandations et choix du projet.
- [ ] Les versions, prérequis et limites sont indiqués lorsque nécessaires.
- [ ] Les affirmations importantes sont soutenues par des sources fiables.
- [ ] Les procédures sont compatibles avec le périmètre décrit.
- [ ] Les éléments non testés ne sont pas présentés comme validés.
- [ ] Les références correspondent au produit et à la version concernés.

## 4. Commandes et procédures

- [ ] Chaque commande est complète, copiable et expliquée.
- [ ] Le contexte d'exécution et les privilèges requis sont indiqués.
- [ ] Le résultat attendu et son interprétation sont précisés.
- [ ] Les commandes destructrices ou à impact sont signalées avant leur exécution.
- [ ] Les prérequis, contrôles postérieurs et erreurs possibles sont décrits.
- [ ] Un retour arrière est fourni lorsqu'il est pertinent et techniquement possible.
- [ ] Les scripts ont été testés avant d'être présentés comme validés.

## 5. Sécurité et anonymisation

- [ ] Aucun mot de passe, jeton, secret, certificat privé ou clé privée n'est présent.
- [ ] Les adresses IP et noms d'hôtes réels ont été remplacés par des valeurs génériques.
- [ ] Les domaines internes, comptes, chemins personnels, partages et identifiants ont été anonymisés.
- [ ] Les journaux, captures éventuelles et sorties de commandes ne révèlent pas l'infrastructure privée.
- [ ] Les privilèges nécessaires sont limités au minimum.
- [ ] Les impacts sur la disponibilité et les accès d'administration sont identifiés.
- [ ] Les limites et risques résiduels sont explicités.

## 6. Supervision et exploitation

- [ ] La supervision est décrite lorsqu'elle est pertinente pour le composant.
- [ ] Les alertes proposées ont un objectif et une interprétation explicites.
- [ ] Les étapes de maintenance et de mise à jour sont abordées lorsque nécessaires.
- [ ] Les vérifications après changement sont identifiées.
- [ ] Les opérations de retrait ou de retour arrière ne laissent pas de protection résiduelle inconnue.

## 7. Qualité rédactionnelle

- [ ] Le texte est clair, factuel et suffisamment concis.
- [ ] Les acronymes sont développés à leur première occurrence lorsque cela aide le lecteur.
- [ ] Les tableaux et blocs de code sont lisibles.
- [ ] Les fautes, doublons et caractères parasites ont été recherchés.
- [ ] Les références sont directement pertinentes et accessibles.
- [ ] Le statut du contenu est explicite : prévu, en cours, déployé ou validé.

## 8. Contrôles Git et Pull Request

- [ ] La branche est dédiée à un objectif cohérent.
- [ ] La PR cible `main` et décrit les motivations et le périmètre.
- [ ] Les fichiers modifiés sont limités au besoin annoncé.
- [ ] Les différences ont été relues.
- [ ] Les contrôles adaptés ont été exécutés et leurs résultats sont indiqués.
- [ ] Les commentaires de revue ont été traités.
- [ ] Aucun changement direct non revu n'a été effectué sur `main`.

## 9. Décision

La documentation peut être proposée à la fusion lorsque tous les contrôles applicables sont satisfaits. Toute exception doit être justifiée dans la PR ; une exception ne doit pas masquer une donnée sensible ou un risque non maîtrisé.

## 10. Références

- [Guide de rédaction](../00-Introduction/DOC-000-Writing-Guide.md)
- [Charte de rédaction](../01-Methode-de-conception/03-Charte-de-redaction.md)
- [Processus de contribution et de revue](./Contribution-Review-Process.md)
- [ANSSI](https://cyber.gouv.fr/)
- [NIST CSRC](https://csrc.nist.gov/)
- [OWASP](https://owasp.org/)
