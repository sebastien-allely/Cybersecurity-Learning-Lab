# Hardening Debian

| Élément                           | Valeur                                                                                                                       |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                                                  |
| **Technologie**                   | Debian                                                                                                                       |
| **Catégorie**                     | Hardening                                                                                                                    |
| **Objectif**                      | Présenter les principes et les mesures de durcissement appliqués au socle Debian utilisé dans le Cybersecurity-Learning-Lab. |
| **Auteur**                        | Sébastien Allely                                                                                                             |
| **Version**                       | 1.0                                                                                                                          |
| **Date de dernière modification** | 07/08/2026                                                                                                                   |

---

## 1. Objectif

Ce dossier décrit les mesures de durcissement applicables au système Debian utilisé comme socle de plusieurs composants du laboratoire.

Le hardening vise à réduire la surface d'attaque du système tout en conservant les fonctionnalités nécessaires à son rôle.

---

## 2. Positionnement

Debian constitue le socle système de plusieurs composants du laboratoire.

Les mesures présentées ici concernent donc le système d'exploitation lui-même.

Les mécanismes propres aux applications ou services hébergés sur Debian sont documentés dans leurs dossiers respectifs.

Cette séparation permet notamment de distinguer :

* le durcissement du système ;
* le durcissement des services ;
* la protection ;
* la supervision.

---

## 3. Principes

Le durcissement repose notamment sur :

* la réduction de la surface d'attaque ;
* la limitation des services actifs ;
* la sécurisation des accès d'administration ;
* la gestion des mises à jour ;
* la journalisation ;
* la supervision ;
* la protection des fichiers et configurations ;
* la sauvegarde ;
* la vérification régulière de la configuration.

---

## 4. Relation avec l'architecture

Les mesures de hardening sont appliquées en cohérence avec les décisions d'architecture documentées dans :

`docs/02-Architecture/Debian/`

Le hardening ne constitue donc pas une démarche indépendante : il met en œuvre les mesures de réduction des risques identifiées lors de la conception.

---

## 5. Validation

Toute modification de configuration doit être vérifiée avant son intégration au laboratoire.

La validation doit notamment porter sur :

* le fonctionnement du système ;
* les services nécessaires ;
* les accès d'administration ;
* la journalisation ;
* la supervision ;
* les mécanismes de sécurité associés.

---

## 6. Maintenance

Le durcissement doit être réévalué lors :

* des mises à jour importantes ;
* de l'ajout ou de la suppression d'un service ;
* de l'évolution de l'architecture ;
* de l'identification d'une nouvelle vulnérabilité ;
* de la modification des exigences de sécurité.
