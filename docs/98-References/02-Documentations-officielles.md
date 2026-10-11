# Documentations officielles

| Élément | Valeur |
|---|---|
| **Nom du document** | `02-Documentations-officielles.md` |
| **Technologie** | Documentation éditeur et projets |
| **Catégorie** | Références |
| **Objectif** | Centraliser les portails officiels utiles à l'installation, la configuration, la sécurisation et la maintenance des composants. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## Objectif

Les documentations officielles sont la source prioritaire pour vérifier les paramètres disponibles, les prérequis, les procédures supportées, les changements de version et les limites connues d'un produit.

## Sources par domaine

| Domaine | Source officielle |
|---|---|
| Debian | [Debian Documentation](https://www.debian.org/doc/) |
| Ubuntu Server | [Ubuntu Server Documentation](https://documentation.ubuntu.com/server/) |
| Proxmox VE | [Proxmox VE Documentation](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/documentation) |
| Windows Server | [Microsoft Learn](https://learn.microsoft.com/windows-server/) |
| Active Directory | [Microsoft Learn — Active Directory Domain Services](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-domain-services) |
| Apache HTTP Server | [Apache HTTP Server Documentation](https://httpd.apache.org/docs/) |
| MariaDB | [MariaDB Documentation](https://mariadb.com/docs/server) |
| GLPI | [GLPI Documentation](https://glpi-user-documentation.readthedocs.io/) |
| Zabbix | [Zabbix Documentation](https://www.zabbix.com/documentation/current/en/manual) |
| Fail2ban | [Fail2ban project](https://github.com/fail2ban/fail2ban/wiki) |
| CrowdSec | [CrowdSec Documentation](https://docs.crowdsec.net/) |
| Docker | [Docker Documentation](https://docs.docker.com/) |
| OpenSSH | [OpenSSH Manual Pages](https://www.openssh.com/manual.html) |

## Méthode de consultation

1. Identifier la version effectivement installée ou visée.
2. Ouvrir la documentation correspondant à cette version lorsque plusieurs branches sont disponibles.
3. Vérifier les prérequis, les conséquences et les procédures de mise à niveau.
4. Tester la procédure dans un environnement contrôlé.
5. Citer dans le document technique la page précise qui justifie le paramètre ou la procédure.

Les liens de ce tableau sont des points d'entrée. Ils ne constituent pas, à eux seuls, la référence suffisante pour justifier une commande ou un réglage précis.

## Maintenance de la liste

Vérifier périodiquement les liens et actualiser les références lorsque le projet change de version majeure. Éviter de remplacer une référence versionnée par une documentation « current » sans vérifier que le contenu correspond au produit documenté.
