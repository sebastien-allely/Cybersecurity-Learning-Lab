# Désinstallation de Fail2ban

| Élément | Valeur |
|---|---|
| **Nom du document** | `11-Désinstallation.md` |
| **Technologie** | Fail2ban et système Linux |
| **Catégorie** | Maintenance et retrait |
| **Objectif** | Décrire une démarche de retrait contrôlé de Fail2ban en limitant le risque de laisser des règles résiduelles ou de réduire involontairement la protection. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif et avertissement

La désinstallation supprime ou désactive une couche de protection contre certaines tentatives répétées. Elle ne doit être effectuée qu'après validation du besoin, identification d'une mesure de remplacement éventuelle et planification d'une fenêtre de changement.

Les commandes exactes dépendent de la distribution, de la méthode d'installation et du pare-feu utilisé. Ce document décrit une procédure de décision, pas une séquence de commandes universelle.

## 2. Prérequis

- Confirmer l'autorisation de retirer le composant.
- Identifier les services et jails protégés, les filtres personnalisés, les exclusions et les actions de pare-feu.
- Vérifier les dépendances de supervision et d'automatisation.
- Sauvegarder la configuration utile et les éléments nécessaires à une restauration.
- Disposer d'un accès d'administration alternatif.
- Définir la mesure compensatoire et le responsable de son maintien, si le besoin de protection persiste.

## 3. Procédure contrôlée

1. **Inventorier :** relever les jails actives, filtres locaux, fichiers de configuration, actions et éléments de supervision.
2. **Évaluer :** documenter le risque lié à la suppression et les contrôles qui resteront en place.
3. **Désactiver progressivement :** utiliser la procédure supportée par la distribution et observer les effets avant la suppression des paquets.
4. **Contrôler le pare-feu :** vérifier les règles, chaînes ou ensembles créés par Fail2ban. Ne pas vider globalement le pare-feu pour retirer une règle.
5. **Désinstaller :** utiliser le gestionnaire de paquets correspondant à la distribution, après vérification de la liste des paquets qui seront retirés.
6. **Nettoyer avec prudence :** supprimer uniquement les configurations ou filtres personnalisés identifiés comme propres à ce déploiement et devenus inutiles.
7. **Vérifier :** confirmer l'état du service, l'absence des règles résiduelles identifiées, le fonctionnement des services protégés et l'actualisation de la supervision.
8. **Documenter :** consigner la date, le motif, les résultats, les risques résiduels et les mesures de remplacement.

## 4. Risques

- Une règle de pare-feu résiduelle peut provoquer un blocage inattendu.
- La suppression d'une règle trop large peut retirer des protections non liées à Fail2ban.
- Le retrait du paquet peut affecter une dépendance ou une automatisation.
- Une suppression prématurée peut exposer un service à des tentatives répétées.
- La suppression de fichiers de configuration peut empêcher un retour arrière simple.

Ne jamais exécuter une commande globale de vidage du pare-feu dans le seul but de désinstaller Fail2ban.

## 5. Retour arrière

Si le retrait produit un effet inattendu :
- restaurer le paquet selon le gestionnaire de paquets et la version disponibles ;
- restaurer les fichiers de configuration sauvegardés ;
- rétablir uniquement les règles nécessaires avec la méthode supportée par la configuration d'origine ;
- vérifier les jails, les journaux, les services protégés et la supervision.

Le retour arrière doit être testé ou planifié avant le retrait. La restauration des fichiers ne garantit pas que les règles dynamiques précédentes seront automatiquement rétablies.

## 6. Critères de clôture

Le retrait peut être considéré comme terminé lorsque le service est retiré conformément au plan, que les règles résiduelles ont été vérifiées, que les services restent accessibles, que la mesure compensatoire est active si nécessaire et que l'inventaire ainsi que la supervision sont à jour.

## 7. Références

- [Fail2ban — Documentation du projet](https://www.fail2ban.org/wiki/index.php/Main_Page)
- [Debian — Documentation](https://www.debian.org/doc/)
- [Ubuntu Server — Documentation](https://documentation.ubuntu.com/server/)
