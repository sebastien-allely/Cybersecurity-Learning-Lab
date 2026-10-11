# Veille technologique et sécurité

| Élément | Valeur |
|---|---|
| **Nom du document** | `04-Veille-technologique.md` |
| **Technologie** | Veille technologique |
| **Catégorie** | Références et maintenance |
| **Objectif** | Définir une méthode proportionnée de veille sur les vulnérabilités, versions, correctifs et recommandations applicables au laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

La veille sert à repérer les évolutions qui peuvent affecter la sécurité, la disponibilité ou la maintenabilité des composants documentés. Elle doit conduire à une décision tracée, et non à une mise à jour automatique sans analyse.

## 2. Sources à surveiller

- Avis de sécurité des éditeurs et projets utilisés.
- Bulletins et publications de l'ANSSI.
- Bases et avis de vulnérabilités reconnus, dont NVD et les avis des distributions.
- Notes de version et annonces de fin de support.
- Documentation officielle des produits et dépendances.
- Changements de référentiels ou de guides utilisés dans les procédures.

## 3. Processus

1. **Collecter :** identifier les avis qui concernent réellement les composants et versions du laboratoire.
2. **Qualifier :** vérifier la version affectée, l'exposition, les prérequis d'exploitation et les mesures compensatoires.
3. **Prioriser :** estimer la criticité en tenant compte de l'exploitabilité et de l'impact local.
4. **Décider :** mettre à jour, appliquer une mesure compensatoire, accepter temporairement le risque ou documenter l'absence d'action.
5. **Planifier :** définir les tests, sauvegardes, fenêtre de changement et retour arrière.
6. **Vérifier :** confirmer la version et les contrôles après changement.
7. **Tracer :** enregistrer la décision, les preuves, le responsable et l'échéance éventuelle.

## 4. Critères de priorisation

Prendre en compte la présence d'une version vulnérable, l'exposition réseau et les privilèges du composant, l'existence d'un exploit connu, la criticité de l'actif, la disponibilité d'un correctif et le risque d'indisponibilité induit par la mise à jour.

Ne pas se baser uniquement sur un score de vulnérabilité : le contexte d'exposition et l'impact sur le laboratoire sont déterminants.

## 5. Traçabilité minimale

Pour chaque avis significatif, consigner l'identifiant ou le lien, le composant et la version concernés, l'évaluation, la décision, l'échéance, le test et le résultat. Les données sensibles de l'infrastructure ne doivent pas être publiées.

## 6. Références

- [ANSSI](https://cyber.gouv.fr/)
- [NIST National Vulnerability Database](https://nvd.nist.gov/)
- [CISA Known Exploited Vulnerabilities Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
- [Debian Security](https://www.debian.org/security/)
- [Ubuntu Security Notices](https://ubuntu.com/security/notices)
