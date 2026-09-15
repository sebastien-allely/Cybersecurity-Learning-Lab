# 01 - Justification des décisions


| Élément | Valeur |
| **Nom du document** | `01-Justification-des-decisions.md` |
| **Technologie** | Zabbix |
| **Catégorie** | Hardening |
| **Objectif** | Définir les principes guidant les décisions de sécurité et de durcissement de Zabbix. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# Objectif

Présenter les principes de sécurité retenus pour sécuriser la plateforme de supervision ZABBIX01 tout en garantissant sa disponibilité et son exploitabilité.

---

# Définition

Le durcissement (Hardening) consiste à réduire la surface d'attaque d'un système en appliquant des mesures de sécurité adaptées à son contexte d'utilisation.

Pour une plateforme de supervision, l'objectif est double :

- protéger les informations collectées ;
- garantir la capacité de détecter un incident.

Une plateforme de supervision compromise peut masquer une attaque, supprimer des alertes ou fournir des informations sensibles sur l'ensemble du système d'information.

---

# Pourquoi durcir ZABBIX01 ?

ZABBIX01 centralise des informations critiques :

- état des serveurs ;
- services exécutés ;
- journaux ;
- métriques système ;
- événements de sécurité ;
- informations d'infrastructure.

Sa compromission peut permettre à un attaquant de :

- désactiver des alertes ;
- modifier les seuils de détection ;
- supprimer des historiques ;
- masquer une compromission en cours.

Le durcissement de ZABBIX01 contribue donc directement à la sécurité globale du laboratoire.

---

# Référentiel

Le présent référentiel s'appuie notamment sur :

- les recommandations de l'ANSSI ;
- le NIST Cybersecurity Framework ;
- la documentation officielle de ZABBIX01 ;
- le SOCLE de Stéphane Robert pour les mesures de sécurisation applicables au système Linux hôte lorsque celles-ci concernent la plateforme de supervision.

Les recommandations sont adaptées au contexte d'un laboratoire pédagogique.

---

# Décisions retenues

Le référentiel recommande notamment :

- appliquer le principe du moindre privilège ;
- limiter le nombre de comptes administrateurs ;
- protéger les fichiers de configuration ;
- maintenir ZABBIX01 et ses dépendances à jour ;
- sécuriser l'accès à l'interface Web ;
- journaliser les actions sensibles ;
- superviser les composants critiques de ZABBIX01 ;
- documenter toutes les personnalisations.

---

# Mise en œuvre dans le laboratoire

Le laboratoire applique ces principes de la manière suivante :

- utilisation de **ZABBIX01 Agent 2** sur les machines virtuelles Linux ;
- développement de **Templates** personnalisés adaptés aux technologies supervisées ;
- création de **UserParameters** spécifiques lorsque les métriques natives sont insuffisantes ;
- séparation des fichiers de configuration des UserParameters par technologie dans `/etc/zabbix/zabbix_agent2.d/` ;
- limitation des privilèges accordés au compte `zabbix` via des règles `sudo` ciblées ;
- supervision des sauvegardes Proxmox, de CrowdSec, des disques NVMe et d'autres composants critiques.

Chaque personnalisation est documentée afin d'en faciliter la maintenance et l'audit.

---

# Vérification

Le durcissement doit être vérifié régulièrement afin de s'assurer que :

- les recommandations restent appliquées ;
- les personnalisations sont toujours justifiées ;
- les évolutions de la plateforme n'introduisent pas de nouveaux risques.

---

# Supervision

La plateforme doit également superviser son propre fonctionnement.

Une attention particulière est portée à :

- la disponibilité du serveur ZABBIX01 ;
- la disponibilité de MariaDB ;
- la disponibilité d'Apache HTTP Server ;
- le fonctionnement de ZABBIX01 Agent 2 ;
- l'état des UserParameters ;
- les sauvegardes de la plateforme.

---

# Bonnes pratiques

Le référentiel recommande de :

- documenter chaque personnalisation ;
- privilégier les fonctionnalités natives avant de développer un UserParameter ;
- limiter les scripts exécutés avec des privilèges élevés ;
- conserver une architecture simple et maintenable ;
- réduire les faux positifs afin de préserver la qualité de la supervision.

---

# Dépendances

Le durcissement de ZABBIX01 dépend notamment des référentiels suivants :

- Apache HTTP Server ;
- MariaDB ;
- Ubuntu Server ;
- Proxmox VE ;
- CrowdSec ;
- ClamAV ;
- Fail2ban.

---

# Conclusion

Le durcissement de ZABBIX01 ne vise pas uniquement à protéger la plateforme elle-même. Il garantit également la fiabilité des informations de supervision sur lesquelles reposent les décisions d'exploitation et les investigations de sécurité.

---

# Références

- Documentation officielle ZABBIX01.
- Guide d'hygiène informatique – ANSSI.
- NIST Cybersecurity Framework.
- SOCLE de Stéphane Robert (mesures applicables au système Linux hôte).
