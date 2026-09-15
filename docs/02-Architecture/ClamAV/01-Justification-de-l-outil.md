# 01 - Justification de l'outil

| Élément | Valeur |
| **Nom du document** | `01-Justification-de-l-outil.md` |
| **Technologie** | ClamAV |
| **Catégorie** | Architecture |
| **Objectif** | Justifier l'utilisation de ClamAV comme mécanisme d'analyse antivirus dans le laboratoire et définir son positionnement dans la stratégie de protection. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 03/08/2026 |

---

# Rôle de ClamAV dans le laboratoire

ClamAV est utilisé comme moteur d'analyse antivirus permettant de rechercher des fichiers correspondant à des signatures ou à des caractéristiques reconnues comme malveillantes.

Dans le laboratoire, son utilisation répond principalement à un objectif de :

* détection ;
* analyse ;
* identification de fichiers suspects ;
* protection de répertoires sélectionnés.

---

# Justification du choix

ClamAV présente plusieurs caractéristiques adaptées au laboratoire :

* disponibilité sur les systèmes Linux ;
* fonctionnement en ligne de commande ;
* possibilité d'automatiser les analyses ;
* mise à jour régulière des signatures ;
* intégration avec des scripts ;
* possibilité de définir des répertoires à analyser ;
* faible complexité d'intégration.

ClamAV constitue ainsi un composant pédagogique permettant d'étudier concrètement le fonctionnement d'un mécanisme antivirus sur Linux.

---

# Positionnement de sécurité

ClamAV ne doit pas être considéré comme un EDR ou comme un mécanisme de détection comportementale complet.

Il intervient principalement sur la **détection de fichiers malveillants connus ou détectables par son moteur**.

Il complète donc les autres mécanismes du laboratoire :

* contrôle des accès ;
* durcissement du système ;
* supervision Zabbix ;
* AIDE ;
* Fail2ban ;
* CrowdSec ;
* sauvegardes.

---

# Automatisation

Le laboratoire utilise également des scripts afin d'automatiser certaines opérations liées à ClamAV.

Les scripts doivent notamment permettre :

* de contrôler la présence du logiciel ;
* de vérifier sa configuration ;
* d'effectuer les analyses prévues ;
* de gérer les résultats ;
* de limiter les effets indésirables d'une analyse.

Les automatisations doivent rester idempotentes lorsque cela est pertinent.

---

# Principe retenu

ClamAV est donc considéré comme une **couche de détection antivirus complémentaire**, et non comme une solution de sécurité globale.
