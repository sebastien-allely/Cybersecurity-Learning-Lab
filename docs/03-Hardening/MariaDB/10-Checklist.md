# 10 - Checklist

| Élément                           | Valeur                                                                                                                            |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `10-Checklist.md`                                                                                                                 |
| **Technologie**                   | MariaDB                                                                                                                           |
| **Catégorie**                     | Hardening                                                                                                                         |
| **Objectif**                      | Vérifier l'application des mesures de durcissement de MariaDB et la protection de la base de données utilisée par le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                                  |
| **Version**                       | 1.0                                                                                                                               |
| **Date de dernière modification** | 03/08/2026                                                                                                                        |

---

> **Utilisation pédagogique**
>
> Cette checklist constitue un support de contrôle destiné à l'apprenant.
> Les cases sont volontairement laissées non cochées et doivent être renseignées lors de la réalisation du contrôle.
>
> Une case cochée signifie que le contrôle a été effectivement réalisé et ne constitue pas, à elle seule, une preuve de conformité permanente.

---

## 1. Installation et version

* [ ] La version de MariaDB est connue.
* [ ] La version utilisée est supportée.
* [ ] Les paquets MariaDB installés sont identifiés.
* [ ] Les composants inutiles sont supprimés ou désactivés lorsque possible.
* [ ] Les mises à jour de sécurité sont suivies.
* [ ] Les vulnérabilités affectant MariaDB sont régulièrement évaluées.

Vérification de la version :

```bash
mariadb --version
```

---

## 2. Comptes et privilèges

* [ ] Les comptes MariaDB sont identifiés.
* [ ] Les comptes inutilisés sont supprimés ou désactivés.
* [ ] Les comptes administrateurs sont identifiés.
* [ ] Les comptes applicatifs sont distincts des comptes d'administration.
* [ ] Chaque application utilise un compte dédié lorsque nécessaire.
* [ ] Les privilèges sont limités au strict nécessaire.
* [ ] Les comptes anonymes sont absents.
* [ ] Les comptes disposant de privilèges élevés sont régulièrement contrôlés.

Vérification :

```sql
SELECT User, Host FROM mysql.user;
```

---

## 3. Authentification

* [ ] Le mécanisme d'authentification utilisé est connu.
* [ ] Les comptes disposent d'une méthode d'authentification adaptée.
* [ ] Les comptes inutilisés sont supprimés.
* [ ] Les accès administratifs sont protégés.
* [ ] Les identifiants ne sont pas stockés en clair dans les fichiers accessibles.
* [ ] Les secrets utilisés par les applications sont protégés.

Pour le compte utilisé par GLPI :

* [ ] Le compte est dédié à GLPI.
* [ ] Il ne dispose pas de privilèges d'administration globale.
* [ ] Son périmètre d'accès est limité à la base nécessaire.

---

## 4. Réduction de la surface d'attaque

* [ ] MariaDB n'est pas exposé inutilement sur le réseau.
* [ ] Le port d'écoute est connu.
* [ ] Les interfaces d'écoute sont identifiées.
* [ ] Les connexions distantes sont limitées au strict nécessaire.
* [ ] Les règles de pare-feu autorisent uniquement les flux nécessaires.
* [ ] Les fonctionnalités inutilisées sont désactivées lorsque possible.

Vérification :

```bash
ss -lntp | grep 3306
```

Le port `3306` ne doit pas être considéré comme devant être exposé par défaut.

---

## 5. Configuration

* [ ] Les fichiers de configuration actifs sont identifiés.
* [ ] Les paramètres de sécurité importants sont documentés.
* [ ] Les paramètres inutiles ou dangereux sont corrigés.
* [ ] Les permissions sur les fichiers de configuration sont vérifiées.
* [ ] Les fichiers de configuration sont protégés.
* [ ] Les configurations critiques sont sauvegardées avant modification.

Emplacements à examiner selon l'installation :

```text
/etc/mysql/
/etc/mysql/mariadb.conf.d/
```

La configuration réellement chargée doit être vérifiée avant toute modification.

---

## 6. Protection des données

* [ ] Les bases de données hébergées sont identifiées.
* [ ] Les données sensibles sont identifiées.
* [ ] Les droits d'accès aux bases sont contrôlés.
* [ ] Les fichiers de données sont protégés.
* [ ] Les permissions du répertoire de données sont vérifiées.
* [ ] Les sauvegardes sont protégées.
* [ ] Les sauvegardes ne sont pas accessibles aux utilisateurs non autorisés.

Pour le laboratoire, la base utilisée par GLPI doit notamment être considérée comme une donnée critique pour le fonctionnement de l'inventaire.

---

## 7. Journalisation

* [ ] Les mécanismes de journalisation utilisés sont connus.
* [ ] Les journaux pertinents sont disponibles.
* [ ] Les erreurs MariaDB sont détectables.
* [ ] Les accès ou événements de sécurité pertinents peuvent être investigués.
* [ ] Les journaux sont protégés contre les modifications non autorisées.
* [ ] La rotation des journaux est fonctionnelle.
* [ ] L'espace disque utilisé par les journaux est surveillé.

