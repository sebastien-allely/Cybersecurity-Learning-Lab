# 02 - Réduction de la surface d'attaque


| Élément | Valeur |
| **Nom du document** | `02-Reduction-de-la-surface-d-attaque.md` |
| **Technologie** | Proxmox VE |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La réduction de la surface d'attaque constitue la première mesure de durcissement d'un système.

Avant d'ajouter des mécanismes de sécurité, il est préférable de supprimer les éléments inutiles susceptibles d'être exploités par un attaquant.

Chaque service, interface ou fonctionnalité supplémentaire représente un point d'entrée potentiel.

---

# 2. Risques traités

Les mesures présentées dans ce document permettent notamment de réduire les risques suivants :

- compromission d'un service inutile ;
- exploitation d'une vulnérabilité sur un composant non utilisé ;
- augmentation de la surface d'exposition ;
- complexification de l'administration ;
- augmentation de la dette technique.

---

# 3. Principes retenus

Les décisions de durcissement reposent sur quatre principes.

## Ne conserver que le nécessaire

Tout composant inutile doit être supprimé ou désactivé.

Une fonctionnalité non utilisée ne doit pas rester active uniquement parce qu'elle est installée par défaut.

---

## Réduire les services exposés

Les interfaces d'administration doivent être limitées aux seuls utilisateurs autorisés.

Les services accessibles depuis le réseau doivent être strictement justifiés.

---

## Limiter les dépendances

Chaque logiciel supplémentaire augmente :

- la complexité ;
- le nombre de mises à jour ;
- les vulnérabilités potentielles.

Le référentiel privilégie donc les mécanismes natifs lorsqu'ils répondent au besoin.

---

## Conserver un système simple

Un système simple est :

- plus facile à maintenir ;
- plus facile à superviser ;
- plus facile à auditer.

La simplicité constitue un facteur de sécurité.

---

# 4. Mesures retenues

## Interfaces d'administration

### Objectif

Limiter les accès administratifs aux seuls réseaux autorisés.

### Justification

L'interface Web Proxmox et l'API REST permettent une administration complète de l'hyperviseur.

Une exposition non maîtrisée augmente fortement le risque de compromission.

### Vérification

- Vérifier les interfaces réseau exposées.
- Vérifier les règles de filtrage.
- Vérifier l'absence d'exposition Internet non justifiée.

---

## Services système

### Objectif

Conserver uniquement les services nécessaires au fonctionnement de Proxmox VE.

### Justification

Chaque service actif représente un point d'entrée potentiel.

Les services inutilisés doivent être supprimés ou désactivés après analyse de leur impact.

### Vérification

Lister régulièrement les services actifs :

```bash
systemctl list-units --type=service
```

Toute évolution doit être justifiée.

---

## Paquets installés

### Objectif

Limiter le nombre de logiciels installés.

### Justification

Chaque paquet supplémentaire augmente :

- la surface d'attaque ;
- le nombre de CVE potentielles ;
- les besoins de maintenance.

### Vérification

Les logiciels installés doivent être connus, documentés et justifiés.

---

## Comptes administrateurs

### Objectif

Limiter le nombre de comptes disposant de privilèges élevés.

### Justification

Chaque compte privilégié constitue une cible potentielle.

Le principe du moindre privilège est appliqué systématiquement.

---

# 5. Critères de décision

Avant d'ajouter ou de conserver un composant, les questions suivantes doivent être posées :

- Est-il indispensable au fonctionnement de l'infrastructure ?
- Quel actif protège-t-il ou expose-t-il ?
- Quels risques introduit-il ?
- Existe-t-il une alternative native ?
- Peut-il être supervisé ?
- Peut-il être maintenu dans le temps ?
- Sa suppression aurait-elle un impact opérationnel ?

Si ces questions ne peuvent être clairement justifiées, le composant ne doit pas être conservé.

---

# 6. Vérification

La réduction de la surface d'attaque doit être revue régulièrement.

Les contrôles portent notamment sur :

- les services actifs ;
- les ports ouverts ;
- les interfaces exposées ;
- les comptes administrateurs ;
- les paquets installés ;
- les règles de pare-feu.

Toute modification doit être documentée.

---

# 7. Supervision

Plusieurs éléments peuvent être intégrés à la supervision ZABBIX01 :

- disponibilité des services critiques ;
- apparition d'un nouveau service ;
- modification des ports exposés (si un mécanisme de contrôle est mis en place) ;
- état du pare-feu Proxmox ;
- disponibilité de l'agent ZABBIX01.

L'objectif n'est pas de superviser tous les changements, mais de détecter ceux qui modifient significativement la surface d'attaque.

---

# Conclusion

La réduction de la surface d'attaque constitue le fondement du durcissement.

Avant de renforcer un système, il convient d'en limiter l'exposition. Cette démarche réduit les risques, simplifie l'administration et diminue durablement la dette technique.

---

# Références

## Référentiels

- ANSSI – Guide d'administration sécurisée.
- NIST Cybersecurity Framework.

## Documentation officielle

- Documentation officielle Proxmox VE.
- Documentation Debian.
- Documentation systemd.

## Guides techniques

- SOCLE – Stéphane Robert (bonnes pratiques de réduction de la surface d'attaque sous Linux).
