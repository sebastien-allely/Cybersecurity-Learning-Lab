# 06 - Protection et sauvegarde

| Élément                           | Valeur                                                                                                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Nom du document**               | `06-Protection-et-sauvegarde.md`                                                                                                                             |
| **Technologie**                   | Ubuntu                                                                                                                                                       |
| **Catégorie**                     | Hardening                                                                                                                                                    |
| **Objectif**                      | Définir les mesures de protection et de sauvegarde permettant de préserver la disponibilité, l'intégrité et la capacité de restauration des systèmes Ubuntu. |
| **Auteur**                        | Sébastien Allely                                                                                                                                             |
| **Version**                       | 1.0                                                                                                                                                          |
| **Date de dernière modification** | 02/08/2026                                                                                                                                                   |

---

## 1. Objectif

Le durcissement ne doit pas uniquement chercher à empêcher une compromission.

Il doit également permettre de limiter les conséquences d'une erreur, d'une corruption, d'une défaillance matérielle ou d'un incident de sécurité.

La protection des systèmes Ubuntu repose donc sur plusieurs mécanismes complémentaires :

* protection des fichiers ;
* protection des configurations ;
* sauvegardes ;
* contrôle des accès ;
* supervision ;
* capacité de restauration.

---

## 2. Protection des fichiers de configuration

Les fichiers de configuration critiques doivent être protégés contre les modifications non autorisées.

Avant toute modification importante :

1. identifier le fichier ;
2. sauvegarder sa version actuelle ;
3. effectuer la modification ;
4. vérifier sa syntaxe ;
5. tester le service ;
6. conserver la sauvegarde selon les besoins.

Les fichiers de configuration critiques doivent être **protégés et sauvegardés**.

---

## 3. Fichiers sensibles

Une attention particulière doit être portée aux fichiers contenant :

* des paramètres de sécurité ;
* des comptes ;
* des privilèges ;
* des secrets ;
* des certificats ;
* des clés privées ;
* des paramètres réseau ;
* des configurations applicatives.

Les permissions doivent empêcher un utilisateur non autorisé de modifier ou de consulter ces données.

---

## 4. Sauvegarde

La sauvegarde doit permettre de restaurer un système ou ses données après :

* une erreur humaine ;
* une défaillance matérielle ;
* une corruption ;
* une mauvaise mise à jour ;
* une compromission ;
* une suppression accidentelle.

Une sauvegarde qui ne peut pas être restaurée ne constitue pas une protection suffisante.

---

## 5. Configuration et données

Il convient de distinguer :

* la sauvegarde du système ;
* la sauvegarde des fichiers de configuration ;
* la sauvegarde des données applicatives ;
* la sauvegarde des secrets ;
* la sauvegarde des éléments nécessaires à la restauration.

Pour les applications critiques, la procédure de restauration doit tenir compte des dépendances.

---

## 6. Principe 3-2-1

Lorsque le niveau de risque le justifie, la stratégie de sauvegarde peut s'appuyer sur le principe :

* plusieurs copies ;
* plusieurs supports ;
* au moins une copie séparée du système principal.

L'objectif est de réduire le risque qu'un même incident détruise simultanément le système et toutes ses sauvegardes.

---

## 7. Protection contre la compromission

Une sauvegarde accessible avec les mêmes privilèges que le système sauvegardé peut être compromise simultanément.

Il faut donc limiter :

* les droits d'accès ;
* les comptes utilisés pour les sauvegardes ;
* l'exposition réseau ;
* les possibilités de suppression ;
* les possibilités de modification.

Lorsque cela est possible, une copie indépendante doit être conservée.

---

## 8. Test de restauration

Une sauvegarde doit être régulièrement testée.

Le test doit permettre de vérifier :

* l'existence de la sauvegarde ;
* son intégrité ;
* son accessibilité ;
* la possibilité de restaurer ;
* la cohérence des données restaurées ;
* le temps nécessaire à la restauration.

La restauration doit être documentée lorsque le système est critique.

---

## 9. Supervision

La supervision doit permettre de détecter les problèmes liés à la sauvegarde ou à l'espace disponible.

Les éléments pouvant être surveillés comprennent :

* espace disque ;
* disponibilité du système ;
* état des services ;
* erreurs ;
* résultat des tâches de sauvegarde lorsque celui-ci est exposé à la supervision.

---

## 10. Sauvegarde avant changement

Avant une modification importante du système :

```bash
cp <fichier> <fichier>.bak
```

Cette méthode constitue une protection ponctuelle pour une configuration, mais ne remplace pas une véritable stratégie de sauvegarde.

La sauvegarde doit être réalisée dans un emplacement adapté au niveau de risque.

---

## 11. Restauration

Une restauration doit être réalisée selon une procédure maîtrisée :

**identifier → sauvegarder l'état actuel si possible → restaurer → vérifier → tester → documenter.**

Après restauration, il faut notamment vérifier :

```bash
systemctl --failed
```

et :

```bash
journalctl -p warning..alert -b
```

Les services nécessaires doivent ensuite être testés fonctionnellement.

---

## 12. Conclusion

La protection d'un système Ubuntu repose autant sur la prévention que sur la capacité à revenir à un état connu.

La sauvegarde doit donc être considérée comme un mécanisme de résilience et non comme une simple copie de fichiers.
