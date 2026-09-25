# 10 - Checklist

| Élément                           | Valeur                                                                                                                                   |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `10-Checklist.md`                                                                                                                        |
| **Technologie**                   | Apache HTTP Server                                                                                                                       |
| **Catégorie**                     | Hardening                                                                                                                                |
| **Objectif**                      | Vérifier l'application des mesures de durcissement d'Apache HTTP Server et la sécurité de son exposition HTTP/HTTPS dans le laboratoire. |
| **Auteur**                        | Sébastien Allely                                                                                                                         |
| **Version**                       | 1.0                                                                                                                                      |
| **Date de dernière modification** | 03/08/2026                                                                                                                               |

---

> **Utilisation pédagogique**
>
> Cette checklist constitue un support de contrôle destiné à l'apprenant.
> Les cases sont volontairement laissées non cochées et doivent être renseignées lors de la réalisation du contrôle.
>
> Une case cochée signifie que le contrôle a été effectivement réalisé et ne constitue pas, à elle seule, une preuve de conformité permanente.

---

## 1. Installation et version

* [ ] La version d'Apache HTTP Server est connue.
* [ ] La version utilisée est supportée.
* [ ] Les paquets Apache installés sont identifiés.
* [ ] Les modules activés sont recensés.
* [ ] Les modules inutiles sont désactivés lorsque possible.
* [ ] Les mises à jour de sécurité sont suivies.

```bash
apache2ctl -v
```

---

## 2. Configuration

* [ ] La configuration Apache est documentée.
* [ ] Les fichiers de configuration actifs sont identifiés.
* [ ] Les configurations inutiles sont supprimées ou désactivées.
* [ ] Les fichiers de configuration sont protégés.
* [ ] Les configurations critiques sont sauvegardées avant modification.
* [ ] La syntaxe de configuration est vérifiée après chaque modification.

```bash
apache2ctl configtest
```

Les fichiers de configuration doivent être **protégés et sauvegardés**.

---

## 3. Modules

Les modules actifs doivent être justifiés.

```bash
apache2ctl -M
```

Pour chaque module :

* [ ] Son rôle est connu.
* [ ] Son utilisation est justifiée.
* [ ] Son niveau de risque est pris en compte.
* [ ] Il est maintenu à jour.

Tout module inutile doit être désactivé lorsque cela est possible.

---

## 4. Surface d'attaque

* [ ] Les interfaces d'écoute sont connues.
* [ ] Les ports exposés sont justifiés.
* [ ] Les Virtual Hosts sont identifiés.
* [ ] Les services inutiles sont désactivés.
* [ ] L'accès aux interfaces d'administration est restreint.
* [ ] Les fichiers sensibles ne sont pas exposés.
* [ ] L'indexation des répertoires est désactivée lorsqu'elle n'est pas nécessaire.

```bash
ss -tulpen
```

---

## 5. HTTP et HTTPS

* [ ] HTTPS est utilisé lorsque des données sensibles sont transmises.
* [ ] Le certificat utilisé est valide.
* [ ] Le certificat correspond au service publié.
* [ ] Les protocoles obsolètes sont désactivés.
* [ ] Les suites cryptographiques faibles sont exclues.
* [ ] Les paramètres TLS sont régulièrement réévalués.
* [ ] HTTP est redirigé vers HTTPS lorsque nécessaire.

---

## 6. En-têtes HTTP

Les en-têtes de sécurité pertinents doivent être évalués.

Selon le contexte :

* [ ] `Strict-Transport-Security` est configuré lorsque pertinent.
* [ ] `X-Content-Type-Options` est configuré.
* [ ] `Content-Security-Policy` est évaluée.
* [ ] `Referrer-Policy` est évaluée.
* [ ] Les informations techniques inutilement exposées sont limitées.

La configuration doit tenir compte des applications publiées afin de ne pas provoquer de dysfonctionnement.

---

## 7. Contrôle d'accès

* [ ] Les répertoires accessibles depuis le Web sont identifiés.
* [ ] Les permissions sont vérifiées.
* [ ] Les fichiers de configuration ne sont pas accessibles publiquement.
* [ ] Les fichiers cachés ou sensibles ne sont pas exposés.
* [ ] Les répertoires d'administration sont protégés.
* [ ] Les restrictions d'accès sont documentées.

Une attention particulière doit être portée aux fichiers contenant :

* secrets ;
* identifiants ;
* certificats ;
* clés privées ;
* fichiers de configuration ;
* sauvegardes.

---

## 8. Comptes et privilèges

* [ ] Apache n'est pas exécuté avec des privilèges administrateur inutiles.
* [ ] L'utilisateur du service est identifié.
* [ ] Les permissions des fichiers publiés sont maîtrisées.
* [ ] Les permissions d'écriture sont limitées.
* [ ] Les répertoires nécessitant une écriture sont identifiés.
* [ ] Les privilèges supplémentaires sont justifiés.

---

