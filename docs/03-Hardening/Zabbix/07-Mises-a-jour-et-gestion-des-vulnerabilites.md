# 07 - Mises à jour et gestion des vulnérabilités


| Élément | Valeur |
| **Nom du document** | `07-Mises-a-jour-et-gestion-des-vulnerabilites.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Définir les mesures de gestion des mises à jour et des vulnérabilités de Zabbix. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Mise en œuvre dans le laboratoire

Le laboratoire :

- réalise un snapshot Proxmox avant les mises à jour majeures ;
- vérifie les notes de version ;
- teste les personnalisations après mise à jour ;
- vérifie les UserParameters.

---

# Vérification

Après chaque mise à jour :

- état des services ;
- fonctionnement des Templates ;
- fonctionnement des Triggers ;
- fonctionnement des UserParameters ;
- sauvegardes.

---

# Supervision

Superviser :

- versions installées ;
- erreurs après mise à jour ;
- disponibilité.

---

# Références

- Documentation ZABBIX01
- CVE
- ANSSI
- SOCLE Stéphane Robert
