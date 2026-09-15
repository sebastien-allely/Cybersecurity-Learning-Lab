# 03 - Analyse des risques

| Élément | Valeur |
| **Nom du document** | `03-Analyse-des-risques.md` |
| **Technologie** | ClamAV |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les risques auxquels ClamAV contribue à répondre ainsi que les limites et risques liés à son utilisation. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Risques traités

ClamAV contribue notamment à réduire :

* le risque de présence de fichiers malveillants connus ;
* le risque de propagation de fichiers infectés ;
* le risque de stockage involontaire d'un fichier malveillant ;
* le risque lié à l'échange de fichiers provenant de sources non maîtrisées.

---

# Risques non couverts

ClamAV ne permet pas de garantir la détection :

* d'un malware inconnu ;
* d'une attaque sans dépôt de fichier ;
* d'une compromission utilisant des outils légitimes ;
* d'une attaque réseau ;
* d'une exploitation directe d'une vulnérabilité ;
* d'un comportement malveillant ne reposant pas sur un fichier détectable.

---

# Risques liés à l'analyse

Une analyse antivirus peut également présenter ses propres contraintes :

* consommation CPU ;
* consommation mémoire ;
* augmentation des entrées/sorties disque ;
* durée importante sur de gros volumes ;
* faux positifs ;
* résultats incomplets en cas de permissions insuffisantes.

---

# Mesures de réduction

Ces risques sont réduits par :

* la sélection raisonnée des répertoires ;
* la limitation de la fréquence des analyses ;
* la surveillance des ressources ;
* la mise à jour des signatures ;
* la gestion contrôlée de la quarantaine ;
* la supervision ;
* la journalisation des résultats.

---

# Principe

ClamAV réduit un risque particulier mais ne doit jamais être considéré comme l'unique mécanisme de protection contre les logiciels malveillants.
