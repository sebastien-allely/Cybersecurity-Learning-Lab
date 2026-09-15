# 08 - Supervision


| Élément | Valeur |
| **Nom du document** | `08-Supervision.md` |
| **Technologie** | Debian |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Mise en œuvre dans le laboratoire

Le laboratoire utilise **ZABBIX01 Agent 2** pour superviser les machines Linux.

Les éléments spécifiques sont organisés dans :

```text
/etc/zabbix/zabbix_agent2.d/
```

Les UserParameters permettent notamment de superviser des éléments qui ne sont pas couverts directement par les métriques natives.

---

# Ressources système

Les métriques principales à surveiller sont :

- utilisation CPU ;
- mémoire disponible ;
- espace disque ;
- inode ;
- charge système ;
- température matérielle lorsqu'elle est disponible ;
- erreurs disque ;
- état SMART lorsqu'il est applicable.

---

# Services

Identifier les services en échec :

```bash
systemctl --failed
```

Lister les services actifs :

```bash
systemctl list-units --type=service --state=running
```

---

# Réseau

Surveiller notamment :

```bash
ss -lntup
```

Le résultat doit correspondre aux services réellement nécessaires.

Toute apparition inattendue d'un port en écoute doit faire l'objet d'une analyse.

---

# Intégrité

AIDE peut être utilisé pour surveiller les fichiers critiques.

Les fichiers particulièrement importants comprennent :

- `/etc/passwd` ;
- `/etc/shadow` ;
- `/etc/group` ;
- `/etc/sudoers` ;
- `/etc/sudoers.d/` ;
- `/etc/ssh/` ;
- `/etc/systemd/`.

---

# Sécurité

Selon les composants installés, le laboratoire peut également superviser :

- CrowdSec ;
- Fail2ban ;
- ClamAV ;
- AIDE ;
- SSH ;
- journaux d'authentification.

---

# Conclusion

La supervision transforme les mesures de sécurité statiques en contrôles continus.

Un système durci mais non supervisé peut progressivement dériver de son état sécurisé sans que l'administrateur ne s'en aperçoive.
