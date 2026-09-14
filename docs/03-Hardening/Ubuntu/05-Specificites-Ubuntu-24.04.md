# 04 - Spécificités Ubuntu 24.04


| Élément | Valeur |
| **Nom du document** | `04-Specificites-Ubuntu-24.04.md` |
| **Technologie** | Ubuntu |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Objectif

Documenter les éléments qui différencient Ubuntu 24.04 LTS d'un système Debian générique.

---

# AppArmor

Ubuntu 24.04 utilise AppArmor 4.0.1 comme mécanisme de confinement. :contentReference[oaicite:8]{index=8}

AppArmor doit être considéré comme un composant de sécurité du système et non comme un service facultatif.

---

# User namespaces

Ubuntu 24.04 renforce les restrictions concernant les user namespaces non privilégiés.

Cette protection est liée à AppArmor et au noyau Ubuntu. :contentReference[oaicite:9]{index=9}

Toute modification de cette protection doit être justifiée par un besoin applicatif clairement identifié.

---

# Mises à jour automatiques

Ubuntu active par défaut les mises à jour de sécurité via `unattended-upgrades`. :contentReference[oaicite:10]{index=10}

Cela constitue une différence opérationnelle importante à prendre en compte lors de la comparaison avec d'autres systèmes Linux.

---

# Pare-feu

Ubuntu recommande l'utilisation d'un pare-feu local.

`ufw` constitue l'outil de gestion simplifié proposé par Ubuntu. :contentReference[oaicite:11]{index=11}

Le choix de l'outil doit néanmoins rester cohérent avec l'architecture réseau du laboratoire.

---

# Noyau

Ubuntu fournit son propre noyau adapté à sa distribution.

La version du noyau doit être vérifiée avant toute procédure spécifique :

```bash
uname -r
```

Pour la VM GLPI01 actuellement documentée :

```text
6.8.0-136-generic
```

---

# Services et paquets

La configuration réellement installée doit toujours être vérifiée plutôt que déduite de l'installation standard.

Exemples :

```bash
systemctl list-units --type=service --state=running
```

et :

```bash
dpkg-query -W
```

---

# Applicabilité au laboratoire

Cette documentation s'applique principalement à la VM Ubuntu utilisée pour GLPI01.

Elle doit être complétée par les référentiels spécifiques des composants :

- Apache ;
- PHP ;
- MariaDB ;
- GLPI01 ;
- LDAP ;
- ZABBIX01 Agent 2 ;
- CrowdSec.

---

# Conclusion

Ubuntu 24.04 apporte plusieurs mécanismes de sécurité intégrés, notamment AppArmor et les protections associées aux user namespaces.

Ces mécanismes doivent être conservés autant que possible et intégrés à la stratégie globale de défense en profondeur du laboratoire.
