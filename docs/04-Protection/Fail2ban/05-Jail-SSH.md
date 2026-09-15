## Jail SSH



Le protocole SSH constitue le principal moyen d'administration des serveurs Linux du Cybersecurity Learning Lab.

Bien que ce service soit durci (authentification par clé, désactivation de l'authentification par mot de passe, interdiction de connexion directe de l'utilisateur `root`), il reste pertinent de le protéger avec Fail2ban.

Fail2ban ne remplace pas le durcissement de SSH. Les deux mécanismes sont complémentaires :

* le durcissement réduit la surface d'attaque ;
* Fail2ban détecte et bloque les tentatives répétées d'authentification.

### Configuration

```ini
[sshd]
enabled  = true
port     = ssh
backend  = systemd
maxretry = 3
findtime = 2d
bantime  = 1h
```

### Explication

La jail `sshd` hérite automatiquement des paramètres définis dans le bloc `[DEFAULT]`.

Seuls les paramètres spécifiques au service SSH sont renseignés dans cette section.

L'utilisation du backend `systemd` permet à Fail2ban d'analyser directement les événements produits par le service SSH via `systemd-journald`, sans dépendre de fichiers de journalisation.

> 🛡️ **Sécurité**
>
> La protection de SSH par Fail2ban ne dispense jamais de mettre en œuvre les mesures de durcissement du service (authentification par clés, désactivation des mots de passe, restriction des utilisateurs autorisés, etc.).

> 💡 **Bonne pratique**
>
> Éviter de redéfinir inutilement les paramètres déjà présents dans le bloc `[DEFAULT]`. Cela simplifie la maintenance et garantit une configuration homogène.

### Validation

Vérifier que la jail est chargée :

```bash
fail2ban-client status sshd
```

Afficher les paramètres appliqués :

```bash
fail2ban-client -d
```

Lister les adresses IP actuellement bannies :

```bash
fail2ban-client status sshd
```

### Test

Depuis une machine de test, effectuer plusieurs tentatives d'authentification volontairement incorrectes.

Après trois échecs dans la fenêtre définie par `findtime`, l'adresse IP doit être bannie pendant une heure.

Le bannissement peut être vérifié avec :

```bash
fail2ban-client status sshd
```

Il peut également être observé dans les journaux :

```bash
journalctl -u fail2ban -f
```

### Dépannage

Si la jail ne détecte aucune tentative d'authentification :

* vérifier que le service SSH est actif ;
* vérifier que `systemd-journald` est en fonctionnement ;
* contrôler les journaux SSH avec :

```bash
journalctl -u ssh
```

* vérifier la configuration de Fail2ban :

```bash
fail2ban-client -d
```
