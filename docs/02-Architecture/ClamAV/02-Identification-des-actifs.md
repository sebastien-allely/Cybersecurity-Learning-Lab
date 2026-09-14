# 02 - Identification des actifs

| Élément | Valeur |
| **Nom du document** | `02-Identification-des-actifs.md` |
| **Technologie** | ClamAV |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les actifs, répertoires et composants concernés par l'utilisation de ClamAV dans le laboratoire. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Actifs concernés

ClamAV est principalement destiné aux systèmes Linux du laboratoire sur lesquels une analyse antivirus apporte une valeur supplémentaire.

Les analyses doivent être définies en fonction :

* du rôle du système ;
* des données présentes ;
* des services exécutés ;
* du niveau de risque ;
* du coût en ressources de l'analyse.

---

# Répertoires concernés

Le laboratoire utilise notamment ClamAV pour analyser des répertoires contenant des fichiers susceptibles d'être déposés ou manipulés par des utilisateurs ou des services.

Le script développé dans le laboratoire prévoit notamment l'analyse de :

```text
/var/www
/home
```

Cette sélection doit être adaptée lorsque l'architecture évolue.

---

# Composants

Les composants principaux sont :

* moteur ClamAV ;
* base de signatures ;
* processus de mise à jour des signatures ;
* outil d'analyse ;
* scripts d'automatisation ;
* mécanisme de quarantaine lorsque celui-ci est utilisé.

---

# Résultats d'analyse

Les résultats doivent permettre de distinguer :

* aucune menace détectée ;
* fichier détecté ;
* erreur d'analyse ;
* problème de mise à jour ;
* problème de permission.

Cette distinction est importante pour éviter de considérer une analyse interrompue comme une analyse propre.
