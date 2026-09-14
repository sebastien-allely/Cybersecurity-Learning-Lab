# 09 - Mises à jour et vulnérabilités

| Élément                           | Valeur                                                                                      |
| --------------------------------- | ------------------------------------------------------------------------------------------- |
| **Nom du document**               | `09-Mises-a-jour-et-vulnerabilites.md`                                                      |
| **Technologie**                   | Debian                                                                                      |
| **Catégorie**                     | Hardening                                                                                   |
| **Objectif**                      | Maintenir les systèmes Debian à jour et réduire leur exposition aux vulnérabilités connues. |
| **Auteur**                        | Sébastien Allely                                                                            |
| **Version**                       | 1.0                                                                                         |
| **Date de dernière modification** | 02/08/2026                                                                                  |

---

## 1. Objectif

Un système correctement configuré mais non maintenu peut rester vulnérable à des failles publiées après son déploiement.

La gestion des mises à jour constitue donc une composante permanente du maintien en condition de sécurité.

---

## 2. Identifier les mises à jour

La première étape consiste à actualiser les informations disponibles dans les dépôts :

```bash
apt update
```

Les paquets pouvant être mis à jour peuvent ensuite être identifiés :

```bash
apt list --upgradable
```

Ces commandes permettent de distinguer :

* l'existence d'une nouvelle version ;
* l'application effective de cette version.

---

## 3. Classification des mises à jour

Toutes les mises à jour ne présentent pas le même niveau d'urgence.

Une attention particulière doit être portée aux mises à jour corrigeant :

* une vulnérabilité exploitable à distance ;
* une élévation de privilèges ;
* une exécution de code ;
* une fuite d'informations ;
* une vulnérabilité affectant un service exposé.

La criticité réelle dépend également du rôle du système.

---

## 4. Sources de référence

Le suivi des vulnérabilités doit s'appuyer sur des sources fiables.

Les références pertinentes comprennent notamment :

* les avis de sécurité Debian ;
* les informations des mainteneurs des paquets ;
* les bases de vulnérabilités reconnues ;
* les recommandations ANSSI lorsque pertinentes ;
* les informations relatives aux composants applicatifs utilisés.

La présence d'une vulnérabilité dans une base ne signifie pas automatiquement que le système est exploitable.

Il faut vérifier :

* la version réellement installée ;
* la version corrigée ;
* le composant concerné ;
* l'exposition du service ;
* les mesures compensatoires.

---

## 5. Application des mises à jour

Les mises à jour doivent être appliquées selon le rôle et la criticité du système.

Une mise à jour peut être réalisée avec :

```bash
apt upgrade
```

Lorsque des changements plus importants sont nécessaires, la commande appropriée doit être choisie après analyse des conséquences.

L'administrateur doit notamment vérifier :

* les dépendances ;
* l'espace disque ;
* l'impact sur les services ;
* les éventuels redémarrages ;
* la possibilité de restauration.

---

## 6. Redémarrage nécessaire

Certaines mises à jour peuvent nécessiter un redémarrage du système ou d'un service.

Après une opération importante, il convient notamment de vérifier :

```bash
systemctl --failed
```

et :

```bash
uname -r
```

Le fonctionnement des services critiques doit également être vérifié.

---

## 7. Gestion des vulnérabilités

Une vulnérabilité doit être traitée selon son niveau de risque.

Une démarche possible est :

1. identifier la vulnérabilité ;
2. identifier les systèmes concernés ;
3. vérifier la version installée ;
4. déterminer l'exposition ;
5. identifier la correction disponible ;
6. appliquer la correction ;
7. vérifier le fonctionnement ;
8. documenter l'opération.

---

## 8. Cas où la correction immédiate est impossible

Une mise à jour peut parfois être temporairement impossible pour des raisons opérationnelles.

Dans ce cas, il faut rechercher des mesures compensatoires :

* désactivation du service ;
* restriction réseau ;
* limitation des utilisateurs ;
* filtrage des ports ;
* isolement du système ;
* surveillance renforcée.

Cette situation doit être documentée comme un risque résiduel et non considérée comme une résolution définitive.

---

## 9. Vérification après mise à jour

Après une mise à jour, il faut vérifier :

```bash
systemctl --failed
```

Les ports ouverts :

```bash
ss -tulpen
```

Les erreurs récentes :

```bash
journalctl -p err -b
```

Les services critiques doivent ensuite être testés fonctionnellement.

---

## 10. Traçabilité

Les mises à jour importantes doivent être traçables.

Il convient de conserver lorsque nécessaire :

* date de l'opération ;
* système concerné ;
* paquet ou composant ;
* raison de l'opération ;
* résultat ;
* éventuel redémarrage ;
* problème rencontré.

Cette traçabilité facilite notamment les investigations ultérieures.

---

## 11. Supervision

La supervision doit permettre d'identifier les situations nécessitant une intervention.

Dans le laboratoire, Zabbix peut notamment être utilisé pour surveiller :

* disponibilité du système ;
* espace disque ;
* état des services ;
* disponibilité de l'agent ;
* anomalies système.

La supervision ne remplace toutefois pas le suivi des avis de sécurité.

---

## 12. Conclusion

La gestion des vulnérabilités Debian est un processus continu.

Le principe retenu est :

**identifier → évaluer → corriger → vérifier → documenter.**

L'objectif n'est pas simplement d'installer toutes les mises à jour disponibles, mais de maintenir chaque système dans un état de sécurité cohérent avec son rôle et son niveau d'exposition.
