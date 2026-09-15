# 08 - Mises à jour et gestion des vulnérabilités

| Élément                           | Valeur                                                                                      |
| --------------------------------- | ------------------------------------------------------------------------------------------- |
| **Nom du document**               | `08-Mises-a-jour-et-gestion-des-vulnerabilites.md`                                          |
| **Technologie**                   | Ubuntu                                                                                      |
| **Catégorie**                     | Hardening                                                                                   |
| **Objectif**                      | Maintenir les systèmes Ubuntu à jour et réduire leur exposition aux vulnérabilités connues. |
| **Auteur**                        | Sébastien Allely                                                                            |
| **Version**                       | 1.0                                                                                         |
| **Date de dernière modification** | 02/08/2026                                                                                  |

---

## 1. Objectif

Le durcissement d'un système n'est pas permanent.

De nouvelles vulnérabilités sont régulièrement découvertes dans :

* le noyau ;
* les bibliothèques ;
* les applications ;
* les services ;
* les composants installés.

La gestion des mises à jour constitue donc une activité permanente de maintien en condition de sécurité.

---

## 2. Identification des mises à jour

Actualiser les informations des dépôts :

```bash
sudo apt update
```

Lister les paquets pouvant être mis à jour :

```bash
apt list --upgradable
```

La présence d'une mise à jour doit être évaluée selon le rôle et l'exposition du système.

---

## 3. Sources de sécurité

Le suivi doit notamment s'appuyer sur :

* les avis de sécurité Ubuntu ;
* les informations des mainteneurs ;
* les bases de vulnérabilités reconnues ;
* les recommandations institutionnelles pertinentes ;
* les informations relatives aux applications utilisées.

Une vulnérabilité publiée doit être rapprochée de la version réellement installée.

---

## 4. Évaluation du risque

Pour chaque vulnérabilité importante, il convient d'identifier :

* le composant concerné ;
* la version installée ;
* la version corrigée ;
* l'exposition ;
* les possibilités d'exploitation ;
* les mesures compensatoires ;
* l'impact potentiel.

La criticité d'une vulnérabilité ne dépend donc pas uniquement de son score.

---

## 5. Application des mises à jour

Les mises à jour doivent être appliquées selon une procédure maîtrisée.

```bash
sudo apt upgrade
```

Avant une opération importante, il convient de vérifier :

* les sauvegardes ;
* l'espace disponible ;
* les dépendances ;
* les éventuels redémarrages ;
* l'impact sur les services.

---

## 6. Vérification après mise à jour

Après une mise à jour :

```bash
systemctl --failed
```

Puis :

```bash
journalctl -p err -b
```

Les services critiques doivent être testés.

L'état du noyau peut être vérifié avec :

```bash
uname -r
```

---

## 7. Redémarrage

Certaines mises à jour nécessitent un redémarrage.

Lorsqu'un redémarrage est nécessaire, il doit être planifié en fonction du rôle du système.

Après redémarrage, il faut vérifier :

* disponibilité du système ;
* services ;
* réseau ;
* supervision ;
* applications ;
* journaux.

---

## 8. Vulnérabilité non corrigée

Si un correctif ne peut pas être appliqué immédiatement, des mesures compensatoires peuvent être envisagées :

* désactivation d'un service ;
* restriction réseau ;
* filtrage ;
* limitation des utilisateurs ;
* isolement ;
* surveillance renforcée.

Ces mesures réduisent le risque mais ne remplacent pas la correction définitive.

---

## 9. Traçabilité

Les mises à jour importantes doivent être documentées.

La traçabilité peut comprendre :

* système concerné ;
* date ;
* composant ;
* vulnérabilité ;
* version avant correction ;
* version après correction ;
* résultat ;
* problème rencontré ;
* redémarrage éventuel.

---

## 10. Supervision

La supervision Zabbix peut contribuer à détecter les conséquences d'une mise à jour :

* service arrêté ;
* saturation ;
* espace disque insuffisant ;
* indisponibilité ;
* anomalie système.

Elle ne remplace cependant pas la veille de sécurité.

---

## 11. Principe

La gestion des vulnérabilités suit le cycle :

**identifier → évaluer → prioriser → corriger → vérifier → documenter.**

L'objectif est de maintenir le système dans un état cohérent avec son niveau de risque.
