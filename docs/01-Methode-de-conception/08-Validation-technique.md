# 08 - Validation technique

| Élément                           | Valeur                                                                                                                                            |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `08-Validation-technique.md`                                                                                                                      |
| **Technologie**                   | Méthode de conception                                                                                                                             |
| **Catégorie**                     | Méthodologie                                                                                                                                      |
| **Objectif**                      | Définir la méthode permettant de vérifier qu'une décision technique ou de sécurité est correctement mise en œuvre et produit le résultat attendu. |
| **Auteur**                        | Sébastien Allely                                                                                                                                  |
| **Version**                       | 1.0                                                                                                                                               |
| **Date de dernière modification** | 04/08/2026                                                                                                                                        |

---

# Objectif

Une mesure de sécurité ne peut pas être considérée comme maîtrisée uniquement parce qu'elle a été configurée.

Elle doit être **vérifiée**.

La validation technique permet de démontrer que :

* la configuration attendue est présente ;
* le service fonctionne ;
* le mécanisme produit le comportement attendu ;
* les événements associés sont observables ;
* la supervision fonctionne lorsque celle-ci est applicable ;
* les limites identifiées sont connues.

La validation constitue donc le lien entre la **décision** et la **preuve de son efficacité technique**.

---

# Principe

La validation doit être définie avant ou au moment de la mise en œuvre.

La logique retenue est :

```text
Décision
   ↓
Résultat attendu
   ↓
Méthode de vérification
   ↓
Test
   ↓
Résultat observé
   ↓
Conclusion
```

Une configuration qui ne peut pas être vérifiée constitue un point faible dans la maîtrise du système.

---

# 1. Vérifier la configuration

La première étape consiste à vérifier que la configuration réellement appliquée correspond à la configuration attendue.

La vérification peut notamment porter sur :

* les fichiers de configuration ;
* les permissions ;
* les services actifs ;
* les paramètres ;
* les règles réseau ;
* les comptes ;
* les tâches planifiées ;
* les mécanismes de sécurité activés.

La vérification doit porter sur **l'état réel du système**, et non uniquement sur les fichiers qui ont été modifiés.

---

# 2. Vérifier le fonctionnement

Une configuration correcte ne garantit pas qu'un service fonctionne correctement.

Il faut donc vérifier :

* l'état du service ;
* les processus associés ;
* les ports nécessaires ;
* les dépendances ;
* les journaux ;
* les erreurs éventuelles.

Exemple de logique :

```text
Configuration présente
        ↓
Service démarré
        ↓
Dépendances disponibles
        ↓
Fonctionnement opérationnel
```

---

# 3. Tester le comportement attendu

Lorsque cela est possible, un test doit provoquer le comportement attendu.

Le test doit être adapté au composant étudié.

Exemples :

* provoquer une tentative d'authentification incorrecte ;
* vérifier qu'un fichier est détecté ;
* provoquer un événement de supervision ;
* vérifier qu'une règle réseau bloque le flux attendu ;
* vérifier qu'une sauvegarde peut être restaurée.

Un test doit rester contrôlé et ne pas introduire de risque inutile dans le laboratoire.

---

# 4. Vérifier les événements observables

La validation doit également déterminer si les événements associés à la mesure sont correctement enregistrés.

Les sources peuvent notamment être :

* journaux système ;
* journaux applicatifs ;
* journaux de sécurité ;
* métriques ;
* événements réseau ;
* événements Zabbix.

La question à résoudre est :

> Si le mécanisme fonctionne ou échoue, où puis-je le constater ?

Cette information est essentielle pour la supervision et le diagnostic.

---

# 5. Vérifier la supervision

Lorsqu'une mesure est supervisée, il faut vérifier non seulement que l'item ou le contrôle existe, mais également que le mécanisme d'alerte fonctionne.

La validation peut comprendre :

```text
Événement
   ↓
Collecte
   ↓
Item / métrique
   ↓
Condition
   ↓
Trigger
   ↓
Alerte
```

Un mécanisme de supervision qui n'a jamais été testé ne doit pas être considéré comme fiable.

---

# 6. Documenter le résultat

Chaque validation importante doit permettre de conserver une trace du résultat.

La documentation doit préciser au minimum :

| Élément          | Description                    |
| ---------------- | ------------------------------ |
| Objet            | Ce qui est validé              |
| Précondition     | État nécessaire avant le test  |
| Méthode          | Procédure utilisée             |
| Résultat attendu | Comportement recherché         |
| Résultat observé | Comportement réellement obtenu |
| Conclusion       | Conforme ou non conforme       |
| Date             | Date du contrôle               |

La preuve peut prendre différentes formes :

* sortie de commande ;
* journal ;
* capture d'écran lorsque celle-ci apporte une valeur ;
* résultat d'un script ;
* événement Zabbix ;
* rapport de test.

---

# 7. Gestion des échecs

Un résultat non conforme ne doit pas être masqué.

Il doit permettre d'identifier :

* la configuration incorrecte ;
* la dépendance défaillante ;
* le comportement inattendu ;
* la limite de la solution ;
* l'erreur de conception éventuelle.

La démarche devient alors :

```text
Test
 ↓
Échec
 ↓
Analyse
 ↓
Correction
 ↓
Nouveau test
 ↓
Validation
```

Une validation n'est donc pas uniquement un contrôle final. Elle participe également à l'amélioration du système.

---

# 8. Réversibilité

Lorsqu'une validation nécessite une modification du système, celle-ci doit être réversible lorsque cela est possible.

Avant un changement important :

* sauvegarder la configuration ;
* identifier l'état initial ;
* documenter la modification ;
* prévoir le retour arrière.

La validation ne doit pas créer un risque supérieur à celui qu'elle cherche à maîtriser.

---

# 9. Critères de validation

Une décision peut être considérée comme techniquement validée lorsque :

* la configuration attendue est présente ;
* le fonctionnement attendu est démontré ;
* les événements pertinents sont observables ;
* les contrôles applicables ont été réalisés ;
* les résultats sont documentés ;
* les éventuelles limites sont identifiées.

La validation ne signifie pas que le risque est supprimé.

Elle démontre que la mesure fonctionne conformément au comportement attendu dans les conditions testées.

---

# 10. Réévaluation

Une validation n'est pas nécessairement définitive.

Elle doit être renouvelée lorsqu'un changement significatif intervient, notamment :

* modification de configuration ;
* changement de version ;
* modification d'une dépendance ;
* modification de l'architecture ;
* changement du niveau d'exposition ;
* modification du mécanisme de supervision.

La validation fait donc partie du cycle de vie du composant.

---

# Principe de conception

Le référentiel retient la chaîne suivante :

```text
Décision
   ↓
Résultat attendu
   ↓
Test
   ↓
Observation
   ↓
Validation
   ↓
Supervision
   ↓
Réévaluation
```

La sécurité ne doit pas être considérée comme acquise parce qu'une configuration a été appliquée.

Elle doit être démontrée par des contrôles reproductibles.

---

# Conclusion

La validation technique permet de transformer une configuration en résultat démontré.

Elle fournit une preuve que la décision prise a été correctement mise en œuvre et qu'elle produit le comportement attendu dans les conditions testées.

Elle constitue également une base nécessaire à la supervision, à la maintenance et à la réévaluation des décisions de sécurité.