Les journaux réellement activés doivent être identifiés dans la configuration du serveur.

---

## 8. Mises à jour et vulnérabilités

* [ ] La version de MariaDB est régulièrement contrôlée.
* [ ] Les mises à jour de sécurité sont suivies.
* [ ] Les paquets système sont maintenus à jour.
* [ ] Les vulnérabilités affectant MariaDB sont évaluées.
* [ ] Les mises à jour importantes sont documentées.
* [ ] Le fonctionnement des applications dépendantes est contrôlé après mise à jour.

Vérification des paquets :

```bash
apt list --upgradable
```

---

## 9. Supervision

MariaDB doit être intégré à la supervision du laboratoire lorsque son rôle le justifie.

* [ ] La disponibilité du service est supervisée.
* [ ] L'état du service est surveillé.
* [ ] L'espace disque est surveillé.
* [ ] Les ressources système sont surveillées.
* [ ] Les erreurs importantes peuvent générer une alerte.
* [ ] Les anomalies affectant une application dépendante peuvent être détectées.
* [ ] Les alertes importantes ont été testées.

Pour GLPI, la supervision doit permettre de distinguer une indisponibilité de l'application d'une indisponibilité de sa base de données.

---

## 10. Sauvegarde

Les données MariaDB doivent être intégrées à la stratégie de sauvegarde du laboratoire.

* [ ] Les bases critiques sont identifiées.
* [ ] Les bases nécessaires à GLPI sont sauvegardées.
* [ ] Les sauvegardes sont protégées.
* [ ] Les sauvegardes sont stockées sur un emplacement distinct du serveur.
* [ ] La fréquence de sauvegarde est définie.
* [ ] La rétention est définie.
* [ ] Une restauration a été testée.

Une sauvegarde dont la restauration n'a jamais été testée ne permet pas de démontrer la capacité réelle de récupération.

---

## 11. Protection et sauvegarde des configurations

Les fichiers de configuration MariaDB doivent être **protégés et sauvegardés**.

À identifier notamment :

```text
/etc/mysql/
/etc/mysql/mariadb.conf.d/
```

La sauvegarde doit également prendre en compte les paramètres nécessaires à la reconstruction du service.

Les fichiers contenant des secrets ou des informations sensibles doivent conserver des permissions restrictives.

---

## 12. Validation après modification

Après toute modification importante de configuration :

```bash
systemctl status mariadb
```

Puis consulter les journaux :

```bash
journalctl -u mariadb -b
```

Lorsque nécessaire, vérifier également les connexions et le fonctionnement de l'application dépendante.

Pour GLPI :

* [ ] MariaDB fonctionne.
* [ ] GLPI peut accéder à sa base.
* [ ] Les opérations de lecture fonctionnent.
* [ ] Les opérations d'écriture fonctionnent.
* [ ] Aucune erreur MariaDB significative n'est apparue.

---

## 13. Contrôle final

* [ ] Version connue et supportée.
* [ ] Comptes identifiés.
* [ ] Comptes inutilisés supprimés.
* [ ] Privilèges minimisés.
* [ ] Authentification maîtrisée.
* [ ] Accès réseau limité.
* [ ] Port d'écoute justifié.
* [ ] Configuration sécurisée.
* [ ] Fichiers de configuration protégés.
* [ ] Données protégées.
* [ ] Journalisation disponible.
* [ ] Mises à jour suivies.
* [ ] Vulnérabilités évaluées.
* [ ] Supervision fonctionnelle.
* [ ] Sauvegardes disponibles.
* [ ] Restauration testée.
* [ ] Fonctionnement de GLPI vérifié après modification.

---

## 14. Résultat

| Contrôle                      | Résultat                  |
| ----------------------------- | ------------------------- |
| Installation et version       | ☐ Conforme ☐ Non conforme |
| Comptes et privilèges         | ☐ Conforme ☐ Non conforme |
| Authentification              | ☐ Conforme ☐ Non conforme |
| Surface d'attaque             | ☐ Conforme ☐ Non conforme |
| Configuration                 | ☐ Conforme ☐ Non conforme |
| Protection des données        | ☐ Conforme ☐ Non conforme |
| Journalisation                | ☐ Conforme ☐ Non conforme |
| Mises à jour                  | ☐ Conforme ☐ Non conforme |
| Supervision                   | ☐ Conforme ☐ Non conforme |
| Sauvegarde                    | ☐ Conforme ☐ Non conforme |
| Protection des configurations | ☐ Conforme ☐ Non conforme |
| Validation finale             | ☐ Conforme ☐ Non conforme |

Toute non-conformité doit être documentée et faire l'objet d'une correction, d'une mesure compensatoire ou d'une justification.

---

## 15. Conclusion

Cette checklist constitue le contrôle final du durcissement de MariaDB.

MariaDB doit être considéré comme un composant critique lorsqu'il héberge les données d'une application telle que GLPI. Sa sécurité dépend donc à la fois de la protection du moteur de base de données, des comptes, des données, de son exposition réseau, de sa journalisation, de sa supervision et de sa capacité de restauration.
