# 11 - Checklist


| Élément | Valeur |
| **Nom du document** | `11-Checklist.md` |
| **Technologie** | Debian |
| **Catégorie** | Architecture |
| **Objectif** | Vérifier que les principales mesures de durcissement Debian ont été appliquées et validées. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

## Système

* [ ] La distribution Debian est identifiée.
* [ ] La version Debian est documentée.
* [ ] Le rôle du système est identifié.
* [ ] Le socle Debian est distingué des applications hébergées.

---

## Installation

* [ ] Les sources d'installation sont identifiées.
* [ ] Les dépôts APT sont documentés.
* [ ] La configuration initiale est documentée.
* [ ] Les comptes administratifs sont identifiés.

---

## Réseau

* [ ] Le réseau du laboratoire est identifié.
* [ ] Les interfaces sont documentées.
* [ ] Le routage est documenté.
* [ ] La résolution DNS est documentée.
* [ ] Les services réseau sont identifiés.

---

## Services

* [ ] Les services nécessaires au rôle du système sont identifiés.
* [ ] Les services actifs sont supervisés lorsque nécessaire.
* [ ] Les services inutiles sont identifiés pour le hardening.

---

## Journalisation

* [ ] journald est disponible.
* [ ] Les journaux nécessaires sont identifiés.
* [ ] Les erreurs système peuvent être recherchées.
* [ ] La supervision complète la journalisation.

---

## Vulnérabilités

* [ ] Les mises à jour Debian sont suivies.
* [ ] Debian Security Tracker est identifié comme source.
* [ ] Les DSA sont pris en compte.
* [ ] Les CVE pertinentes sont évaluées.
* [ ] Les mises à jour critiques sont tracées.

---

## Sauvegardes

* [ ] Les configurations critiques sont identifiées.
* [ ] Les données critiques sont identifiées.
* [ ] Les sauvegardes sont réalisées.
* [ ] Les restaurations sont testées.

---

## Documentation

* [ ] L'en-tête documentaire est présent.
* [ ] La version du document est indiquée.
* [ ] Les références sont présentes.
* [ ] Les informations sensibles sont anonymisées.
* [ ] L'architecture actuelle est distinguée de l'architecture cible.
* [ ] Les mesures de hardening ne sont pas dupliquées ici.
