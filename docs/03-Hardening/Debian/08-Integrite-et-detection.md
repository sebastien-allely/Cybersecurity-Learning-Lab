# 08 - Intégrité et détection

| Élément                           | Valeur                                                                                                           |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `08-Integrite-et-detection.md`                                                                                   |
| **Technologie**                   | Debian                                                                                                           |
| **Catégorie**                     | Hardening                                                                                                        |
| **Objectif**                      | Définir les mécanismes permettant de détecter les modifications anormales ou non autorisées d'un système Debian. |
| **Auteur**                        | Sébastien Allely                                                                                                 |
| **Version**                       | 1.0                                                                                                              |
| **Date de dernière modification** | 02/08/2026                                                                                                       |

---

## 1. Objectif

La protection de l'intégrité vise à détecter les modifications qui ne correspondent pas aux changements légitimes d'administration ou de maintenance.

Les éléments particulièrement sensibles comprennent :

* fichiers système ;
* fichiers de configuration ;
* scripts ;
* exécutables ;
* fichiers de services ;
* fichiers de configuration de sécurité.

---

## 2. Pourquoi contrôler l'intégrité

Une modification inattendue peut être la conséquence :

* d'une compromission ;
* d'une élévation de privilèges ;
* d'une erreur d'administration ;
* d'une modification logicielle ;
* d'une opération de maintenance.

Le contrôle d'intégrité ne permet donc pas, à lui seul, de conclure à une compromission.

Il constitue un **signal nécessitant une analyse complémentaire**.

---

## 3. Fichiers prioritaires

Les fichiers à surveiller doivent être sélectionnés en fonction du rôle du système.

Les emplacements génériques importants comprennent notamment :

```text
/etc/
/etc/ssh/
/etc/systemd/
/etc/sudoers
/etc/sudoers.d/
```

Les répertoires propres aux applications doivent être ajoutés lorsqu'ils contiennent des configurations critiques.

---

## 4. AIDE

AIDE peut être utilisé pour comparer l'état actuel des fichiers avec une référence connue.

Le principe général est :

1. construire une base de référence ;
2. surveiller les fichiers définis dans la politique ;
3. comparer l'état actuel avec cette référence ;
4. analyser les différences ;
5. mettre à jour la référence après une modification légitime.

Une modification de la base de référence doit être considérée comme une opération de sécurité.

Elle ne doit pas être effectuée automatiquement après une alerte sans avoir déterminé la cause du changement.

---

## 5. Interprétation des modifications

Une modification détectée doit être classée.

| Situation                         | Action                                              |
| --------------------------------- | --------------------------------------------------- |
| Modification planifiée            | Documenter et valider                               |
| Mise à jour système               | Vérifier le paquet ou la maintenance correspondante |
| Modification administrative       | Vérifier l'opération effectuée                      |
| Modification inconnue             | Investiguer                                         |
| Modification sur fichier critique | Priorité élevée                                     |

Il faut éviter de considérer toute différence comme une compromission.

---

## 6. Intégrité et supervision

Les contrôles d'intégrité peuvent être intégrés à la supervision.

Dans le laboratoire, Zabbix peut servir à signaler :

* l'état du contrôle d'intégrité ;
* l'exécution du contrôle ;
* les erreurs ;
* les résultats nécessitant une investigation.

Cette intégration permet de transformer un contrôle périodique en événement exploitable.

---

## 7. Protection de la base de référence

La base utilisée pour déterminer l'état de référence doit elle-même être protégée.

Un attaquant disposant d'un contrôle suffisant sur le système pourrait autrement modifier à la fois :

* les fichiers surveillés ;
* la base de référence ;
* les mécanismes de contrôle.

La protection de la référence doit donc être prise en compte dans l'architecture de sécurité.

---

## 8. Gestion des changements

Une modification légitime doit être identifiée avant la mise à jour de la référence.

Le processus recommandé est :

1. planifier le changement ;
2. sauvegarder la configuration ;
3. appliquer le changement ;
4. vérifier le fonctionnement ;
5. exécuter le contrôle d'intégrité ;
6. analyser les différences ;
7. mettre à jour la référence si nécessaire ;
8. documenter le changement.

---

## 9. Limites

Le contrôle d'intégrité présente plusieurs limites.

Il ne permet pas nécessairement de détecter :

* une modification effectuée puis restaurée ;
* une activité exécutée uniquement en mémoire ;
* une compromission du mécanisme de contrôle ;
* une activité légitime utilisée à des fins malveillantes.

Il doit donc être associé à :

* la journalisation ;
* la supervision ;
* le contrôle des accès ;
* les mises à jour ;
* la réponse à incident.

---

## 10. Conclusion

L'intégrité constitue une couche de détection complémentaire au durcissement.

Le principe retenu est :

**modifier → vérifier → analyser → documenter → réévaluer la référence.**

Une alerte d'intégrité doit déclencher une analyse et non une simple remise automatique à l'état attendu.
