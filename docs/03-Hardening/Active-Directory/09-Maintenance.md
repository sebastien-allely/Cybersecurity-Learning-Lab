# 09 - Maintenance

| Élément                           | Valeur                                                                                                                      |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `09-Maintenance.md`                                                                                                         |
| **Technologie**                   | Active Directory Domain Services                                                                                            |
| **Catégorie**                     | Hardening                                                                                                                   |
| **Objectif**                      | Définir les principes de maintenance nécessaires au maintien en condition opérationnelle et de sécurité d'Active Directory. |
| **Auteur**                        | Sébastien Allely                                                                                                            |
| **Version**                       | 1.0                                                                                                                         |
| **Date de dernière modification** | 21/09/2026                                                                                                                  |

---

# 1. Objectif

Le durcissement d'Active Directory n'est pas une action ponctuelle réalisée lors de l'installation du contrôleur de domaine.

La sécurité de l'annuaire doit être maintenue tout au long de son cycle de vie afin de conserver l'efficacité des mesures mises en place et de limiter l'apparition de nouvelles vulnérabilités.

La maintenance contribue directement au maintien en condition de sécurité (MCS) et au maintien en condition opérationnelle (MCO).

Elle doit permettre de conserver un environnement :

* à jour ;
* maîtrisé ;
* documenté ;
* supervisé ;
* restaurable.

---

# 2. Principes de maintenance

Le référentiel retient les principes suivants :

* effectuer les opérations de maintenance de manière planifiée ;
* limiter les modifications aux besoins identifiés ;
* documenter les changements importants ;
* vérifier les conséquences des modifications ;
* conserver une capacité de retour arrière lorsque cela est nécessaire ;
* contrôler le fonctionnement d'Active Directory après chaque opération importante ;
* maintenir la documentation à jour.

Une opération de maintenance ne doit pas introduire une modification de sécurité non maîtrisée.

---

# 3. Mises à jour

Les contrôleurs de domaine doivent bénéficier des mises à jour de sécurité applicables à Windows Server et aux composants Active Directory.

Les opérations de mise à jour doivent notamment prendre en compte :

* les correctifs de sécurité ;
* les mises à jour cumulatives Windows Server ;
* les vulnérabilités affectant les services d'annuaire ;
* les vulnérabilités affectant les services associés ;
* les dépendances avec DNS et les autres composants de l'infrastructure.

Avant une opération importante, l'administrateur doit vérifier que les sauvegardes nécessaires sont disponibles.

Après la mise à jour, le fonctionnement du contrôleur de domaine doit être contrôlé.

---

# 4. Vérification de l'état d'Active Directory

Les contrôles réguliers doivent permettre de détecter les anomalies affectant :

* les contrôleurs de domaine ;
* la réplication ;
* DNS ;
* les services Active Directory ;
* les événements système ;
* les comptes privilégiés ;
* les ressources critiques.

Exemples de commandes :

```powershell
dcdiag
```

```powershell
repadmin /replsummary
```

```powershell
Get-Service
```

Ces commandes permettent d'obtenir un état
