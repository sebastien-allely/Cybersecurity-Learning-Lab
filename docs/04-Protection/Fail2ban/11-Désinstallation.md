# Désinstallation de Fail2ban

| Élément | Valeur |
|---|---|
| **Nom du document** | `11-Désinstallation.md` |
| **Technologie** | Fail2ban et gestion des paquets Linux |
| **Catégorie** | Maintenance et retrait de composant |
| **Objectif** | Décrire une désinstallation contrôlée de Fail2ban et les vérifications nécessaires après son retrait. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

Cette procédure décrit les précautions à prendre avant de retirer Fail2ban d'un hôte Debian ou Ubuntu. La désinstallation réduit la protection contre les tentatives répétées détectées par les jails : elle doit être justifiée et approuvée.

## 2. Prérequis

- Confirmer que Fail2ban est installé et identifier son usage.
- Identifier les jails, filtres et actions personnalisés.
- Vérifier les protections compensatoires en place.
- Disposer d'un accès d'administration de secours.
- Sauvegarder la configuration utile et enregistrer les éléments nécessaires à l'audit.
- Prévoir une fenêtre de changement et une validation après retrait.

## 3. Évaluer l'installation

Afficher l'état du service :

```bash
sudo systemctl status fail2ban --no-pager
```

**Objectif :** déterminer si le service fonctionne. L'absence de service ne prouve pas que le paquet est absent.

Vérifier si le paquet est installé :

```bash
dpkg-query -W -f='${Status} ${Version}\n' fail2ban
```

**Interprétation :** si le paquet est installé, la sortie indique son état et sa version. Une erreur peut signifier que le paquet n'est pas connu comme installé.

## 4. Sauvegarder la configuration

Avant toute désinstallation, sauvegarder la configuration selon les procédures de sauvegarde de l'hôte. Examiner les fichiers sous `/etc/fail2ban/` et repérer les personnalisations nécessaires à l'analyse ou à une éventuelle réinstallation.

Ne pas publier cette sauvegarde : elle peut contenir des informations sur les services et l'architecture. Vérifier l'emplacement et les permissions de la copie avant de poursuivre.

## 5. Retrait du paquet

**Opération à impact :** la commande suivante désinstalle le paquet Fail2ban. Ne l'exécuter qu'après approbation et validation des protections compensatoires.

```bash
sudo apt remove fail2ban
```

**Interprétation :** APT retire le logiciel sans demander la suppression systématique de tous les fichiers de configuration. Examiner la proposition d'APT avant de confirmer. Cette commande ne garantit pas le nettoyage de règles de pare-feu personnalisées ou de fichiers créés manuellement.

La purge de configuration n'est pas incluse dans cette procédure standard. Ne pas utiliser `apt purge` ou supprimer manuellement des fichiers sans avoir établi qu'ils ne sont plus nécessaires.

## 6. Vérifications après retrait

- Vérifier l'état du paquet et du service.
- Examiner les règles de pare-feu et actions personnalisées qui auraient été installées ou modifiées par l'intégration.
- Vérifier qu'aucune autre protection n'est affectée.
- Vérifier les alertes Zabbix attendues : elles peuvent signaler l'absence du composant et doivent être traitées selon la décision de changement.
- Documenter les protections restantes et le risque résiduel.

Ne pas supprimer des règles de pare-feu au hasard : leur origine et leurs dépendances doivent être identifiées avant toute modification.

## 7. Retour arrière

Si le retrait doit être annulé, réinstaller le paquet depuis les dépôts de la distribution, restaurer la configuration sauvegardée si nécessaire, puis vérifier le service, les jails, les journaux et la supervision. La réinstallation seule ne garantit pas la restauration exacte de la configuration antérieure.

## 8. Références

- [Fail2ban — Documentation](https://www.fail2ban.org/wiki/index.php/Main_Page)
- [Debian — APT](https://www.debian.org/doc/manuals/apt-guide/)
- [Ubuntu Server — Documentation](https://documentation.ubuntu.com/server/)
