# 06 - Justification des décisions

| Élément | Valeur |
| **Nom du document** | `06-Justification-des-decisions.md` |
| **Technologie** | ClamAV |
| **Catégorie** | Architecture |
| **Objectif** | Documenter les décisions retenues pour intégrer ClamAV au laboratoire de manière cohérente avec les autres mécanismes de sécurité. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Analyse ciblée

Le laboratoire ne cherche pas à analyser indistinctement l'intégralité des systèmes à chaque exécution.

Les répertoires analysés sont sélectionnés en fonction :

* du risque ;
* de leur contenu ;
* de leur exposition ;
* de la fréquence de modification ;
* du coût de l'analyse.

---

# Quarantaine

Lorsqu'une menace est détectée, l'action doit empêcher autant que possible une exécution ou une utilisation accidentelle du fichier.

La quarantaine permet de séparer le fichier détecté du reste du système tout en conservant la possibilité d'effectuer une analyse complémentaire.

---

# Automatisation

Le laboratoire privilégie les scripts reproductibles et idempotents.

Les scripts ClamAV doivent notamment :

* vérifier les prérequis ;
* éviter les modifications inutiles ;
* gérer les erreurs ;
* produire des résultats exploitables ;
* respecter les permissions du système.

---

# Protection des fichiers de configuration

Les fichiers de configuration doivent être **protégés et sauvegardés**.

Cette règle s'applique notamment aux configurations et scripts utilisés pour :

* les analyses ;
* la mise à jour ;
* la quarantaine ;
* la supervision.

---

# Supervision

La présence du logiciel ne constitue pas une preuve de protection effective.

La supervision doit permettre de vérifier :

* que les composants attendus fonctionnent ;
* que les signatures sont disponibles ;
* que les analyses peuvent être exécutées ;
* que les erreurs importantes sont visibles.

---

# Positionnement

ClamAV reste volontairement une couche de détection antivirus complémentaire.

Il ne remplace ni le durcissement, ni la supervision, ni les mécanismes d'intégrité, ni les dispositifs de détection et de réponse.
