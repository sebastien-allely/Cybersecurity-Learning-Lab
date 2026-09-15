# 11 - Checklist de validation

| Élément                           | Valeur                                                                                                                 |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `11-Checklist-de-validation.md`                                                                                        |
| **Technologie**                   | Debian                                                                                                                 |
| **Catégorie**                     | Hardening                                                                                                              |
| **Objectif**                      | Vérifier de manière structurée qu'un système Debian respecte les mesures de durcissement définies dans le référentiel. |
| **Auteur**                        | Sébastien Allely                                                                                                       |
| **Version**                       | 1.0                                                                                                                    |
| **Date de dernière modification** | 02/08/2026                                                                                                             |

---

## 1. Objectif

Cette checklist permet de vérifier qu'un système Debian a correctement reçu les mesures de durcissement prévues.

Elle doit être utilisée après une installation, une modification importante ou une opération de durcissement.

Une case cochée signifie que le contrôle a été effectué et non simplement que la configuration est supposée correcte.

---

## 2. Identification du système

* [ ] Version Debian identifiée.
* [ ] Version du noyau identifiée.
* [ ] Nom d'hôte vérifié.
* [ ] Rôle du système documenté.
* [ ] Date du contrôle renseignée.

Commandes de référence :

```bash
cat /etc/os-release
uname -r
hostnamectl
```

---

## 3. Mises à jour

* [ ] Les dépôts configurés sont connus.
* [ ] Les informations des dépôts sont à jour.
* [ ] Les mises à jour disponibles ont été identifiées.
* [ ] Les mises à jour de sécurité pertinentes ont été appliquées.
* [ ] Les éventuels redémarrages nécessaires ont été réalisés.
* [ ] Le fonctionnement des services a été vérifié après mise à jour.

```bash
apt update
apt list --upgradable
```

---

## 4. Services

* [ ] Les services actifs sont connus.
* [ ] Chaque service actif possède une justification.
* [ ] Les services inutiles ont été supprimés ou désactivés.
* [ ] Aucun service inattendu n'est actif.
* [ ] Aucun service critique n'est en échec.

```bash
systemctl list-units --type=service --state=running
systemctl --failed
```

---

## 5. Surface réseau

* [ ] Les interfaces réseau sont connues.
* [ ] Les routes sont cohérentes avec l'architecture.
* [ ] Les ports en écoute sont connus.
* [ ] Chaque port ouvert possède une justification.
* [ ] Les services n'écoutent pas inutilement sur toutes les interfaces.
* [ ] L'exposition réseau est limitée au strict nécessaire.

```bash
ip address
ip route
ss -tulpen
```

---

## 6. Comptes et privilèges

* [ ] Les comptes locaux sont connus.
* [ ] Les comptes inutilisés sont désactivés ou supprimés lorsque nécessaire.
* [ ] Les comptes privilégiés sont identifiés.
* [ ] Les membres du groupe `sudo` sont connus.
* [ ] Les privilèges sont conformes au principe du moindre privilège.
* [ ] L'utilisation directe de `root` est limitée.

```bash
getent passwd
getent group sudo
```

---

## 7. SSH

Si SSH est utilisé :

* [ ] La configuration SSH est connue.
* [ ] Les utilisateurs autorisés sont maîtrisés.
* [ ] L'authentification par clé est privilégiée lorsque possible.
* [ ] L'authentification par mot de passe est désactivée lorsque le contexte le permet.
* [ ] L'accès direct de `root` est maîtrisé.
* [ ] L'exposition réseau du service SSH est limitée.
* [ ] La configuration a été validée avant rechargement.

```bash
sshd -t
systemctl status ssh
```

---

## 8. Permissions

* [ ] Les fichiers sensibles possèdent des permissions adaptées.
* [ ] `/etc/shadow` est correctement protégé.
* [ ] `/etc/gshadow` est correctement protégé.
* [ ] `/etc/sudoers` est correctement protégé.
* [ ] `/etc/sudoers.d/` est correctement protégé.
* [ ] Les clés privées sont protégées.
* [ ] Les fichiers de configuration critiques sont accessibles uniquement aux utilisateurs ou services nécessaires.

---

## 9. Journalisation

* [ ] `systemd-journald` fonctionne correctement.
* [ ] Les journaux sont accessibles.
* [ ] Les événements SSH sont disponibles lorsque SSH est utilisé.
* [ ] Les erreurs système peuvent être consultées.
* [ ] L'espace occupé par les journaux est maîtrisé.
* [ ] La conservation des journaux est cohérente avec les besoins du laboratoire.

```bash
journalctl --disk-usage
journalctl -p warning..alert
```

---

## 10. Intégrité

Lorsque le contrôle d'intégrité est déployé :

* [ ] Le mécanisme d'intégrité fonctionne.
* [ ] La base de référence existe.
* [ ] La base de référence est protégée.
* [ ] Les modifications légitimes sont documentées.
* [ ] Les différences inattendues sont investiguées.
* [ ] La référence n'est mise à jour qu'après validation.

---

## 11. Supervision Zabbix

* [ ] L'agent Zabbix 2 fonctionne.
* [ ] Le serveur Zabbix reçoit les données attendues.
* [ ] La disponibilité de l'agent est supervisée.
* [ ] L'utilisation CPU est supervisée.
* [ ] La mémoire est supervisée.
* [ ] L'espace disque est supervisé.
* [ ] Les services critiques sont supervisés.
* [ ] Les alertes importantes ont été testées.

La supervision doit permettre de détecter une dégradation ou une indisponibilité sans dépendre d'un contrôle manuel.

---

## 12. Configuration

* [ ] Les fichiers de configuration critiques sont identifiés.
* [ ] Les configurations ont été sauvegardées avant modification.
* [ ] Les fichiers sensibles sont protégés.
* [ ] Les modifications importantes sont documentées.
* [ ] Les configurations peuvent être restaurées.

---

## 13. Validation finale

* [ ] Aucun service critique n'est en échec.
* [ ] Aucun port inattendu n'est ouvert.
* [ ] Aucun événement critique non expliqué n'est présent dans les journaux.
* [ ] Le système reste administrable.
* [ ] Les services nécessaires fonctionnent.
* [ ] La supervision fonctionne.
* [ ] Les sauvegardes nécessaires sont disponibles.
* [ ] Les modifications sont documentées.

---

## 14. Résultat

| Contrôle          | Résultat                        |
| ----------------- | ------------------------------- |
| Identification    | ☐ Conforme ☐ Non conforme       |
| Mises à jour      | ☐ Conforme ☐ Non conforme       |
| Services          | ☐ Conforme ☐ Non conforme       |
| Réseau            | ☐ Conforme ☐ Non conforme       |
| Comptes           | ☐ Conforme ☐ Non conforme       |
| SSH               | ☐ Conforme ☐ Non conforme ☐ N/A |
| Permissions       | ☐ Conforme ☐ Non conforme       |
| Journalisation    | ☐ Conforme ☐ Non conforme       |
| Intégrité         | ☐ Conforme ☐ Non conforme ☐ N/A |
| Supervision       | ☐ Conforme ☐ Non conforme       |
| Configuration     | ☐ Conforme ☐ Non conforme       |
| Validation finale | ☐ Conforme ☐ Non conforme       |

Toute non-conformité doit être documentée et faire l'objet d'une action corrective ou d'une justification.

---

## 15. Conclusion

La checklist constitue le contrôle final du durcissement.

Elle ne remplace pas l'analyse des risques ni la documentation des décisions.

Elle permet de vérifier que les mesures définies ont effectivement été appliquées et que le système reste fonctionnel après leur mise en œuvre.
