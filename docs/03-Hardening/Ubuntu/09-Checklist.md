# 09 - Checklist

| Élément                           | Valeur                                                                                                               |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `09-Checklist.md`                                                                                                    |
| **Technologie**                   | Ubuntu                                                                                                               |
| **Catégorie**                     | Hardening                                                                                                            |
| **Objectif**                      | Vérifier que les mesures de durcissement Ubuntu ont été appliquées et que le système reste fonctionnel et supervisé. |
| **Auteur**                        | Sébastien Allely                                                                                                     |
| **Version**                       | 1.0                                                                                                                  |
| **Date de dernière modification** | 02/08/2026                                                                                                           |

---

## 1. Identification

* [ ] Version Ubuntu identifiée.
* [ ] Version du noyau identifiée.
* [ ] Nom d'hôte vérifié.
* [ ] Rôle du système documenté.
* [ ] Date du contrôle renseignée.

```bash
cat /etc/os-release
uname -r
hostnamectl
```

---

## 2. Mises à jour

* [ ] Les dépôts sont connus.
* [ ] Les informations des dépôts sont à jour.
* [ ] Les mises à jour disponibles ont été identifiées.
* [ ] Les mises à jour de sécurité pertinentes ont été appliquées.
* [ ] Les éventuels redémarrages ont été effectués.
* [ ] Les services ont été vérifiés après mise à jour.

---

## 3. Services

* [ ] Les services actifs sont connus.
* [ ] Chaque service actif est justifié.
* [ ] Les services inutiles sont désactivés ou supprimés lorsque possible.
* [ ] Aucun service inattendu n'est actif.
* [ ] Aucun service critique n'est en échec.

```bash
systemctl list-units --type=service --state=running
systemctl --failed
```

---

## 4. Surface réseau

* [ ] Les interfaces sont connues.
* [ ] Les routes sont cohérentes.
* [ ] Les ports ouverts sont connus.
* [ ] Chaque port possède une justification.
* [ ] L'exposition réseau est limitée.

```bash
ip address
ip route
ss -tulpen
```

---

## 5. Comptes et privilèges

* [ ] Les comptes locaux sont connus.
* [ ] Les comptes inutilisés sont traités.
* [ ] Les comptes privilégiés sont identifiés.
* [ ] Les membres de `sudo` sont justifiés.
* [ ] Le principe du moindre privilège est respecté.
* [ ] L'utilisation de `root` est limitée.

```bash
getent passwd
getent group sudo
```

---

## 6. AppArmor

* [ ] AppArmor est actif.
* [ ] Les profils chargés sont identifiés.
* [ ] Les profils des services critiques sont vérifiés.
* [ ] Les profils en mode `complain` sont justifiés.
* [ ] Les profils en mode `enforce` sont fonctionnels.
* [ ] Les événements AppArmor sont analysables.
* [ ] Les profils modifiés sont sauvegardés.

---

## 7. SSH

Si SSH est utilisé :

* [ ] La configuration est connue.
* [ ] Les utilisateurs autorisés sont maîtrisés.
* [ ] L'authentification est correctement configurée.
* [ ] L'accès direct `root` est maîtrisé.
* [ ] L'exposition réseau est limitée.
* [ ] La configuration a été validée.

```bash
sshd -t
systemctl status ssh
```

---

## 8. Protection des configurations

* [ ] Les fichiers de configuration critiques sont identifiés.
* [ ] Les configurations ont été sauvegardées avant modification.
* [ ] Les permissions sont adaptées.
* [ ] Les fichiers sensibles sont protégés.
* [ ] Les sauvegardes sont disponibles.

Les fichiers de configuration critiques doivent être **protégés et sauvegardés**.

---

## 9. Journalisation

* [ ] Les journaux système sont disponibles.
* [ ] Les erreurs peuvent être consultées.
* [ ] Les événements SSH sont disponibles lorsque nécessaire.
* [ ] L'espace occupé par les journaux est maîtrisé.
* [ ] Les événements importants peuvent être investigués.

```bash
journalctl -p warning..alert
journalctl --disk-usage
```

---

## 10. Supervision Zabbix

* [ ] Zabbix Agent 2 fonctionne.
* [ ] Le serveur Zabbix reçoit les données.
* [ ] La disponibilité de l'agent est supervisée.
* [ ] CPU supervisé.
* [ ] Mémoire supervisée.
* [ ] Espace disque supervisé.
* [ ] Services critiques supervisés.
* [ ] Les alertes importantes ont été testées.

Configuration principale à protéger :

```text
/etc/zabbix/zabbix_agent2.conf
/etc/zabbix/zabbix_agent2.d/
```

---

## 11. Intégrité

Lorsque le mécanisme est déployé :

* [ ] Le contrôle d'intégrité fonctionne.
* [ ] La référence existe.
* [ ] La référence est protégée.
* [ ] Les modifications légitimes sont documentées.
* [ ] Les différences inattendues sont investiguées.

---

## 12. Sauvegarde

* [ ] Les sauvegardes nécessaires existent.
* [ ] Les configurations critiques sont sauvegardées.
* [ ] Les sauvegardes sont protégées.
* [ ] Une restauration a été testée.
* [ ] Les éléments nécessaires à une restauration sont identifiés.

---

## 13. Validation finale

* [ ] Aucun service critique n'est en échec.
* [ ] Aucun port inattendu n'est ouvert.
* [ ] Aucun événement critique non expliqué n'est présent.
* [ ] Le système reste administrable.
* [ ] Les services nécessaires fonctionnent.
* [ ] AppArmor fonctionne.
* [ ] Zabbix Agent 2 fonctionne.
* [ ] Les sauvegardes sont disponibles.
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
| AppArmor          | ☐ Conforme ☐ Non conforme       |
| SSH               | ☐ Conforme ☐ Non conforme ☐ N/A |
| Journalisation    | ☐ Conforme ☐ Non conforme       |
| Intégrité         | ☐ Conforme ☐ Non conforme ☐ N/A |
| Supervision       | ☐ Conforme ☐ Non conforme       |
| Sauvegarde        | ☐ Conforme ☐ Non conforme       |
| Validation finale | ☐ Conforme ☐ Non conforme       |

Toute non-conformité doit être documentée et faire l'objet d'une action corrective ou d'une justification.

---

## 15. Conclusion

Cette checklist constitue le contrôle final du durcissement Ubuntu.

Elle permet de vérifier que les mesures définies dans le référentiel ont effectivement été appliquées et que le système reste opérationnel après leur mise en œuvre.
