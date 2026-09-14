# 06 - Services et processus


| Élément | Valeur |
| **Nom du document** | `06-Services-et-processus.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## systemd

Debian utilise systemd comme système d'initialisation et gestionnaire de services dans les installations standards concernées.

Les services peuvent être administrés avec :

```bash
systemctl
```

---

## État des services

Lister les services actifs :

```bash
systemctl --type=service --state=running
```

Identifier les services en échec :

```bash
systemctl --failed
```

Vérifier un service :

```bash
systemctl status <service>
```

---

## Processus

Les processus peuvent être observés avec :

```bash
ps aux
```

ou :

```bash
top
```

Selon les outils installés, `htop` peut également être utilisé.

---

## Ports réseau

Les sockets en écoute peuvent être identifiés avec :

```bash
ss -lntup
```

Cette information permet de rapprocher les services actifs de leur exposition réseau.

---

## Principe d'architecture

Un service ne doit être considéré comme nécessaire que lorsqu'il correspond au rôle du système.

La réduction des services inutiles relève du hardening et est donc documentée séparément.

---

## Références

* Documentation Debian
* Documentation systemd
* Debian Administrator's Handbook
