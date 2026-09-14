---

Nom du document : README des Labs
Technologie : Multi-technologies
Catégorie : Travaux pratiques
Objectif : Présenter l'organisation, les règles et les objectifs des travaux pratiques du laboratoire
Auteur : Sébastien ALLELY
Version : 1.0
Date de dernière modification : 13/09/2026
------------------------------------------

# Labs

## 1. Objectif

Les labs regroupent les travaux pratiques permettant de **mettre en œuvre, vérifier et valider** les mesures décrites dans la documentation du projet.

Ils complètent les documents d'architecture, de durcissement, de protection, de supervision et de réponse à incident.

Chaque lab doit permettre de répondre à une question technique concrète et produire un résultat vérifiable.

Le principe est :

**concevoir → configurer → tester → observer → diagnostiquer → valider**

---

## 2. Organisation

Les travaux pratiques sont regroupés par technologie ou domaine technique.

```text
labs/
├── README.md
└── 01-Proxmox/
    ├── 01-Verification-du-durcissement.md
    ├── 02-Verification-du-cluster.md
    ├── 03-Verification-des-sauvegardes.md
    └── 04-Test-de-restauration.md
```

Les labs peuvent évoluer avec le projet. Un nouveau scénario doit être ajouté uniquement lorsqu'il apporte une validation technique identifiable.

---

## 3. Principes

Chaque lab doit :

* avoir un objectif clairement défini ;
* préciser les prérequis ;
* identifier les composants concernés ;
* décrire les manipulations à effectuer ;
* définir les éléments observables ;
* préciser le résultat attendu ;
* permettre de déterminer si le test est réussi ou non ;
* identifier les risques éventuels liés au test ;
* éviter toute action destructive non maîtrisée.

Les manipulations doivent être réalisées dans un environnement de laboratoire.

---

## 4. Structure d'un lab

Chaque fiche de travaux pratiques suit autant que possible cette structure :

1. Objectif
2. Contexte
3. Prérequis
4. Périmètre
5. Risques
6. Procédure
7. Vérifications
8. Résultats attendus
9. Analyse
10. Critères de validation
11. Retour d'expérience
12. Références

---

## 5. Méthode de validation

Un test n'est pas considéré comme validé uniquement parce qu'une commande s'exécute correctement.

La validation doit prendre en compte :

* le comportement attendu du système ;
* les journaux disponibles ;
* les événements remontés par la supervision ;
* les mécanismes de sécurité concernés ;
* les conséquences éventuelles sur les autres composants ;
* la capacité à revenir à un état fonctionnel.

Lorsque cela est pertinent, le résultat doit être confronté aux objectifs définis dans la documentation du projet.

---

## 6. Sécurité des manipulations

Les tests pouvant provoquer une indisponibilité, une perte de données ou une modification importante de la configuration doivent être identifiés avant leur exécution.

Les tests destructifs ou potentiellement perturbateurs doivent être réalisés uniquement lorsqu'une procédure de retour arrière est disponible.

La priorité est donnée aux tests d'observation et de validation avant les tests de rupture.

---

## 7. Relation avec la documentation

Les labs ne doivent pas reproduire intégralement les documents techniques.

La documentation explique :

* pourquoi une technologie est utilisée ;
* comment elle est conçue ;
* quels sont ses risques ;
* quelles mesures de sécurité sont retenues.

Les labs permettent de vérifier concrètement :

* que la configuration correspond aux décisions documentées ;
* que les mécanismes de sécurité fonctionnent ;
* que les événements sont observables ;
* que les procédures d'exploitation ou de restauration sont réalisables.

---

## 8. Critères de qualité

Un lab est considéré comme exploitable lorsqu'un autre administrateur disposant des mêmes prérequis peut :

1. comprendre l'objectif du test ;
2. reproduire la manipulation ;
3. identifier les résultats attendus ;
4. déterminer si le test est réussi ;
5. comprendre les éventuels écarts ;
6. revenir à un état fonctionnel lorsque cela est nécessaire.

---

## 9. Références

Les références techniques doivent être indiquées directement dans les fiches concernées.

Les sources privilégiées sont :

* ANSSI ;
* NIST ;
* OWASP lorsque le sujet concerne la sécurité applicative ;
* MITRE ATT&CK lorsque le sujet concerne les techniques d'attaque ;
* documentations officielles des éditeurs ;
* SOCLE de Stéphane Robert lorsqu'il constitue une référence technique d'implémentation pertinente ;
* guides techniques reconnus en complément.

Le SOCLE de Stéphane Robert constitue une **référence technique d'implémentation** et non un référentiel normatif.
