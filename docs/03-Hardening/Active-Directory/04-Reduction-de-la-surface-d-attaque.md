# 04 - Réduction de la surface d'attaque


| Élément | Valeur |
| **Nom du document** | `04-Reduction-de-la-surface-d-attaque.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Hardening |
| **Objectif** | Présenter et documenter les éléments nécessaires à la compréhension du sujet traité par ce document dans le référentiel Cybersecurity-Learning-Lab. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

La réduction de la surface d'attaque consiste à limiter les services, interfaces et fonctionnalités accessibles afin de diminuer les possibilités d'exploitation d'Active Directory.

---

# 2. Risques identifiés

Les principaux risques sont :

- exploitation d'un service inutile ;
- compromission via un protocole hérité ;
- accès distant non maîtrisé ;
- exécution de logiciels non autorisés ;
- augmentation de la dette technique.

---

# 3. Décisions retenues

Le référentiel recommande :

- n'installer que les rôles indispensables au contrôleur de domaine ;
- désactiver les services inutiles ;
- limiter l'usage de NTLM lorsque cela est compatible avec l'infrastructure ;
- restreindre les accès RDP aux administrateurs autorisés ;
- limiter l'utilisation de PowerShell à distance aux besoins d'administration ;
- supprimer les fonctionnalités obsolètes ou non utilisées.

---

# 4. Vérification

Une revue régulière doit contrôler :

- les rôles installés ;
- les services actifs ;
- les ports exposés ;
- les règles du pare-feu Windows ;
- les fonctionnalités Windows activées.

---

# 5. Supervision

Les événements suivants présentent une valeur opérationnelle :

- activation d'un nouveau rôle ;
- modification du pare-feu Windows ;
- ouverture d'un nouveau port ;
- démarrage d'un service inhabituel.

---

# 6. Dépendances avec les autres référentiels

## Dépendances techniques

- Windows Server
- DNS
- Kerberos

## Dépendances fonctionnelles

- GLPI01
- ZABBIX01

## Dépendances de sécurité

- Journalisation
- Supervision
- Sauvegardes

---

# 7. Conclusion

La réduction de la surface d'attaque limite les opportunités d'exploitation et participe directement à la résilience du contrôleur de domaine.

---

# Références

## Référentiels

- ANSSI – Recommandations de sécurisation d'Active Directory.
- Microsoft Security Baselines.

## Documentation officielle

- Microsoft Learn.
