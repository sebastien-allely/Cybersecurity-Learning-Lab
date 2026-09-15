# 02 - Identification des actifs


| Élément | Valeur |
| **Nom du document** | `02-Identification-des-actifs.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les composants Zabbix concernés par les mesures de sécurité. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Identifier les composants critiques de ZABBIX01 afin de justifier les décisions d'architecture et de sécurité.

---

# 2. Actifs métier

Les principaux actifs sont :

- modèles (Templates) ;
- hôtes ;
- groupes d'hôtes ;
- tableaux de bord ;
- cartes ;
- déclencheurs (Triggers) ;
- actions ;
- médias de notification.

---

# 3. Actifs techniques

Les principaux composants techniques sont :

- serveur ZABBIX01 ;
- base de données ;
- interface Web ;
- agent ZABBIX01 ;
- agent ZABBIX01 2 ;
- UserParameters ;
- API.

---

# 4. Actifs de sécurité

Les actifs critiques comprennent :

- comptes administrateurs ;
- rôles ;
- clés API ;
- fichiers de configuration ;
- historiques ;
- journaux.

---

# 5. Dépendances

## Dépendances techniques

- Apache
- MariaDB
- Ubuntu Server

## Dépendances fonctionnelles

- Proxmox VE
- Active Directory
- GLPI01
- Linux
- Windows

## Dépendances de sécurité

- CrowdSec
- Fail2ban
- ClamAV

---

# 6. Criticité

La perte de ZABBIX01 n'empêche pas directement le fonctionnement du laboratoire, mais entraîne une perte de visibilité susceptible de retarder fortement la détection d'un incident.

---

# 7. Conclusion

ZABBIX01 constitue un actif transverse dont la disponibilité conditionne la capacité de supervision du laboratoire.
