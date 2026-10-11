# Maintenance de Fail2ban

| Élément | Valeur |
|---|---|
| **Nom du document** | `09-Maintenance.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Maintenance et protection |
| **Objectif** | Définir les contrôles périodiques permettant de maintenir Fail2ban fonctionnel et adapté aux évolutions du système. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

La maintenance de Fail2ban doit préserver la disponibilité des services protégés tout en vérifiant que les filtres, jails, journaux et actions restent adaptés. Toute modification est tracée et validée.

## 2. Prérequis et précautions

- Disposer d'un accès d'administration alternatif au service protégé.
- Connaître les jails activées, leurs fichiers de journal et les actions de bannissement utilisées.
- Disposer d'une sauvegarde des fichiers de configuration modifiés.
- Planifier les mises à jour et changements ayant un impact sur l'authentification ou le pare-feu.
- Ne pas publier de journaux réels ou d'informations identifiantes dans les preuves de test.

## 3. Contrôles périodiques

| Fréquence indicative | Contrôle | Résultat attendu |
|---|---|---|
| Après chaque changement | Validation de la configuration et de l'état du service | Pas d'erreur de syntaxe ; service opérationnel |
| Régulièrement | Revue des jails, filtres, seuils et exclusions | Chaque règle a un objectif actuel et documenté |
| Régulièrement | Analyse des journaux et faux positifs | Les événements sont compris ; aucune exclusion injustifiée |
| À chaque mise à jour | Lecture des notes de version et vérification des changements | Compatibilité confirmée ou plan de correction établi |
| Périodiquement | Revue des accès d'administration et de la supervision | Accès minimaux ; alertes pertinentes |
| Après incident | Analyse des bannissements et de l'efficacité de la règle | Décisions et actions correctives tracées |

Les fréquences exactes sont à adapter au niveau de risque, à l'exposition et à la fréquence des changements.

## 4. Mise à jour et changement de configuration

1. Identifier la version installée et les changements disponibles dans la distribution.
2. Lire les notes de version et identifier les changements de format ou de comportement.
3. Sauvegarder les fichiers de configuration concernés dans un emplacement protégé.
4. Appliquer le changement pendant une fenêtre adaptée au risque.
5. Valider la configuration avec les outils disponibles pour la version installée.
6. Redémarrer ou recharger le service uniquement selon la procédure supportée.
7. Vérifier le statut du service, les jails, les journaux, les règles de pare-feu et la supervision.

Ne pas appliquer une commande de mise à jour universelle sans connaître la distribution, sa politique de paquets et les dépendances locales.

## 5. Gestion des faux positifs

Avant d'ajouter une adresse à une liste d'exclusion, confirmer l'origine du trafic, l'usage légitime et le périmètre de l'exclusion. Préférer une exclusion minimale et temporaire, documentée avec un propriétaire et une date de révision. Une exclusion large peut neutraliser la protection pour une partie importante du réseau.

## 6. Retour arrière

Si un changement entraîne des erreurs ou bloque un accès légitime :
- utiliser l'accès d'administration de secours ;
- restaurer les seuls fichiers de configuration concernés depuis la sauvegarde ;
- vérifier la syntaxe et l'état du service ;
- vérifier les actions de pare-feu et les jails actives ;
- documenter la cause et la décision de reprise.

La restauration d'une configuration ne garantit pas l'annulation de toutes les actions déjà appliquées par le pare-feu. Vérifier l'état effectif des bannissements avant de conclure au retour à la normale.

## 7. Références

- [Fail2ban — Documentation du projet](https://github.com/fail2ban/fail2ban/wiki)
- [Debian — Documentation](https://www.debian.org/doc/)
- [Ubuntu Server — Documentation](https://documentation.ubuntu.com/server/)
