# Inventaire initial de la V2.0

| Élément | Valeur |
|---|---|
| **Nom du document** | `Inventaire-V2.0.md` |
| **Technologie** | Inventaire des actifs et gestion de configuration |
| **Catégorie** | Gestion du projet |
| **Objectif** | Établir un état initial vérifiable des composants, dépendances, écarts et preuves à collecter avant les chantiers de sécurisation de la V2.0. |
| **Auteur** | Sébastien Allely |
| **Version** | 0.3 |
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

Les identifiants **ACT-001 à ACT-007 reprennent la nomenclature existante du laboratoire**. ACT-008 et ACT-009 prolongent cette séquence pour les deux composants PKI identifiés dans le périmètre V2.0 ; aucun identifiant existant n'est réattribué. ACT-007 est hors périmètre opérationnel dans l'état historique disponible. Les statuts d'ACT-003 et d'ACT-004 doivent être confirmés par une collecte datée avant d'engager un chantier. La criticité indiquée ci-dessous est une appréciation initiale, à confirmer lors de l'analyse de risques.

| Identifiant | Actif / fonction | État connu à la préparation de la V2.0 | Criticité initiale | Dépendances principales | Vérifications prioritaires |
|---|---|---|---|---|
| ACT-001 | Active Directory et DNS associé | **Observé historiquement** — service d'annuaire déployé ; la supervision de services Windows principaux a commencé. La mention de LDAP dans la roadmap V1 correspond à un domaine documenté et ne prouve pas qu'un consommateur LDAP est configuré ou utilise actuellement le service. Aucun consommateur LDAP n'était identifié lors du dernier contrôle connu ; ce point doit être reconfirmé. LDAPS n'est pas considéré comme validé. | À évaluer | Virtualisation, réseau, DNS, synchronisation horaire, sauvegardes, certificats pour le futur LDAPS | Rôles et services actifs ; clients LDAP réellement configurés ; ports et flux ; état des alertes ; stratégie de récupération ; prérequis et tests des certificats avant toute obligation LDAPS. |
| ACT-002 | Supervision centralisée Zabbix | **Observé historiquement** — serveur Zabbix déployé ; des éléments de supervision des services AD ont été configurés. L'affichage d'un widget restait à finaliser lors du dernier état connu. | À évaluer | Virtualisation, réseau, base de données, agents, comptes techniques, horloge | Version actuelle ; disponibilité du serveur et des agents ; éléments, déclencheurs, tags, dépendances et tableaux de bord existants ; qualité des alertes ; sauvegarde et restauration de la configuration et de la base. |
| ACT-003 | Hôte de conteneurs | **Observé historiquement** — hôte Linux et moteur de conteneurs présents ; la liste et l'état des conteneurs doivent être réinventoriés. L'interface d'administration HTTPS utilisait un certificat autosigné. Ne pas déduire de cette observation que les conteneurs attendus sont actifs ou à jour. | À évaluer | Virtualisation, réseau, DNS, stockage, gestion des secrets, mises à jour | État réel de la machine ; système et moteur ; conteneurs et images ; ports publiés ; privilèges ; provenance des images ; secrets ; stratégie de mise à jour et de retour arrière ; certificat de l'interface d'administration. |
| ACT-004 | Gestion de parc et inventaire applicatif GLPI | **Préparé, non validé** — une montée de version a été préparée ; la version effectivement installée après migration et la validation fonctionnelle restent à confirmer. | À évaluer | Système Linux, serveur web, PHP, base de données, sauvegardes, accès d'administration, supervision | Version actuelle ; état de migration de la base ; tests fonctionnels ; plugins ; agents ; permissions ; exposition réseau ; preuve de sauvegarde exploitable et retour arrière. |
| ACT-005 | Nœud de virtualisation Proxmox VE 1 | **Observé historiquement** — premier nœud du cluster à deux nœuds. Le cluster et son quorum ont été observés ; aucun QDevice n'était en place. | À évaluer | Réseau, stockage, alimentation, accès d'administration, sauvegardes, second nœud | Version et état actuels ; quorum après incidents/redémarrages ; configuration de haute disponibilité ; règles de pare-feu ; accès de secours ; stockage et dépendances des VM. |
| ACT-006 | Nœud de virtualisation Proxmox VE 2 | **Observé historiquement** — second nœud du cluster à deux nœuds. La virtualisation constitue une dépendance critique des services hébergés. | À évaluer | Réseau, stockage, alimentation, accès d'administration, sauvegardes, premier nœud | Version et état actuels ; quorum après incidents/redémarrages ; configuration de haute disponibilité ; règles de pare-feu ; accès de secours ; stockage et dépendances des VM. |
| ACT-007 | Ancienne machine Windows / ancien RODC | **Hors périmètre opérationnel selon l'état historique** — l'ancien contrôleur de domaine en lecture seule a été rétrogradé, retiré du domaine et arrêté. Il ne doit pas être présenté comme un service actif. | Sans criticité opérationnelle présumée ; à confirmer | Hyperviseur et stockage tant que la VM existe | Confirmer l'état arrêté ; vérifier l'absence de dépendance résiduelle ; décider et documenter son devenir avant toute suppression ou réutilisation. |
| ACT-008 | PKI-ROOT — autorité racine sur machine dédiée | **Préparé, non validé** — une machine Debian de base a été installée sur la box Internet ; le rôle d'autorité racine, la génération/protection de la clé et les cérémonies PKI ne sont pas considérés comme validés. La machine est prévue pour rester normalement arrêtée hors opérations contrôlées. | **Critique (provisoire)** | Box Internet et virtualisation qu'elle fournit, accès d'administration, stockage durable et sauvegarde protégée de la clé, horloge fiable ; dépendance de confiance de l'AC intermédiaire | Vérifier que l'AC racine n'émet pas au quotidien ; état du service CA ; génération et protection de la clé privée ; sauvegarde/restauration et procédure de récupération ; période de validité ; contrôle d'accès ; procédure d'émission du certificat de l'intermédiaire ; procédure de révocation et renouvellement. |
| ACT-009 | Service d'autorité de certification intermédiaire sur l'hôte de conteneurs | **Planifié / à confirmer** — le service d'AC intermédiaire doit être hébergé sur Docker ; son déploiement, sa configuration et sa validation ne sont pas établis par la seule présence de l'hôte de conteneurs. Il doit émettre les certificats destinés aux services du laboratoire. | **Critique (provisoire)** | ACT-003 (hôte de conteneurs), ACT-008 (AC racine pour la chaîne de confiance), réseau, DNS, horloge, stockage persistant, gestion des secrets, sauvegardes et supervision | Confirmer le moteur et l'état des conteneurs ; identifier le logiciel CA et sa version ; vérifier la chaîne racine/intermédiaire et les contraintes de signature ; protéger la clé privée ; définir les droits d'émission, profils et durées ; inventaire des certificats ; révocation/renouvellement ; sauvegarde/restauration ; journaux et alertes ; test de panne et procédure de reprise. |

