# 07 - Journalisation et supervision

| Élément                           | Valeur                                                                                                                   |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `07-Journalisation-et-supervision.md`                                                                                    |
| **Technologie**                   | Debian                                                                                                                   |
| **Catégorie**                     | Hardening                                                                                                                |
| **Objectif**                      | Renforcer la capacité de détection et d'investigation grâce à la journalisation et à la supervision des systèmes Debian. |
| **Auteur**                        | Sébastien Allely                                                                                                         |
| **Version**                       | 1.0                                                                                                                      |
| **Date de dernière modification** | 02/08/2026                                                                                                               |

---

## 1. Objectif

La journalisation et la supervision complètent les mesures préventives de durcissement.

Un système peut être correctement configuré et néanmoins être compromis à la suite :

* d'une vulnérabilité inconnue ;
* d'un identifiant compromis ;
* d'une erreur de configuration ;
* d'une attaque réussie ;
* d'une compromission d'un composant dépendant.

L'objectif est donc de disposer d'informations permettant de détecter et d'analyser ces événements.

---

## 2. Journalisation système

Debian s'appuie notamment sur `systemd-journald` pour la collecte des événements système.

La consultation des journaux peut être effectuée avec :

```bash
journalctl
```

Les événements récents peuvent être consultés avec :

```bash
journalctl -n 100
```

Les événements du démarrage courant :

```bash
journalctl -b
```

Les événements associés à un service :

```bash
journalctl -u <service>
```

---

## 3. Événements importants

Les événements particulièrement intéressants pour la sécurité comprennent notamment :

* démarrage et arrêt du système ;
* démarrage et arrêt des services ;
* connexions SSH ;
* échecs d'authentification ;
* élévations de privilèges ;
* modifications de configuration ;
* erreurs système ;
* changements d'état des mécanismes de sécurité.

Les journaux doivent être suffisamment précis pour permettre de reconstruire une séquence d'événements.

---

## 4. Recherche d'événements anormaux

Les événements importants peuvent être recherchés par niveau de priorité.

```bash
journalctl -p warning..alert
```

Les erreurs du démarrage courant :

```bash
journalctl -b -p err
```

Les événements SSH peuvent être recherchés selon le service de journalisation utilisé :

```bash
journalctl -u ssh
```

L'analyse doit tenir compte du rôle du système et des services réellement installés.

---

## 5. Conservation des journaux

La conservation des journaux doit permettre une investigation suffisamment longue tout en tenant compte de l'espace disque disponible.

Un système de journalisation mal dimensionné peut provoquer un remplissage du système de fichiers.

L'espace disponible doit donc être surveillé :

```bash
df -h
```

L'état et l'utilisation du journal peuvent être examinés avec :

```bash
journalctl --disk-usage
```

---

## 6. Supervision

La supervision permet de détecter les anomalies qui ne sont pas nécessairement visibles dans une consultation manuelle des journaux.

Dans le laboratoire, Zabbix constitue le mécanisme principal de supervision.

Les éléments suivants peuvent notamment être surveillés :

* disponibilité du système ;
* disponibilité de l'agent ;
* utilisation CPU ;
* mémoire disponible ;
* espace disque ;
* charge système ;
* état des services ;
* erreurs ;
* événements liés aux mécanismes de sécurité.

---

## 7. Cohérence entre journalisation et supervision

La supervision ne doit pas être considérée comme un remplacement des journaux.

Les deux mécanismes répondent à des objectifs différents :

| Mécanisme      | Fonction                                              |
| -------------- | ----------------------------------------------------- |
| Journalisation | Fournir le détail des événements                      |
| Supervision    | Détecter rapidement une anomalie                      |
| Alerting       | Signaler une situation nécessitant une action         |
| Investigation  | Exploiter les événements pour comprendre la situation |

Une alerte Zabbix doit donc pouvoir conduire l'administrateur vers les informations nécessaires à son diagnostic.

---

## 8. Surveillance des services

Les services critiques doivent faire l'objet d'une surveillance adaptée.

L'état général des services peut être vérifié avec :

```bash
systemctl --failed
```

Pour un service précis :

```bash
systemctl status <service>
```

Lorsqu'un service critique devient indisponible, l'événement doit être détecté suffisamment rapidement pour permettre une intervention.

---

## 9. Protection des journaux

Les journaux doivent être protégés contre :

* la modification non autorisée ;
* la suppression ;
* la saturation du stockage ;
* l'accès non justifié.

Dans le contexte d'une investigation, l'intégrité et la disponibilité des journaux sont particulièrement importantes.

Lorsque le niveau de risque le justifie, une conservation sur un système distinct peut être envisagée.

---

## 10. Exploitation en cas d'incident

Les journaux constituent une source importante lors d'une réponse à incident.

Ils peuvent notamment permettre de rechercher :

* la première activité suspecte ;
* les connexions ;
* les commandes ou actions privilégiées lorsqu'elles sont journalisées ;
* les changements de configuration ;
* les arrêts ou démarrages de services ;
* les modifications intervenues avant ou après l'événement.

La synchronisation temporelle du système est donc indispensable à une analyse fiable.

---

## 11. Vérification

Les mécanismes de journalisation et de supervision doivent être testés périodiquement.

Il faut vérifier :

* qu'un événement attendu est effectivement journalisé ;
* que Zabbix collecte les métriques attendues ;
* qu'une panne de service génère l'alerte prévue ;
* que les journaux restent disponibles ;
* que l'espace disque ne risque pas d'être saturé.

Une supervision non testée ne doit pas être considérée comme fiable.

---

## 12. Conclusion

La journalisation fournit les éléments nécessaires à l'analyse tandis que la supervision permet une détection rapide.

Leur association permet de passer d'une approche uniquement préventive à une approche intégrant :

**prévention → détection → analyse → réaction → amélioration.**
