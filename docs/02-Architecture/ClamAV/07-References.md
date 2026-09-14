# 07 - Références

| Élément | Valeur |
| **Nom du document** | `07-References.md` |
| **Technologie** | ClamAV |
| **Catégorie** | Architecture |
| **Objectif** | Référencer les sources techniques et de cybersécurité utilisées pour concevoir l'intégration de ClamAV dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Documentation technique

Les principales références techniques sont :

* documentation officielle ClamAV ;
* documentation de la distribution Linux utilisée ;
* documentation des mécanismes de mise à jour des signatures ;
* documentation des outils d'analyse ClamAV.

---

# Référentiels de cybersécurité

La conception générale du laboratoire s'appuie notamment sur :

* ANSSI ;
* NIST Cybersecurity Framework ;
* MITRE ATT&CK ;
* OWASP lorsque les fichiers analysés appartiennent à des applications web.

Ces référentiels permettent de replacer l'utilisation de ClamAV dans une démarche globale de réduction du risque.

---

# Références internes

Les scripts d'automatisation sont conservés dans :

```text
automation/bash/
```

Les éventuels éléments de supervision sont intégrés à :

```text
zabbix/
```

Les autres mécanismes de protection du laboratoire doivent être considérés conjointement à ClamAV.

---

# Maintenance des références

Les références doivent être réévaluées lors :

* d'une mise à jour majeure de ClamAV ;
* d'un changement de distribution ;
* d'une modification du mécanisme de mise à jour ;
* d'une évolution du script d'analyse ;
* d'une modification de l'architecture du laboratoire.

La documentation doit rester alignée avec la mise en œuvre réellement présente dans le laboratoire.
