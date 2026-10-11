# Documentation Fail2ban

| Élément | Valeur |
|---|---|
| **Nom du document** | `README.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Protection |
| **Objectif** | Présenter l'organisation des procédures Fail2ban et guider le lecteur vers le document adapté. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## Objectif

Cette section documente le rôle de Fail2ban, son installation, sa configuration, ses jails et les activités de maintenance associées. Fail2ban complète les autres mesures de sécurité ; il ne remplace ni le durcissement des services, ni le pare-feu, ni une supervision centralisée.

## Parcours documentaire

| Document | Objet |
|---|---|
| `01-Introduction.md` | Rôle, cas d'usage et limites |
| `02-Architecture.md` | Fonctionnement et composants |
| `03-Installation.md` | Installation sur les distributions prises en charge |
| `04-Configuration.md` | Principes et paramètres de configuration |
| `05-Jail-SSH.md` | Protection du service SSH |
| `06-Jail-Proxmox.md` | Exemple de protection de l'administration Proxmox VE |
| `07-Creation-filtres-personnalises.md` | Conception et test de filtres personnalisés |
| `08-Supervision-Zabbix.md` | Contrôles de service et supervision |
| `09-Maintenance.md` | Contrôles périodiques et mises à jour |
| `10-Cycle-de-vie.md` | Gestion des changements de bout en bout |
| `11-Désinstallation.md` | Retrait contrôlé du composant |

## Principes de mise en œuvre

- Documenter le risque ciblé et la raison de chaque jail.
- Préférer les filtres fournis par la distribution lorsqu'ils répondent au besoin.
- Tester les filtres sur des événements représentatifs, y compris des cas négatifs.
- Limiter les privilèges et conserver un accès d'administration de secours.
- Vérifier les journaux, le service, les jails et la supervision après un changement.
- Documenter les faux positifs, les limites et la procédure de retour arrière.

## Avertissement

Les noms de services, les chemins et les paramètres peuvent varier selon la distribution et sa version. Les procédures doivent être adaptées puis validées dans le laboratoire avant une utilisation sur un système important.

## Références

- [Fail2ban — Documentation](https://github.com/fail2ban/fail2ban/wiki)
- [Debian — Documentation](https://www.debian.org/doc/)
- [Ubuntu Server — Documentation](https://documentation.ubuntu.com/server/)
- [Zabbix — Documentation](https://www.zabbix.com/documentation/current/en/manual)
