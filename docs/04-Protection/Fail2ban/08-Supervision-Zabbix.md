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

## 1. Objectif

La supervision doit détecter une indisponibilité de Fail2ban, une jail attendue absente ou une anomalie de fonctionnement. Elle complète les contrôles de sécurité et ne remplace pas l'analyse des journaux.

## 2. Prérequis

- Fail2ban installé et configuré sur l'hôte supervisé.
- Zabbix Agent 2 opérationnel et autorisé à communiquer avec le serveur ou le proxy Zabbix.
- Accès de lecture aux états nécessaires, sans octroyer de privilèges administratifs généraux à l'agent.
- Liste documentée des jails attendues pour l'hôte concerné.

## 3. Contrôles à envisager

| Contrôle | Objectif | Limite |
|---|---|---|
| État du service | Détecter un service arrêté ou en échec | Un service actif ne prouve pas que les filtres détectent correctement les événements |
| État des jails | Vérifier la présence des jails attendues | La liste dépend du rôle de l'hôte |
| État du processus | Détecter une anomalie de processus | Indicateur complémentaire |
| Journaux Fail2ban | Détecter erreurs de configuration et d'exécution | Nécessite une collecte adaptée |
| Événements de bannissement | Observer l'activité et ses variations | Une hausse ou une baisse n'est pas automatiquement un incident |

## 4. Vérifications locales

Afficher l'état du service :

```bash
sudo systemctl status fail2ban --no-pager
```

**Objectif :** vérifier l'état rapporté par systemd. Un service actif est un premier indicateur, pas une validation complète.

Afficher les jails chargées :

```bash
sudo fail2ban-client status
```

**Résultat attendu :** une réponse indiquant les jails actuellement chargées. Comparer la liste à l'inventaire attendu.

Afficher les détails d'une jail précise :

```bash
sudo fail2ban-client status sshd
```

**Objectif :** examiner la jail `sshd` si elle existe sur cet hôte. Remplacer ce nom par une jail réellement configurée ; une jail absente peut renvoyer une erreur.

## 5. Intégration Zabbix

Avant d'ajouter un item, un trigger ou une règle de découverte :
1. vérifier les items, triggers, tags, dépendances et templates déjà associés à l'hôte ;
2. rechercher si un contrôle équivalent existe ;
3. définir le type d'item, l'intervalle, la valeur de référence et le comportement en cas de donnée inconnue ;
4. limiter les droits de l'agent à la lecture strictement nécessaire ;
5. tester le contrôle et les cas de panne avant de l'activer à grande échelle.

Ne pas supposer qu'un template Fail2ban natif est présent. L'implémentation dépend de la version Zabbix, de la configuration de l'agent et du mécanisme de collecte retenu. Éviter les appels arbitraires à `sudo` depuis l'agent ; si un UserParameter est nécessaire, il doit être fixe, borné, documenté et testé.

## 6. Alertes et interprétation

Les alertes doivent distinguer le service indisponible, une jail attendue absente, une erreur de collecte et une activité de bannissement inhabituelle. Une absence de bannissements ne prouve pas l'absence d'attaques. Une activité élevée peut provenir d'un scan, d'une erreur de configuration ou d'un client légitime mal configuré.

## 7. Validation

- Vérifier le service et les jails localement.
- Vérifier que Zabbix reçoit des valeurs récentes et cohérentes.
- Simuler uniquement dans un environnement de test contrôlé les états dégradés pertinents.
- Confirmer que les triggers se déclenchent et se rétablissent selon les critères définis.
- Documenter les résultats, faux positifs et limites.

## 8. Références

- [Fail2ban — Documentation](https://www.fail2ban.org/wiki/index.php/Main_Page)
- [Zabbix — Documentation](https://www.zabbix.com/documentation/current/en/manual)
- [Zabbix — Agent 2](https://www.zabbix.com/documentation/current/en/manual/concepts/agent2)
- [MITRE ATT&CK — Brute Force (T1110)](https://attack.mitre.org/techniques/T1110/)
