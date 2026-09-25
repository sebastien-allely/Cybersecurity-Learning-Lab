# 10 - Checklist

| Élément                           | Valeur                                                                                                                                       |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `10-Checklist.md`                                                                                                                            |
| **Technologie**                   | Active Directory Domain Services                                                                                                             |
| **Catégorie**                     | Hardening                                                                                                                                    |
| **Objectif**                      | Vérifier l'application des mesures de durcissement d'Active Directory Domain Services et la protection du service d'annuaire du laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                                             |
| **Version**                       | 1.0                                                                                                                                          |
| **Date de dernière modification** | 03/08/2026                                                                                                                                   |

---

> **Utilisation pédagogique**
>
> Cette checklist constitue un support de contrôle destiné à l'apprenant.
> Les cases sont volontairement laissées non cochées et doivent être renseignées lors de la réalisation du contrôle.
>
> Une case cochée signifie que le contrôle a été effectivement réalisé et ne constitue pas, à elle seule, une preuve de conformité permanente.

---

## 1. Infrastructure Active Directory

* [ ] Le rôle Active Directory Domain Services est identifié.
* [ ] Les contrôleurs de domaine sont identifiés.
* [ ] Le rôle de chaque contrôleur de domaine est documenté.
* [ ] Les services Active Directory nécessaires sont identifiés.
* [ ] Les dépendances DNS sont documentées.
* [ ] Les niveaux fonctionnels utilisés sont connus.
* [ ] Les fonctionnalités inutilisées sont désactivées lorsque possible.

---

## 2. Comptes et privilèges

* [ ] Les comptes administrateurs sont identifiés.
* [ ] Les comptes inutilisés sont désactivés ou supprimés.
* [ ] Les comptes privilégiés sont limités.
* [ ] Les comptes d'administration sont séparés des comptes utilisateurs standards lorsque nécessaire.
* [ ] Les appartenances aux groupes privilégiés sont régulièrement contrôlées.
* [ ] Les comptes de service sont identifiés.
* [ ] Les privilèges des comptes de service sont limités.
* [ ] Les comptes disposant de privilèges élevés sont surveillés.

Une attention particulière doit être portée aux groupes :

```text
Domain Admins
Enterprise Admins
Administrators
Schema Admins
```

---

## 3. Authentification

* [ ] Les politiques de mots de passe sont définies.
* [ ] Les paramètres de verrouillage des comptes sont définis.
* [ ] Les protocoles d'authentification obsolètes sont identifiés.
* [ ] NTLM est évalué et limité lorsque possible.
* [ ] L'utilisation de Kerberos est privilégiée.
* [ ] Les comptes privilégiés sont particulièrement protégés.
* [ ] Les mécanismes d'authentification faibles sont identifiés.

Les paramètres d'authentification doivent être adaptés au contexte du laboratoire et documentés.

---

## 4. Réduction de la surface d'attaque

* [ ] Les services actifs sur le contrôleur de domaine sont identifiés.
* [ ] Les services inutiles sont désactivés lorsque possible.
* [ ] Les ports réseau nécessaires sont identifiés.
* [ ] Les flux réseau vers le contrôleur de domaine sont limités.
* [ ] Les accès d'administration sont restreints.
* [ ] Les interfaces d'administration ne sont pas inutilement exposées.
* [ ] Les protocoles obsolètes sont désactivés lorsque possible.
* [ ] LLMNR est évalué.
* [ ] NetBIOS over TCP/IP est évalué.
* [ ] SMBv1 est désactivé s'il n'est pas nécessaire.

---

## 5. Stratégies de groupe

* [ ] Les GPO appliquées sont identifiées.
* [ ] Les GPO inutilisées sont supprimées ou désactivées.
* [ ] Les paramètres de sécurité sont documentés.
* [ ] Les paramètres de sécurité des postes et serveurs sont cohérents.
* [ ] Les scripts de démarrage et d'ouverture de session sont contrôlés.
* [ ] Les paramètres permettant l'exécution de logiciels ou scripts sont maîtrisés.
* [ ] Les modifications importantes des GPO sont documentées.

---

## 6. DNS

* [ ] Le rôle DNS associé à Active Directory est identifié.
* [ ] Les zones DNS sont documentées.
* [ ] Les transferts de zone sont contrôlés.
* [ ] Les redirecteurs DNS sont identifiés.
* [ ] Les mises à jour dynamiques sont maîtrisées.
* [ ] Les serveurs DNS autorisés sont identifiés.
* [ ] Les journaux DNS pertinents sont disponibles.

Le DNS constitue une dépendance critique d'Active Directory et doit être traité comme tel.

---

## 7. Journalisation et détection

* [ ] L'audit des événements de sécurité est activé.
* [ ] Les événements liés aux authentifications sont journalisés.
* [ ] Les événements liés aux comptes privilégiés sont journalisés.
* [ ] Les modifications importantes de l'annuaire sont détectables.
* [ ] Les journaux sont protégés contre les modifications non autorisées.
* [ ] La conservation des journaux est définie.
* [ ] Les événements importants peuvent être analysés après incident.

Les événements de sécurité doivent pouvoir être corrélés avec les autres éléments de supervision du laboratoire.

---

## 8. Protection des données

