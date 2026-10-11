# Supervision de Fail2ban avec Zabbix

| Élément | Valeur |
|---|---|
| **Nom du document** | `08-Supervision-Zabbix.md` |
| **Technologie** | Fail2ban et Zabbix |
| **Catégorie** | Protection et supervision |
| **Objectif** | Définir les objectifs, contrôles et limites de la supervision de Fail2ban. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif et périmètre

La supervision vise à détecter une indisponibilité de Fail2ban, une perte de fonctionnement des jails attendues ou une anomalie dans les journaux utiles. Elle complète les contrôles du système et du pare-feu ; elle ne garantit pas à elle seule l'efficacité des filtres ni l'absence d'attaque.

Le mode de collecte (agent, vérifications actives ou passives, journalisation) doit être choisi selon l'architecture et la version de Zabbix déployées.

## 2. Prérequis

- Zabbix Agent 2 ou une méthode de collecte explicitement retenue est installé et fonctionnel.
- Les droits de collecte sont limités aux commandes et fichiers nécessaires.
- La liste des jails attendues et leur objectif sont documentés.
- Les journaux ne contiennent pas de secrets et leur accès est contrôlé.
- Les contrôles sont testés en préproduction ou sur un hôte de laboratoire.

## 3. Contrôles recommandés

| Contrôle | Finalité | Limite |
|---|---|---|
| État du service Fail2ban | Détecter un arrêt ou un échec de démarrage | Un service actif ne prouve pas que toutes les jails fonctionnent |
| Présence des jails attendues | Repérer une jail désactivée ou absente | La liste doit être maintenue après chaque changement |
| État des jails et compteurs | Repérer des changements anormaux ou une absence de données | Les valeurs doivent être interprétées dans le contexte des journaux |
| Erreurs récentes du service | Détecter une erreur de configuration ou d'accès aux journaux | Les motifs dépendent de la distribution et de la version |
| Fonctionnement de l'agent Zabbix | Distinguer un problème de collecte d'une panne de Fail2ban | La disponibilité de l'agent ne garantit pas la validité des données |

## 4. Déploiement des contrôles

1. Définir les éléments et déclencheurs requis dans le modèle Zabbix adapté à la version utilisée.
2. Limiter les commandes privilégiées à une liste explicite ; ne pas autoriser un accès root générique à l'agent.
3. Tester la collecte avec une jail existante et vérifier les cas de service arrêté, jail absente et collecte en erreur.
4. Définir des seuils et fenêtres de détection cohérents avec l'usage du serveur.
5. Documenter les dépendances entre les déclencheurs afin d'éviter les alertes en cascade lors d'une panne de l'agent.

Aucun UserParameter n'est fourni comme prêt à déployer dans ce document : sa commande, ses droits, son format de sortie et son comportement en erreur doivent être définis puis testés avant publication d'une configuration exécutable.

## 5. Vérification et interprétation

Une validation complète doit démontrer que :
- l'état du service est correctement détecté ;
- une jail attendue absente génère le résultat prévu ;
- les erreurs de collecte sont visibles et distinctes des états fonctionnels ;
- les valeurs remontées correspondent à l'état observé localement ;
- une panne de l'agent ne produit pas de fausses conclusions sur Fail2ban.

Conserver les résultats de test dans la documentation interne du laboratoire sans publier les noms d'hôtes, adresses ou journaux privés.

## 6. Risques et retour arrière

Une mauvaise règle de détection peut produire des alertes inutiles ou masquer un défaut réel. Une commande privilégiée mal conçue peut élargir les droits de l'agent. Valider les permissions et les scénarios d'erreur avant activation.

Pour revenir en arrière, désactiver les éléments ou déclencheurs introduits et retirer les droits de collecte spécifiques après vérification qu'ils ne sont pas partagés avec d'autres contrôles. Ne pas supprimer une règle sudo ou un paramètre commun sans vérifier ses dépendances.

## 7. Références

- [Zabbix — Documentation](https://www.zabbix.com/documentation/current/en/manual)
- [Fail2ban — Documentation du projet](https://www.fail2ban.org/wiki/index.php/Main_Page)
- [Debian — Documentation](https://www.debian.org/doc/)
