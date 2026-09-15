# 04 - Surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Surface-d-attaque.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les principaux éléments constituant la surface d'attaque d'Active Directory. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La surface d'attaque regroupe l'ensemble des éléments accessibles susceptibles d'être exploités par un attaquant afin de compromettre Active Directory.

Son identification permet de justifier les décisions de durcissement.

---

# 2. Services exposés

Le contrôleur de domaine expose notamment :

- LDAP ;
- LDAPS (si configuré) ;
- Kerberos ;
- DNS ;
- SMB ;
- RPC ;
- WinRM (si activé) ;
- RDP (administration).

Chaque service exposé constitue un point d'entrée potentiel.

---

# 3. Interfaces d'administration

Les principales interfaces d'administration sont :

- Console Active Directory Users and Computers ;
- Group Policy Management Console ;
- DNS Manager ;
- PowerShell ;
- Windows Admin Center (si utilisé).

L'accès à ces interfaces doit être strictement réservé aux administrateurs autorisés.

---

# 4. Comptes sensibles

Les comptes suivants présentent une criticité élevée :

- Domain Admins ;
- Administrators ;
- comptes de service ;
- compte KRBTGT ;
- comptes de secours.

---

# 5. Données sensibles

Les principaux actifs exposés sont :

- NTDS.dit ;
- SYSVOL ;
- GPO ;
- objets Active Directory ;
- journaux de sécurité.

---

# 6. Conclusion

La réduction de la surface d'attaque d'Active Directory repose principalement sur la limitation des services exposés, la protection des comptes privilégiés et la maîtrise des interfaces d'administration.