* [ ] Les données Active Directory sont identifiées.
* [ ] Les fichiers système critiques sont protégés.
* [ ] Les permissions sur les répertoires sensibles sont vérifiées.
* [ ] Les fichiers de configuration critiques sont protégés et sauvegardés.
* [ ] Les sauvegardes Active Directory sont protégées.
* [ ] Les données nécessaires à une restauration sont identifiées.

Une compromission du contrôleur de domaine doit être considérée comme un événement critique pour l'infrastructure.

---

## 9. Mises à jour et vulnérabilités

* [ ] Le niveau de mise à jour du système est connu.
* [ ] Les mises à jour de sécurité sont appliquées.
* [ ] Les vulnérabilités affectant Windows Server et Active Directory sont suivies.
* [ ] Les correctifs critiques sont évalués rapidement.
* [ ] Les mises à jour importantes sont documentées.
* [ ] Le fonctionnement d'Active Directory est contrôlé après mise à jour.

---

## 10. Supervision

Active Directory doit être intégré à la supervision du laboratoire.

* [ ] La disponibilité du contrôleur de domaine est supervisée.
* [ ] Les services Active Directory critiques sont supervisés.
* [ ] DNS est supervisé.
* [ ] Les ressources système sont supervisées.
* [ ] L'espace disque est supervisé.
* [ ] Les événements critiques peuvent générer une alerte.
* [ ] Les alertes importantes ont été testées.

La supervision par **Zabbix** doit compléter l'analyse des journaux Windows et ne pas la remplacer.

---

## 11. Sauvegarde et restauration

* [ ] Une stratégie de sauvegarde Active Directory est définie.
* [ ] Les sauvegardes sont protégées contre les accès non autorisés.
* [ ] Les sauvegardes sont stockées sur un emplacement approprié.
* [ ] La rétention est définie.
* [ ] La restauration d'Active Directory est documentée.
* [ ] Une procédure de restauration est disponible.
* [ ] Une restauration a été testée dans le laboratoire.

La sauvegarde doit permettre de restaurer l'annuaire dans un état cohérent après une défaillance ou une compromission.

---

## 12. Protection et sauvegarde des configurations

Les éléments critiques de configuration doivent être **protégés et sauvegardés**.

La documentation doit notamment identifier :

```text
Active Directory
DNS
GPO
Configuration réseau
Paramètres d'authentification
Politiques de sécurité
```

Les fichiers et paramètres nécessaires à la reconstruction du contrôleur de domaine doivent être pris en compte dans la stratégie de sauvegarde.

---

## 13. Contrôle des accès d'administration

* [ ] Les accès d'administration sont limités.
* [ ] Les comptes administrateurs sont identifiés.
* [ ] Les connexions administratives sont journalisées.
* [ ] Les postes utilisés pour administrer Active Directory sont maîtrisés.
* [ ] Les accès distants d'administration sont protégés.
* [ ] Les privilèges permanents sont limités lorsque possible.
* [ ] Les appartenances aux groupes privilégiés sont régulièrement réévaluées.

---

## 14. Contrôle final

* [ ] Comptes privilégiés contrôlés.
* [ ] Groupes privilégiés contrôlés.
* [ ] Politiques d'authentification vérifiées.
* [ ] GPO vérifiées.
* [ ] DNS vérifié.
* [ ] Services inutiles désactivés.
* [ ] Protocoles obsolètes évalués.
* [ ] Journalisation opérationnelle.
* [ ] Supervision opérationnelle.
* [ ] Mises à jour appliquées.
* [ ] Vulnérabilités évaluées.
* [ ] Configuration critique protégée et sauvegardée.
* [ ] Sauvegarde disponible.
* [ ] Procédure de restauration disponible.
* [ ] Restauration testée.
* [ ] Les événements de sécurité importants peuvent être investigués.

---

## 15. Résultat

| Contrôle                        | Résultat                  |
| ------------------------------- | ------------------------- |
| Infrastructure Active Directory | ☐ Conforme ☐ Non conforme |
| Comptes et privilèges           | ☐ Conforme ☐ Non conforme |
| Authentification                | ☐ Conforme ☐ Non conforme |
| Surface d'attaque               | ☐ Conforme ☐ Non conforme |
| Stratégies de groupe            | ☐ Conforme ☐ Non conforme |
| DNS                             | ☐ Conforme ☐ Non conforme |
| Journalisation                  | ☐ Conforme ☐ Non conforme |
| Protection des données          | ☐ Conforme ☐ Non conforme |
| Mises à jour                    | ☐ Conforme ☐ Non conforme |
| Supervision                     | ☐ Conforme ☐ Non conforme |
| Sauvegarde / restauration       | ☐ Conforme ☐ Non conforme |
| Accès d'administration          | ☐ Conforme ☐ Non conforme |
| Contrôle final                  | ☐ Conforme ☐ Non conforme |

Toute non-conformité doit être documentée et faire l'objet d'une correction, d'une mesure compensatoire ou d'une justification.

---

## 16. Conclusion

Cette checklist constitue le contrôle final du durcissement d'Active Directory Domain Services.

Compte tenu du rôle central de l'annuaire, une compromission d'Active Directory peut affecter une part importante du laboratoire. La protection doit donc couvrir simultanément les comptes privilégiés, l'authentification, les GPO, DNS, les services exposés, la journalisation, la supervision et les mécanismes de restauration.
