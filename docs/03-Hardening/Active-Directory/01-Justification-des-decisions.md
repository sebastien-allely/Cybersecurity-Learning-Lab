# 01 - Justification des décisions


| Élément | Valeur |
| **Nom du document** | `01-Justification-des-decisions.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Définir les principes guidant les décisions de durcissement d'Active Directory. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Le durcissement d'Active Directory vise à protéger le référentiel d'identité du laboratoire contre les compromissions, les élévations de privilèges et les modifications non autorisées.

Les décisions présentées résultent directement de l'analyse des risques réalisée sur Active Directory.

---

# 2. Risques identifiés

Les principaux risques sont :

- compromission d'un compte privilégié ;
- élévation de privilèges ;
- modification des stratégies de groupe ;
- compromission de la base NTDS.dit ;
- compromission du contrôleur de domaine.

---

# 3. Principes de conception

Le référentiel repose sur :

- le principe du moindre privilège ;
- la séparation des rôles ;
- la défense en profondeur ;
- la traçabilité ;
- le maintien en condition de sécurité.

---

# 4. Décisions retenues

Le référentiel recommande notamment :

- limiter le nombre de Domain Admins ;
- administrer le domaine avec des comptes dédiés ;
- protéger les GPO ;
- sécuriser les sauvegardes ;
- superviser les événements critiques ;
- documenter toute modification importante.

---

# 5. Vérification

Une revue régulière doit vérifier :

- les groupes privilégiés ;
- les délégations ;
- les GPO ;
- les comptes de service.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Windows Server
- DNS

## Dépendances fonctionnelles

- GLPI01
- ZABBIX01

## Dépendances de sécurité

- Sauvegardes
- Journalisation
- Supervision

---

# 7. Conclusion

La sécurité du laboratoire dépend directement de la protection d'Active Directory. Son durcissement constitue une priorité.

---

# Références

- ANSSI – Active Directory.
- Microsoft Security Baselines.
- Microsoft Learn.
