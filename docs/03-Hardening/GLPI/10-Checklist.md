# 10 - Checklist

| Élément                           | Valeur                                                                                                  |
| --------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `10-Checklist.md`                                                                                       |
| **Technologie**                   | GLPI                                                                                                    |
| **Catégorie**                     | Hardening                                                                                               |
| **Objectif**                      | Vérifier l'application des mesures de durcissement de GLPI et de ses principaux composants de sécurité. |
| **Auteur**                        | Sébastien Allely                                                                                        |
| **Version**                       | 1.0                                                                                                     |
| **Date de dernière modification** | 03/08/2026                                                                                              |

---

## 1. Application GLPI

* [ ] La version de GLPI installée est connue.
* [ ] La version utilisée est supportée.
* [ ] Les extensions installées sont identifiées.
* [ ] Les extensions inutilisées sont supprimées ou désactivées.
* [ ] Les fonctionnalités non nécessaires sont désactivées.
* [ ] La configuration de GLPI est documentée.
* [ ] Les fichiers de configuration critiques sont protégés et sauvegardés.

---

## 2. Comptes et privilèges

* [ ] Les comptes GLPI sont identifiés.
* [ ] Les comptes inutilisés sont désactivés ou supprimés.
* [ ] Les comptes administrateurs sont identifiés.
* [ ] Le nombre de comptes disposant de privilèges élevés est limité.
* [ ] Les droits sont attribués selon le principe du moindre privilège.
* [ ] Les comptes techniques sont identifiés et justifiés.

---

## 3. Authentification

* [ ] Le mécanisme d'authentification utilisé est documenté.
* [ ] L'intégration LDAP/Active Directory est correctement configurée lorsque nécessaire.
* [ ] Les paramètres de connexion à l'annuaire sont protégés.
* [ ] Les groupes ou utilisateurs autorisés sont maîtrisés.
* [ ] Les comptes administrateurs ne disposent pas de droits excessifs.
* [ ] Les mécanismes d'authentification inutilisés sont désactivés.

---

## 4. Apache et HTTPS

Lorsque GLPI est publié par Apache :

* [ ] Apache est correctement configuré.
* [ ] HTTPS est utilisé.
* [ ] Le certificat est valide.
* [ ] Les protocoles et suites cryptographiques obsolètes sont désactivés.
* [ ] HTTP est redirigé vers HTTPS lorsque nécessaire.
* [ ] L'accès à GLPI est limité au périmètre réseau attendu.
* [ ] Les fichiers sensibles de l'application ne sont pas directement accessibles depuis le Web.

---

## 5. PHP

* [ ] La version de PHP est supportée.
* [ ] Les extensions PHP nécessaires sont identifiées.
* [ ] Les extensions inutiles sont désactivées lorsque possible.
* [ ] La configuration PHP est adaptée au rôle du serveur.
* [ ] Les informations techniques inutiles ne sont pas exposées aux utilisateurs.
* [ ] Les fichiers de configuration PHP sont protégés.

---

## 6. MariaDB

* [ ] La version de MariaDB est supportée.
* [ ] Le compte utilisé par GLPI est dédié.
* [ ] Le compte GLPI ne dispose que des privilèges nécessaires.
* [ ] L'accès à MariaDB est limité.
* [ ] Les comptes inutilisés sont supprimés.
* [ ] Les données de la base sont sauvegardées.
* [ ] Les fichiers de configuration MariaDB sont protégés et sauvegardés.

---

## 7. Protection des données

* [ ] Les données GLPI sont identifiées.
* [ ] Les données sensibles sont protégées.
* [ ] Les permissions sur les fichiers de l'application sont vérifiées.
* [ ] Les permissions sur les fichiers de configuration sont vérifiées.
* [ ] Les sauvegardes sont protégées.
* [ ] Une procédure de restauration existe.
* [ ] Une restauration a été testée.

---

## 8. Journalisation

* [ ] Les journaux GLPI nécessaires sont disponibles.
* [ ] Les journaux Apache sont disponibles.
* [ ] Les journaux PHP pertinents sont disponibles.
* [ ] Les journaux MariaDB pertinents sont disponibles.
* [ ] Les journaux système sont accessibles.
* [ ] Les événements de sécurité importants peuvent être investigués.
* [ ] La conservation des journaux est adaptée au besoin.