### Fonctions transverses et cibles planifiées

Les lignes suivantes décrivent des domaines de travail, et **ne reçoivent pas de nouvel identifiant ACT dans ce document**. Leur rattachement à un identifiant stable ne sera fait qu'après vérification de la nomenclature du référentiel.

| Domaine | État connu à la préparation de la V2.0 | Vérifications prioritaires |
|---|---|---|
| Sauvegardes des machines virtuelles | **Observé historiquement** — sauvegardes planifiées vers un partage SMB externe aux hyperviseurs ; aucun Proxmox Backup Server n'était déployé dans l'état connu. | Tâches et rétention actuelles ; résultats des dernières exécutions ; protection des accès ; capacité ; intégrité des archives ; test de restauration ; objectifs RPO/RTO et résultats mesurés. |
| Réseau et filtrage | **À confirmer** — l'architecture connue reposait sur un réseau local non segmenté ; une évolution de l'architecture réseau était envisagée. La politique IPv6 demandée doit être vérifiée système par système et équipement par équipement. | Cartographie des zones et flux ; règles effectives ; accès de secours ; exposition des interfaces d'administration ; état IPv6 ; plan de retour arrière avant tout filtrage restrictif. |
| Stockage dédié / NAS | **Planifié** — cible de stockage dédiée à étudier ; le déploiement et les tests de restauration ne sont pas confirmés. | Capacité utile ; conséquences de disques de tailles différentes ; stratégie de redondance ; bruit et consommation ; accès SMB/NFS ; comptes dédiés ; alertes de stockage ; test de restauration. |
| DNS filtrant | **À confirmer** — des travaux d'installation et de filtrage réseau ont été engagés ; le rôle DNS réellement utilisé par les clients et l'état final du service doivent être établis. | Service et version actuels ; clients réellement configurés ; ports DNS ; résolveurs amont ; comportement en cas de panne ; filtrage et accès d'administration ; supervision. |
| PKI — cycle de vie et chaîne de confiance | Les composants sont détaillés en ACT-008 (AC racine) et ACT-009 (AC intermédiaire). Leur état reste préparé/planifié et non validé ; la criticité initiale des deux est critique, à confirmer par analyse de risques. | Vérifier la séparation des rôles racine/intermédiaire ; protection et sauvegarde des clés ; contrôle d'accès ; profils et droits d'émission ; inventaire des certificats ; révocation, renouvellement et tests de restauration. |
| Poste d'administration | **Observé historiquement** — un poste Windows d'administration du laboratoire est utilisé. | Mises à jour ; comptes et privilèges ; outils d'administration ; secrets locaux ; accès aux interfaces ; protection du poste et procédure de secours. |

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
- **PKI et LDAPS :** l'installation d'une machine de base ne signifie pas qu'une autorité est opérationnelle. L'AC racine (ACT-008) doit rester hors ligne par défaut et n'être activée que pour des opérations contrôlées ; l'AC intermédiaire (ACT-009), prévue sur l'hôte Docker, sera le service d'émission courant. La compromission de l'une ou l'autre peut affecter la confiance de toute l'infrastructure. LDAPS dépend de certificats valides et de tests des clients.
- **Conteneurs et DNS filtrant :** réinventorier les services actifs et leurs flux plutôt que se fier aux listes historiques.

