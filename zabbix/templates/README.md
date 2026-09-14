# Templates Zabbix

| Élément                           | Valeur                                                                                                  |
| --------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Nom du document**               | `README.md`                                                                                             |
| **Technologie**                   | Zabbix                                                                                                  |
| **Catégorie**                     | Monitoring / Supervision                                                                                |
| **Objectif**                      | Présenter l'organisation des templates Zabbix utilisés par le Cybersecurity-Learning-Lab et leur rôle. |
| **Auteur**                        | Sébastien Allely                                                                                        |
| **Version**                       | 1.0                                                                                                     |
| **Date de dernière modification** | 13/08/2026                                                                                              |

---

# 1. Objectif

Ce répertoire contient les templates Zabbix utilisés par le laboratoire.

Les templates regroupent les éléments de supervision nécessaires à un type de système ou de service.

Ils permettent notamment de regrouper :

- les items ;
- les triggers ;
- les macros ;
- les dépendances ;
- les règles de découverte lorsque nécessaire ;
- les éléments nécessaires à la supervision des composants du laboratoire.

---

# 2. Documentation associée

Chaque template doit être associé à une documentation permettant de comprendre :

- son objectif ;
- les données collectées ;
- les triggers ;
- les macros ;
- les dépendances ;
- les éventuelles commandes privilégiées ;
- les conditions de validation.

La documentation technique doit permettre de comprendre le fonctionnement du template sans avoir à examiner directement sa configuration dans Zabbix.

---

# 3. Organisation

Les templates sont organisés selon les composants ou technologies qu'ils supervisent.

Les fichiers et répertoires présents dans ce dossier doivent rester cohérents avec les templates réellement utilisés ou validés dans le laboratoire.

---

# 4. Principe de supervision

Les templates doivent privilégier une supervision utile et exploitable.

Un élément de supervision ne doit pas être ajouté uniquement parce qu'une donnée peut être collectée.

Chaque item doit répondre à un besoin identifié, notamment :

- disponibilité ;
- capacité ;
- performance ;
- sécurité ;
- intégrité ;
- fonctionnement d'un service ;
- détection d'une anomalie.

Les triggers doivent également correspondre à des situations nécessitant réellement une attention ou une action.

---

# 5. Sécurité

Les templates ne doivent contenir :

- aucun secret ;
- aucun mot de passe ;
- aucune clé privée ;
- aucune donnée personnelle ;
- aucune information permettant d'identifier une infrastructure réelle.

Les noms d'hôtes, domaines, adresses IP et autres informations spécifiques à l'infrastructure personnelle doivent être anonymisés lorsqu'ils sont nécessaires à titre d'exemple.

Les commandes privilégiées utilisées par les UserParameters ou les éléments de supervision doivent être documentées et limitées au strict nécessaire.

---

# 6. Validation

Avant d'être intégré au laboratoire, un template doit être testé dans l'environnement prévu.

La validation doit notamment vérifier :

- la collecte des données attendues ;
- le fonctionnement des triggers ;
- les valeurs des macros ;
- les dépendances ;
- l'absence de faux positifs importants ;
- l'absence de commandes ou permissions inutilement privilégiées.

Un template considéré comme valide doit correspondre à une configuration réellement fonctionnelle dans le laboratoire.

---

# 7. Relation avec les UserParameters

Certains templates peuvent dépendre de données fournies par des UserParameters exécutés par Zabbix Agent 2.

Dans ce cas, la documentation doit permettre d'identifier :

1. le UserParameter nécessaire ;
2. le fichier de configuration concerné ;
3. les éventuelles permissions supplémentaires ;
4. la commande utilisée ;
5. la méthode de validation.

Les UserParameters sont documentés dans :

`zabbix/userparameters/`

---

# 8. Reproductibilité

Les templates doivent pouvoir être reproduits dans un environnement équivalent à celui décrit par le laboratoire.

Les éléments dépendant d'une configuration personnelle doivent être clairement identifiés et anonymisés avant publication.

L'objectif est de fournir des configurations compréhensibles et adaptables plutôt qu'une copie exacte d'une infrastructure personnelle.

---

# 9. Évolution

Les templates pourront évoluer avec l'infrastructure et les besoins de supervision du laboratoire.

Toute modification importante doit être cohérente avec :

- la documentation Zabbix ;
- les UserParameters associés ;
- les permissions nécessaires ;
- les mécanismes de sécurité ;
- les procédures de validation.

---

# Conclusion

Le répertoire `templates/` constitue la couche de configuration des templates Zabbix du Cybersecurity-Learning-Lab.

Il doit rester distinct :

- de la documentation générale du laboratoire ;
- des UserParameters ;
- des scripts d'automatisation ;
- de la configuration spécifique à une machine.

Cette séparation permet de conserver une organisation claire et de rendre les éléments de supervision réutilisables et compréhensibles.
