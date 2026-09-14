# 04 - Système de fichiers


| Élément | Valeur |
| **Nom du document** | `04-Systeme-de-fichiers.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Configuration

Le répertoire `/etc` contient une grande partie de la configuration système.

Les fichiers critiques doivent être protégés et sauvegardés lorsque leur perte empêcherait la reconstruction ou le fonctionnement du système.

---

## Journaux

Les journaux se trouvent principalement dans :

```text
/var/log/
```

Sur les systèmes utilisant systemd, le journal centralisé peut également être consulté avec :

```bash
journalctl
```

---

## Espace disque

L'espace disponible peut être vérifié avec :

```bash
df -h
```

L'utilisation des inodes :

```bash
df -i
```

---

## Diagnostic

Une saturation du système de fichiers peut provoquer :

* des erreurs d'écriture ;
* des services défaillants ;
* des problèmes de journalisation ;
* des erreurs APT ;
* des interruptions de service.

La capacité disque constitue donc un élément à superviser.

---

## Références

* Documentation Debian
* Debian Administrator's Handbook
