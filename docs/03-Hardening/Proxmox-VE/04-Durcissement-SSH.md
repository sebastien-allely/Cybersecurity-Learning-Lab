# 04 - Durcissement SSH


| Élément | Valeur |
| **Nom du document** | `04-Durcissement-SSH.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


grep permitrootlogin
```

---

## Limiter les utilisateurs autorisés

### Objectif

Réduire le nombre de comptes pouvant accéder au serveur.

### Risque traité

Utilisation abusive d'un compte disposant d'un accès SSH.

### Justification

Plus le nombre de comptes autorisés est faible, plus la surface d'attaque est réduite.

---

## Limiter l'exposition réseau

### Objectif

Restreindre les hôtes pouvant initier une connexion SSH.

### Risque traité

Attaques provenant de réseaux non autorisés.

### Justification

L'administration SSH doit être réservée aux réseaux d'administration.

Cette restriction peut être mise en œuvre au niveau du pare-feu ou du routage selon l'architecture retenue.

---

## Journaliser les événements

### Objectif

Permettre la détection des tentatives d'attaque et faciliter les investigations.

### Risque traité

Absence de visibilité sur les accès.

### Justification

Une mesure de sécurité qui ne produit aucun événement exploitable est difficilement supervisable.

Les journaux doivent permettre d'identifier notamment :

- les connexions réussies ;
- les échecs d'authentification ;
- les tentatives répétées ;
- les élévations de privilèges.

---

# 6. Vérification

Le durcissement SSH doit être vérifié régulièrement.

Les contrôles portent notamment sur :

- les paramètres effectifs d'OpenSSH ;
- les comptes autorisés ;
- les méthodes d'authentification ;
- les journaux système ;
- les règles de filtrage réseau.

---

# 7. Supervision

Les événements suivants présentent une valeur opérationnelle élevée :

- indisponibilité du service SSH ;
- échecs d'authentification dépassant un seuil défini ;
- bannissements Fail2ban ;
- modification du fichier de configuration SSH ;
- redémarrage inattendu du service.

Les seuils d'alerte doivent être définis de manière à limiter les faux positifs.

---

# 8. Conclusion

Le durcissement SSH ne consiste pas à appliquer systématiquement une liste de paramètres.

Il consiste à concevoir un accès d'administration répondant aux besoins opérationnels tout en réduisant les risques identifiés.

Chaque mesure doit être justifiée, vérifiée et supervisée afin de garantir son efficacité dans le temps.

---

# Références

## Référentiels

- ANSSI – Recommandations relatives à l'administration sécurisée des systèmes.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation OpenSSH.
- Documentation Debian.
- Documentation Proxmox VE.

## Guides techniques

- SOCLE – Stéphane Robert (durcissement SSH sous Linux).
