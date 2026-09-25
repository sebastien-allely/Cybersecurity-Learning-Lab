# 12 - Checklist

| Élément                           | Valeur                                                                                                                                       |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `12-Checklist.md`                                                                                                                            |
| **Technologie**                   | Proxmox VE                                                                                                                                   |
| **Catégorie**                     | Hardening                                                                                                                                    |
| **Objectif**                      | Vérifier de manière structurée l'application des mesures de durcissement de Proxmox VE et la sécurité de l'infrastructure de virtualisation. |
| **Auteur**                        | Sébastien Allely                                                                                                                             |
| **Version**                       | 1.0                                                                                                                                          |
| **Date de dernière modification** | 21/09/2026                                                                                                                                   |

---

## 1. Objectif

Cette checklist permet de vérifier qu'un environnement Proxmox VE a correctement reçu les mesures de durcissement prévues.

Elle doit être utilisée après une installation, une modification importante, une opération de durcissement ou lors d'une revue de sécurité.

> **Utilisation pédagogique**
>
> Cette checklist constitue un support de contrôle destiné à l'apprenant.
> Les cases sont volontairement laissées non cochées et doivent être renseignées lors de la réalisation du contrôle.
>
> Une case cochée signifie que le contrôle a été effectivement réalisé et ne constitue pas, à elle seule, une preuve de conformité permanente.

---

## 2. Identification de l'infrastructure

* [ ] Les nœuds Proxmox VE concernés sont identifiés.
* [ ] Le rôle de chaque nœud est documenté.
* [ ] La version de Proxmox VE est connue.
* [ ] La version du noyau utilisée est connue.
* [ ] Les ressources matérielles des nœuds sont identifiées.
* [ ] Les machines virtuelles hébergées sont inventoriées.
* [ ] Les dépendances critiques de l'infrastructure sont documentées.
* [ ] Le périmètre d'administration de Proxmox VE est identifié.

Vérification de la version :

```bash
pveversion
uname -a
```

---

## 3. Gestion des comptes et des privilèges

* [ ] Les comptes administrateurs sont identifiés.
* [ ] Les comptes inutilisés sont supprimés ou désactivés.
* [ ] Les privilèges sont attribués selon le principe du moindre privilège.
* [ ] Les comptes personnels sont privilégiés par rapport aux comptes partagés lorsque cela est possible.
* [ ] Les comptes de service sont identifiés et justifiés.
* [ ] Les droits d'administration sont régulièrement revus.
* [ ] Les mécanismes d'authentification utilisés sont documentés.
* [ ] Les comptes disposant de privilèges élevés sont protégés de manière appropriée.

---

## 4. Accès SSH

* [ ] L'accès SSH est limité aux utilisateurs autorisés.
* [ ] L'authentification par clé est utilisée lorsque cela est possible.
* [ ] L'authentification par mot de passe est désactivée*
