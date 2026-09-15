# 01 - Introduction


| Élément | Valeur |
| **Nom du document** | `01-Introduction.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Protection |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |




## Objectif

Présenter Fail2ban, son rôle dans une stratégie de défense en profondeur et sa place dans l'architecture du Cybersecurity Learning Lab.

## Pourquoi Fail2ban ?

- Protection contre les attaques par force brute.
- Réduction du bruit généré par les attaques automatisées.
- Blocage dynamique des adresses IP malveillantes.
- Solution légère, mature et disponible dans les dépôts officiels Debian/Ubuntu.

## Cas d'utilisation

- SSH
- Proxmox VE
- Apache
- Nginx
- GLPI01
- Services web
- Tout service produisant des journaux exploitables.

## Limites

Fail2ban n'est pas :

- un antivirus ;
- un EDR ;
- un IDS ;
- un IPS ;
- un pare-feu à lui seul.

Il agit uniquement après analyse des journaux.

## Positionnement dans le Cybersecurity Learning Lab

Fail2ban constitue une première ligne de défense contre les attaques opportunistes.

Il complète :

- CrowdSec
- ClamAV
- AIDE
- ZABBIX01
- le durcissement du système

afin de mettre en œuvre une stratégie de défense multicouche.

## Référentiels

- ANSSI
- NIST
- OWASP
- MITRE ATT&CK
- SOCLE de Stéphane Robert
- IT-Connect (Florian Burnel)

## À retenir

Fail2ban ne remplace jamais un durcissement système ; il le complète.
