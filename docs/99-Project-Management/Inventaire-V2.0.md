# Inventaire initial de la V2.0

| Élément | Valeur |
|---|---|
| **Nom du document** | `Inventaire-V2.0.md` |
| **Technologie** | Inventaire des actifs et gestion de configuration |
| **Catégorie** | Gestion du projet |
| **Objectif** | Établir un état initial vérifiable des composants, dépendances, écarts et preuves à collecter avant les chantiers de sécurisation de la V2.0. |
| **Auteur** | Sébastien Allely |
| **Version** | 0.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objet et limites

Ce document ouvre la phase V2.0. Il consolide les informations déjà disponibles et les points qui doivent être vérifiés à nouveau avant toute modification. Il ne constitue pas une preuve que chaque état décrit est encore actuel.

Les données opérationnelles permettant d'identifier l'infrastructure réelle (adresses, noms d'hôtes, domaines internes, comptes, interfaces, chemins, partages et détails de supervision) restent dans le référentiel privé de travail. La documentation publique conserve des rôles génériques et ne publie pas ces valeurs.

Les versions exactes, les adresses et les paramètres détaillés sont à relever dans l'inventaire opérationnel privé au moment de la vérification. Une information historique n'est pas considérée comme actuelle sans contrôle daté.

## 2. Statuts utilisés

| Statut | Signification |
|---|---|
| **Observé historiquement** | Information issue d'une vérification antérieure ; une nouvelle vérification est nécessaire. |
| **Préparé, non validé** | Des prérequis ou fichiers ont été préparés, mais la mise en œuvre finale ou sa validation n'est pas confirmée. |
| **À confirmer** | Les éléments disponibles ne permettent pas de conclure sur l'état actuel. |
| **Planifié** | Intention de conception ; ne pas considérer comme déployé. |
| **Validé** | À utiliser uniquement après contrôle daté, résultat enregistré et critères d'acceptation satisfaits. |

## 3. Inventaire initial des actifs

| Identifiant | Actif / fonction | État connu à la préparation de la V2.0 | Dépendances principales | Vérifications prioritaires |
|---|---|---|---|---|
| ACT-001 | Plateforme de virtualisation en cluster | **Observé historiquement** — cluster à deux nœuds ; quorum observé ; pas de QDevice. La virtualisation est une dépendance critique des services hébergés. | Réseau, stockage, alimentation, accès d'administration, sauvegardes | Versions et état des nœuds ; quorum après incidents/redémarrages ; configuration de haute disponibilité ; règles de pare-feu ; accès de secours ; dépendances de stockage. |
| ACT-002 | Active Directory et DNS | **Observé historiquement** — service d'annuaire déployé ; supervision de services Windows principaux commencée. Aucun consommateur LDAP n'était identifié lors du dernier état connu ; ce point doit être confirmé. LDAPS n'est pas considéré comme validé. | Virtualisation, réseau, DNS, synchronisation horaire, sauvegardes, certificats pour le futur LDAPS | État des rôles et services ; clients LDAP réellement configurés ; ports et flux ; stratégie de récupération ; état des alertes Zabbix ; exigences de certificats avant toute obligation LDAPS. |
| ACT-003 | Supervision centralisée | **Observé historiquement** — serveur Zabbix déployé ; des éléments de supervision des services AD ont été configurés. L'affichage lisible d'un widget restait à finaliser. | Virtualisation, réseau, base de données, agents, comptes techniques, horloge | Version actuelle ; disponibilité du serveur et des agents ; éléments, déclencheurs, tags, dépendances et tableaux de bord existants ; qualité des alertes ; sauvegarde et restauration de la configuration et de la base. |
| ACT-004 | Gestion de parc et inventaire applicatif | **Préparé, non validé** — une montée de version GLPI a été préparée ; la version effectivement installée après migration et la validation fonctionnelle restent à confirmer. | Système Linux, serveur web, PHP, base de données, sauvegardes, accès d'administration, supervision | Version actuelle ; état de migration de la base ; tests fonctionnels ; plugins ; agents ; permissions ; exposition réseau ; preuve de sauvegarde exploitable et retour arrière. |
| ACT-005 | Hôte de conteneurs | **Observé historiquement** — hôte Linux et moteur de conteneurs présents ; une interface d'administration HTTPS utilisait un certificat autosigné. La liste et l'état des conteneurs doivent être réinventoriés. | Virtualisation, réseau, DNS, stockage, gestion des secrets, mises à jour | Système et moteur actuels ; conteneurs/images réellement actifs ; ports publiés ; privilèges ; provenance des images ; secrets ; stratégie de mise à jour et de retour arrière ; certificat de l'interface d'administration. |
| ACT-006 | Environnement de préparation de la PKI | **Préparé, non validé** — une machine de base a été installée ; le service d'autorité de certification et son cycle de vie ne sont pas considérés comme déployés et validés sur la seule base de cette installation. | Protection des clés, sauvegardes, résolution de noms, synchronisation horaire, procédure d'activation | État réel des services ; séparation racine/intermédiaire ; stockage et sauvegarde des clés ; contrôle d'accès ; inventaire des certificats ; révocation et renouvellement. |
| ACT-007 | Sauvegardes des machines virtuelles | **Observé historiquement** — sauvegardes planifiées vers un partage SMB externe à l'hyperviseur ; aucun Proxmox Backup Server n'était déployé dans l'état connu. Un test de restauration documenté reste à confirmer. | Hyperviseur, réseau, stockage cible, identifiants de sauvegarde, capacité disponible | Tâches et rétention actuelles ; résultats des dernières exécutions ; protection des accès ; capacité ; intégrité des archives ; test de restauration prioritaire ; objectifs RPO/RTO et résultats mesurés. |
| ACT-008 | Réseau et filtrage | **À confirmer** — l'architecture connue reposait sur un réseau local non segmenté ; OPNsense était envisagé. La politique IPv6 demandée doit être vérifiée système par système et équipement par équipement. | Routeur/passerelle, commutation, interfaces des hyperviseurs, pare-feu locaux, DNS, accès d'administration | Cartographie des zones et flux ; règles effectives ; accès de secours ; exposition des interfaces d'administration ; état IPv6 ; services qui en dépendent ; plan de retour arrière avant tout filtrage restrictif. |
| ACT-009 | Stockage de sauvegarde dédié / NAS | **Planifié** — cible de stockage dédiée à étudier ; le déploiement et les tests de restauration ne sont pas confirmés. | Réseau, disques, système de fichiers, alimentation, surveillance, politique de sauvegarde | Besoin de capacité utile ; conséquences de disques de tailles différentes ; stratégie de redondance ; bruit et consommation ; accès SMB/NFS ; comptes dédiés ; alertes de stockage ; test de restauration. |
| ACT-010 | Service DNS filtrant | **À confirmer** — des travaux d'installation et de filtrage réseau ont été engagés ; le rôle DNS effectivement utilisé par les clients et l'état final du service doivent être établis. | Passerelle, DHCP, résolveurs amont, règles réseau, disponibilité de la VM | Service et version actuels ; clients réellement configurés ; ports DNS ; résolveurs amont ; comportement en cas de panne ; filtrage et accès d'administration ; supervision. |
| ACT-011 | Poste d'administration | **Observé historiquement** — un poste Windows dédié à l'administration du laboratoire est utilisé. | Réseau, comptes d'administration, MFA si disponible, outils d'accès distant, sauvegarde des configurations | État des mises à jour ; comptes et privilèges ; outils d'administration ; secrets locaux ; accès aux interfaces ; protection du poste et procédure de secours. |

## 4. Écarts documentaires déjà visibles

La documentation d'architecture de la V1 décrit certains composants avec des noms génériques historiques et des dépendances qui ne sont pas nécessairement actuels. Elle doit être comparée à l'état observé avant d'être reprise comme source de vérité.

Les points suivants sont à traiter pendant l'inventaire :

- **Virtualisation :** actualiser la répartition des machines virtuelles, leurs hôtes, leur criticité et leurs dépendances.
- **Active Directory :** ne pas présenter l'intégration LDAP de l'application de gestion de parc comme opérationnelle sans preuve ; aucun consommateur LDAP n'était identifié lors du dernier contrôle connu.
- **GLPI :** distinguer la préparation de la montée de version de la migration réellement effectuée et validée.
- **Zabbix :** préserver les éléments, déclencheurs, tags et dépendances déjà présents ; inventorier avant tout ajout.
- **Sauvegardes :** distinguer réussite d'une tâche, intégrité d'une archive et restauration effectivement testée.
- **Réseau :** ne pas publier de règle de filtrage restrictive avant l'inventaire et le test des flux nécessaires.
- **IPv6 :** l'intention de désactivation n'est pas une preuve de désactivation effective sur l'ensemble des composants.
- **PKI et LDAPS :** l'installation d'une machine de base ne signifie pas qu'une autorité est opérationnelle ; LDAPS dépend de certificats valides et de tests des clients.
- **Conteneurs et DNS filtrant :** réinventorier les services actifs et leurs flux plutôt que se fier aux listes historiques.

## 5. Méthode de collecte des preuves

Pour chaque actif, enregistrer dans le référentiel opérationnel privé :

1. Identifiant stable et rôle.
2. État observé, date et méthode de vérification.
3. Version exacte du système et des composants.
4. Emplacement d'hébergement et dépendances.
5. Interfaces et flux nécessaires.
6. Services et ports en écoute, avec leur justification.
7. Contrôles de sécurité et de supervision effectivement configurés.
8. Sauvegardes disponibles et dernier test de restauration.
9. Criticité, impact d'une panne et objectifs RPO/RTO applicables.
10. Écarts, risque résiduel, action suivante et preuve de clôture.

Une commande exécutée, une configuration préparée ou un service installé ne suffit pas, à lui seul, à marquer un contrôle « validé ». Conserver un résultat vérifiable et sa date ; masquer les valeurs privées avant toute publication.

## 6. Critères de sortie de V2.0

La phase V2.0 pourra être considérée comme terminée lorsque :

- chaque actif actif ou planifié est identifié et son statut est confirmé ;
- les versions et configurations critiques ont été relevées à une date connue ;
- les dépendances entre hyperviseurs, réseau, annuaire, applications, supervision et sauvegardes sont documentées ;
- les flux nécessaires à l'administration et au fonctionnement sont recensés ;
- les sauvegardes et tests de restauration sont distingués sans ambiguïté ;
- les écarts entre documentation et réalité sont listés, priorisés et associés à une action ;
- les risques critiques et les critères d'acceptation des phases suivantes sont définis ;
- la documentation publique est anonymisée et aucune valeur sensible n'y est ajoutée.

## 7. Références

- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [NIST SP 800-53 — Security and Privacy Controls](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)
- [ANSSI — Publications](https://cyber.gouv.fr/publications)
- [Documentation officielle Proxmox VE](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/documentation)
- [Documentation officielle Zabbix](https://www.zabbix.com/documentation/current/en/manual)
