# Manifeste du projet

| Élément | Valeur |
|---|---|
| **Nom du document** | `01-Manifeste.md` |
| **Technologie** | Référentiel du laboratoire |
| **Catégorie** | Méthode de conception |
| **Objectif** | Définir la vision, les objectifs et les engagements du projet Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Vision

**Cybersecurity-Learning-Lab** est un projet pédagogique destiné à concevoir, déployer, sécuriser, superviser et maintenir un environnement informatique de laboratoire. Il vise à développer une compréhension pratique de la cybersécurité défensive et à conserver une trace vérifiable des décisions techniques.

Le dépôt documente des méthodes, architectures, configurations, procédures et exercices. Il ne prétend pas fournir une configuration universelle adaptée à tous les environnements.

## 2. Objectifs

- Comprendre les composants d'une infrastructure et leurs dépendances.
- Appliquer une démarche de sécurité dès la conception.
- Réduire la surface d'attaque et limiter les privilèges.
- Justifier les choix techniques par des besoins et des risques identifiés.
- Vérifier les changements avant leur généralisation.
- Superviser les composants et préparer leur maintenance.
- Documenter les limites, risques résiduels et procédures de retour arrière.
- Développer une documentation reproductible, révisable et anonymisée.

## 3. Principes directeurs

### Sécurité proportionnée au risque

Une mesure doit répondre à un besoin identifié et réduire un risque explicite. La complexité ajoutée doit être justifiée par le bénéfice attendu.

### Défense en profondeur

La protection repose sur plusieurs contrôles complémentaires : configuration sécurisée, filtrage réseau, gestion des identités, mises à jour, supervision, sauvegardes et réponse aux incidents.

### Moindre privilège

Les utilisateurs, services et composants disposent uniquement des droits nécessaires à leurs fonctions. Les accès d'administration sont limités et contrôlés.

### Vérification avant généralisation

Les changements sont testés dans un périmètre maîtrisé. La validation comprend des critères observables, des résultats attendus et, lorsque c'est pertinent, une procédure de retour arrière.

### Traçabilité et amélioration continue

Les décisions, exceptions, limites et actions correctives sont documentées. Le cycle d'amélioration s'inspire de la logique PDCA : planifier, réaliser, vérifier et ajuster.

## 4. Références et statut des recommandations

Les documents peuvent s'appuyer sur les recommandations de l'ANSSI, les publications du NIST, les guides OWASP, MITRE ATT&CK, les documentations officielles des éditeurs et des guides techniques reconnus. Le SOCLE de Stéphane Robert est une référence d'implémentation et non une norme.

Le dépôt distingue :
- les exigences ou recommandations issues d'une source identifiée ;
- les comportements décrits par la documentation officielle ;
- les choix d'architecture propres au laboratoire ;
- les éléments non encore déployés ou non encore validés.

## 5. Périmètre et limites

Le projet est un laboratoire d'apprentissage. Les procédures doivent être adaptées et testées avant tout usage dans un environnement de production. Une commande ou une configuration publiée ne doit pas être interprétée comme une garantie de sécurité absolue.

Les états « prévu », « en cours », « déployé » et « validé » ne sont pas interchangeables. Une mise en œuvre n'est considérée comme validée que lorsque les contrôles documentés ont été exécutés et que leurs résultats sont connus.

## 6. Engagements documentaires

Chaque document respecte le guide de rédaction et la charte du dépôt. Les exemples publics utilisent des valeurs génériques et ne révèlent ni adresses réelles, ni noms internes, ni comptes, secrets, chemins personnels ou détails permettant d'identifier l'infrastructure d'origine.

Les changements passent par une branche dédiée et une Pull Request vers `main`, conformément au processus de contribution.

## 7. Références

- [ANSSI — Publications](https://cyber.gouv.fr/publications)
- [NIST — Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [OWASP](https://owasp.org/)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [GitHub Docs — Pull requests](https://docs.github.com/en/pull-requests)
- [Guide de rédaction](../00-Introduction/DOC-000-Writing-Guide.md)
- [Principes de conception](./02-Principes-de-conception.md)
- [Charte de rédaction](./03-Charte-de-redaction.md)