## 9. Journalisation

* [ ] Les journaux d'accès sont disponibles.
* [ ] Les journaux d'erreurs sont disponibles.
* [ ] Les journaux sont correctement protégés.
* [ ] La rotation des journaux est fonctionnelle.
* [ ] L'espace disque occupé par les journaux est surveillé.
* [ ] Les événements importants peuvent être investigués.

Emplacements courants :

```text
/var/log/apache2/access.log
/var/log/apache2/error.log
```

La configuration réelle du système doit être vérifiée avant de considérer ces chemins comme définitifs.

---

## 10. Mises à jour

* [ ] Apache est maintenu à jour.
* [ ] Les avis de sécurité sont suivis.
* [ ] Les vulnérabilités concernant Apache sont évaluées.
* [ ] Les dépendances système sont maintenues à jour.
* [ ] Les mises à jour importantes sont documentées.
* [ ] Le service est contrôlé après mise à jour.

```bash
apt list --upgradable
```

---

## 11. Supervision

La supervision doit permettre de détecter une dégradation ou une indisponibilité du service.

* [ ] Apache est supervisé par Zabbix lorsque nécessaire.
* [ ] La disponibilité HTTP/HTTPS est contrôlée.
* [ ] Les erreurs importantes sont détectables.
* [ ] L'espace disque est surveillé.
* [ ] Les ressources système sont surveillées.
* [ ] Les alertes importantes ont été testées.

La supervision ne remplace pas l'analyse des journaux.

---

## 12. Protection et sauvegarde

Les fichiers de configuration Apache doivent être **protégés et sauvegardés**.

Les principaux emplacements à examiner sont notamment :

```text
/etc/apache2/
/etc/apache2/apache2.conf
/etc/apache2/ports.conf
/etc/apache2/sites-available/
/etc/apache2/sites-enabled/
/etc/apache2/mods-available/
/etc/apache2/mods-enabled/
```

Les certificats et clés privées utilisés par HTTPS doivent également être protégés et sauvegardés selon la stratégie définie pour le laboratoire.

---

## 13. Validation après modification

Après une modification :

```bash
apache2ctl configtest
```

Puis :

```bash
systemctl status apache2
```

Et, si nécessaire :

```bash
journalctl -u apache2 -b
```

La modification n'est considérée comme validée qu'après vérification :

* de la syntaxe ;
* du démarrage du service ;
* de l'accessibilité attendue ;
* de l'absence d'erreur significative dans les journaux.

---

## 14. Contrôle final

* [ ] Version connue.
* [ ] Modules justifiés.
* [ ] Ports justifiés.
* [ ] Virtual Hosts identifiés.
* [ ] HTTPS correctement configuré.
* [ ] Certificats valides.
* [ ] Protocoles faibles désactivés.
* [ ] Accès aux fichiers sensibles contrôlé.
* [ ] Permissions vérifiées.
* [ ] Comptes et privilèges maîtrisés.
* [ ] Journaux disponibles.
* [ ] Rotation des journaux fonctionnelle.
* [ ] Mises à jour appliquées.
* [ ] Supervision opérationnelle.
* [ ] Configuration sauvegardée.
* [ ] Certificats et clés protégés.
* [ ] Test de configuration effectué.
* [ ] Service fonctionnel après modification.

---

## 15. Résultat

| Contrôle                | Résultat                  |
| ----------------------- | ------------------------- |
| Installation et version | ☐ Conforme ☐ Non conforme |
| Configuration           | ☐ Conforme ☐ Non conforme |
| Modules                 | ☐ Conforme ☐ Non conforme |
| Surface d'attaque       | ☐ Conforme ☐ Non conforme |
| HTTP / HTTPS            | ☐ Conforme ☐ Non conforme |
| En-têtes HTTP           | ☐ Conforme ☐ Non conforme |
| Contrôle d'accès        | ☐ Conforme ☐ Non conforme |
| Comptes et privilèges   | ☐ Conforme ☐ Non conforme |
| Journalisation          | ☐ Conforme ☐ Non conforme |
| Mises à jour            | ☐ Conforme ☐ Non conforme |
| Supervision             | ☐ Conforme ☐ Non conforme |
| Protection / sauvegarde | ☐ Conforme ☐ Non conforme |
| Validation finale       | ☐ Conforme ☐ Non conforme |

Toute non-conformité doit être documentée et faire l'objet d'une correction, d'une mesure compensatoire ou d'une justification.

---

## 16. Conclusion

Cette checklist constitue le contrôle final du durcissement d'Apache HTTP Server.

Elle vérifie simultanément la configuration du serveur Web, son exposition réseau, HTTPS, les contrôles d'accès, la journalisation, les mises à jour, la supervision et la protection des configurations.

Apache ne doit donc pas être considéré isolément : sa sécurité dépend également du système Ubuntu sous-jacent, de PHP et, lorsqu'il publie GLPI, de l'application et de sa base de données.
