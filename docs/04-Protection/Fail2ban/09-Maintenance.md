# Maintenance de Fail2ban

| Élément | Valeur |
|---|---|
| **Nom du document** | `09-Maintenance.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Maintenance et protection |
| **Objectif** | Définir les contrôles périodiques et les opérations de maintenance sûres pour Fail2ban. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

La maintenance vise à conserver une protection fonctionnelle tout en limitant les régressions, les faux positifs et les interruptions de service.

## 2. Prérequis et précautions

- Disposer d'un accès d'administration de secours à l'hôte.
- Connaître les jails, filtres et actions réellement utilisés.
- Consulter les journaux et la supervision avant une modification.
- Sauvegarder les fichiers de configuration concernés avant de les modifier.
- Planifier les changements susceptibles de bloquer des accès légitimes.

Une règle de bannissement incorrecte peut bloquer l'administration distante. Effectuer les changements depuis une session de secours ou un accès console lorsque c'est possible.

## 3. Contrôles périodiques

| Fréquence indicative | Contrôle |
|---|---|
| À chaque changement | Syntaxe, service, jails attendues et tests des filtres modifiés |
| Régulièrement | État du service, erreurs dans les journaux et état de la supervision |
| À chaque mise à jour | Notes de version, compatibilité des filtres et actions, validation après mise à jour |
| Périodiquement | Pertinence des jails, seuils, durées de bannissement et exclusions |
| Lors d'un incident | Corrélation entre événements, journaux applicatifs, réseau et bannissements |

Adapter la fréquence au niveau de risque et à la criticité de l'hôte ; ce tableau est un point de départ, pas une fréquence réglementaire.

## 4. Contrôles de fonctionnement

Afficher l'état du service :

```bash
sudo systemctl status fail2ban --no-pager
```

**Interprétation :** rechercher un état actif et l'absence d'erreur récente pertinente. Un service actif ne suffit pas à démontrer l'efficacité des règles.

Afficher les jails chargées :

```bash
sudo fail2ban-client status
```

**Interprétation :** comparer la liste obtenue avec l'inventaire attendu pour cet hôte.

Examiner les journaux du service :

```bash
sudo journalctl -u fail2ban --since "24 hours ago" --no-pager
```

**Interprétation :** rechercher les erreurs de chargement, de configuration, de backend ou d'exécution. Adapter la fenêtre de temps au contexte de l'incident.

## 5. Modification d'un filtre ou d'une jail

1. Identifier la raison et le risque traité.
2. Sauvegarder les fichiers concernés et noter leur état initial.
3. Vérifier le filtre avec des journaux représentatifs et des cas négatifs.
4. Examiner la configuration et la disponibilité des jails.
5. Appliquer le changement dans une fenêtre maîtrisée.
6. Vérifier le service, les jails, les journaux et les alertes.
7. Consigner le résultat et la procédure de retour arrière.

Ne pas publier une expression régulière comme validée sans l'avoir testée avec des événements représentatifs. Éviter de modifier les fichiers fournis par le paquet lorsque des fichiers locaux dédiés permettent de conserver les personnalisations.

## 6. Mises à jour

Utiliser le mécanisme de mise à jour documenté pour la distribution et le processus de changement du laboratoire. Avant toute mise à jour, consulter les notes de version et déterminer si les filtres, backends ou actions personnalisés sont concernés.

Ne pas lancer une mise à jour sans sauvegarde, fenêtre de changement, vérification postérieure et accès de secours.

## 7. Retour arrière

Si la modification entraîne une erreur ou bloque un accès légitime :
- restaurer uniquement les fichiers sauvegardés qui ont été modifiés ;
- recharger ou redémarrer le service uniquement si nécessaire et après examen de l'impact ;
- vérifier l'état du service et des jails ;
- confirmer le rétablissement des accès et de la supervision ;
- documenter la cause et les mesures correctives.

Le retour arrière ne doit pas laisser volontairement une protection désactivée sans décision documentée et mesure compensatoire.

## 8. Références

- [Fail2ban — Documentation](https://www.fail2ban.org/wiki/index.php/Main_Page)
- [Debian — Documentation](https://www.debian.org/doc/)
- [Ubuntu Server — Documentation](https://documentation.ubuntu.com/server/)
