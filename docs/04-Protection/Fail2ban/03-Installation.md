# 03 - Installation


| Élément | Valeur |
| **Nom du document** | `03-Installation.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Protection |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |




---

# Objectif

Cette section décrit l'installation de Fail2ban sur les systèmes Linux du laboratoire.

L'objectif est d'obtenir une installation minimale, stable et reproductible avant toute phase de configuration.

La configuration détaillée des jails, des filtres personnalisés et de la supervision est décrite dans les chapitres suivants.

---

# Prérequis

Avant de commencer, vérifier les points suivants :

- système Debian ou Ubuntu à jour ;
- accès administrateur (`sudo`) ;
- accès Internet vers les dépôts officiels ;
- horloge système synchronisée (NTP).

---

# Installation

Mettre à jour les dépôts :

```bash
sudo apt update
```

Installer Fail2ban :

```bash
sudo apt install fail2ban
```

Vérifier que le service est actif :

```bash
sudo systemctl status fail2ban
```

Résultat attendu :

```text
Active: active (running)
```

---

# Activation au démarrage

Vérifier l'activation automatique :

```bash
sudo systemctl is-enabled fail2ban
```

Si nécessaire :

```bash
sudo systemctl enable fail2ban
```

---

# Vérification de la version

Contrôler la version installée :

```bash
fail2ban-client version
```

Exemple :

```text
1.1.x
```

---

# Vérification du fonctionnement

Contrôler l'état général :

```bash
sudo fail2ban-client status
```

Résultat attendu :

- le serveur Fail2ban est démarré ;
- aucune erreur de configuration n'est signalée.

À ce stade, aucune jail personnalisée n'est encore activée.

---

# Conclusion

L'installation de Fail2ban est maintenant terminée.

Les chapitres suivants décrivent la configuration des jails, la création des filtres personnalisés et leur intégration dans l'environnement du Cybersecurity-Learning-Lab.