## 5. Méthode de collecte des preuves

Chaque chantier suit le cycle méthodologique du projet, fondé notamment sur le SOCLE de Stéphane Robert comme référence d'implémentation (et non comme norme) :

**Inventaire vérifié → analyse des risques → plan d'action → exécution contrôlée → validation → documentation → Pull Request.**

Ce cycle est appliqué à chaque travail, y compris aux évolutions de configuration, aux changements de supervision, aux mises à niveau, aux règles réseau et aux scripts. L'inventaire et l'analyse précèdent l'intervention ; les critères d'acceptation et les moyens de retour arrière sont définis avant l'exécution lorsque le changement le nécessite. La validation repose sur des résultats observables, et la Pull Request permet la revue des changements avant leur intégration.

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
- les risques critiques et les critères d'acceptation des phases suivantes sont définis, notamment pour l'AC racine et l'AC intermédiaire ;
- la séparation racine/intermédiaire, la protection des clés privées, les sauvegardes/restaurations, la révocation et le renouvellement PKI sont documentés et testés avant de déclarer la PKI opérationnelle ;
- la documentation publique est anonymisée et aucune valeur sensible n'y est ajoutée.

## 7. Références

- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [NIST SP 800-53 — Security and Privacy Controls](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)
- [ANSSI — Publications](https://cyber.gouv.fr/publications)
- SOCLE de Stéphane Robert — référence d'implémentation décrite dans le [référentiel des guides techniques](../98-References/03-Guides-techniques.md) ; ne constitue pas une norme.
- [Documentation officielle Proxmox VE](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/documentation)
- [Documentation officielle Zabbix](https://www.zabbix.com/documentation/current/en/manual)