---

## 9. Mises à jour et vulnérabilités

* [ ] La version de GLPI est régulièrement contrôlée.
* [ ] Les mises à jour de sécurité sont suivies.
* [ ] Les composants PHP sont maintenus à jour.
* [ ] Apache est maintenu à jour.
* [ ] MariaDB est maintenu à jour.
* [ ] Les vulnérabilités affectant les composants sont évaluées.
* [ ] Les mises à jour importantes sont documentées.

---

## 10. Supervision

La supervision par **Zabbix** doit permettre de détecter les principales anomalies.

* [ ] La disponibilité de GLPI est supervisée.
* [ ] Apache est supervisé.
* [ ] MariaDB est supervisé.
* [ ] L'espace disque est supervisé.
* [ ] Les ressources système sont supervisées.
* [ ] Les services critiques sont supervisés.
* [ ] Les alertes importantes sont testées.

La supervision ne remplace pas l'analyse des journaux ni les contrôles de sécurité.

---

## 11. Configuration

Les fichiers de configuration critiques doivent être **protégés et sauvegardés**.

Les principaux éléments à identifier comprennent notamment :

```text
/etc/apache2/
/etc/php/
/etc/mysql/
/etc/glpi/
```

Le chemin exact dépend de la méthode d'installation et de la version des composants.

Les fichiers réellement utilisés par l'installation doivent être identifiés avant toute modification.

---

## 12. Sauvegarde et restauration

* [ ] La base de données GLPI est sauvegardée.
* [ ] Les fichiers nécessaires au fonctionnement de GLPI sont sauvegardés.
* [ ] Les configurations Apache sont sauvegardées.
* [ ] Les configurations PHP nécessaires sont sauvegardées.
* [ ] Les configurations MariaDB nécessaires sont sauvegardées.
* [ ] Les sauvegardes sont protégées.
* [ ] Une restauration de la base a été testée.
* [ ] Une restauration complète a été envisagée ou testée.

Une sauvegarde qui n'a jamais été restaurée ne permet pas de démontrer la capacité réelle de récupération.

---

## 13. Contrôle final

* [ ] GLPI fonctionne normalement.
* [ ] L'accès HTTPS fonctionne.
* [ ] L'authentification fonctionne.
* [ ] L'intégration LDAP/Active Directory fonctionne lorsque nécessaire.
* [ ] MariaDB fonctionne.
* [ ] Apache fonctionne.
* [ ] Aucun service inutile n'est exposé.
* [ ] Les permissions sont cohérentes.
* [ ] Les journaux sont disponibles.
* [ ] Zabbix reçoit les données attendues.
* [ ] Les sauvegardes sont disponibles.
* [ ] Les fichiers de configuration critiques sont protégés et sauvegardés.

---

## 14. Résultat

| Contrôle               | Résultat                  |
| ---------------------- | ------------------------- |
| Application GLPI       | ☐ Conforme ☐ Non conforme |
| Comptes et privilèges  | ☐ Conforme ☐ Non conforme |
| Authentification       | ☐ Conforme ☐ Non conforme |
| Apache / HTTPS         | ☐ Conforme ☐ Non conforme |
| PHP                    | ☐ Conforme ☐ Non conforme |
| MariaDB                | ☐ Conforme ☐ Non conforme |
| Protection des données | ☐ Conforme ☐ Non conforme |
| Journalisation         | ☐ Conforme ☐ Non conforme |
| Mises à jour           | ☐ Conforme ☐ Non conforme |
| Supervision            | ☐ Conforme ☐ Non conforme |
| Sauvegarde             | ☐ Conforme ☐ Non conforme |
| Contrôle final         | ☐ Conforme ☐ Non conforme |

Toute non-conformité doit être documentée et faire l'objet d'une action corrective, d'une mesure compensatoire ou d'une justification.

---

## 15. Conclusion

Cette checklist constitue le contrôle final du durcissement de GLPI.

Elle vérifie non seulement l'application elle-même, mais également ses principales dépendances : Apache, PHP, MariaDB, HTTPS, l'authentification et la supervision.

Le niveau de sécurité réel de GLPI dépend donc de la sécurisation cohérente de l'ensemble de cette chaîne.
