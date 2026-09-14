# 07 - Mises à jour et gestion des vulnérabilités


| Élément | Valeur |
| **Nom du document** | `07-Mises-a-jour-et-gestion-des-vulnerabilites.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le maintien en condition de sécurité (MCS) garantit qu'Active Directory reste protégé face à l'évolution des vulnérabilités affectant Windows Server et les services d'annuaire.

---

# 2. Actifs concernés

Les mesures décrites concernent notamment :

- Windows Server ;
- Active Directory Domain Services ;
- DNS ;
- Kerberos ;
- LDAP ;
- stratégies de groupe (GPO) ;
- composants de sécurité Windows.

---

# 3. Risques identifiés

Les principaux risques sont :

- exploitation d'une vulnérabilité connue ;
- absence de correctifs de sécurité ;
- incompatibilité après une mise à jour ;
- régression fonctionnelle ;
- dette technique.

---

# 4. Décisions retenues

Le référentiel recommande :

- maintenir Windows Server dans une version supportée ;
- appliquer les mises à jour de sécurité selon leur criticité ;
- tester les mises à jour sur un environnement de validation lorsque cela est possible ;
- documenter chaque opération de maintenance ;
- vérifier le bon fonctionnement des services AD01 après chaque mise à jour.

---

# 5. Vérification

Une revue régulière doit contrôler :

- le niveau de correctifs du système ;
- les versions des composants AD01 ;
- les mises à jour en attente ;
- les journaux d'installation.

---

# 6. Supervision

Les événements suivants doivent être surveillés :

- échec d'installation d'une mise à jour ;
- redémarrage anormal du contrôleur de domaine ;
- indisponibilité des services AD01 après maintenance ;
- vulnérabilité critique publiée concernant Windows Server.

---

# 7. Dépendances avec les autres référentiels

## Dépendances techniques

- Windows Server
- DNS

## Dépendances fonctionnelles

- GLPI01
- ZABBIX01

## Dépendances de sécurité

- Sauvegardes
- Journalisation
- Supervision

---

# 8. Conclusion

Le maintien à jour constitue l'un des moyens les plus efficaces de réduire la surface d'attaque d'Active Directory.

---

# Références

## Référentiels

- ANSSI – Recommandations relatives à Active Directory.
- Microsoft Security Baselines.

## Documentation officielle

- Microsoft Learn.

## Guides techniques

- SOCLE – Stéphane Robert (pour les principes généraux de maintien en condition de sécurité, à vérifier avant chaque mise à jour du référentiel).
