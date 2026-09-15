### `docs/06-Incident-Response/04-Investigation.md`

# 04 - Investigation

| Élément                           | Valeur                                                                |
| --------------------------------- | --------------------------------------------------------------------- |
| **Nom du document**               | `04-Investigation.md`                                                 |
| **Technologie**                   | Incident Response                                                     |
| **Catégorie**                     | Incident Response                                                     |
| **Objectif**                      | Décrire une démarche structurée d'analyse d'un événement de sécurité. |
| **Auteur**                        | Sébastien Allely                                                      |
| **Version**                       | 1.0                                                                   |
| **Date de dernière modification** | 05/08/2026                                                            |

---

## 1. Objectif

L'investigation cherche à reconstruire les faits à partir des éléments disponibles.

Elle doit éviter de partir d'une conclusion non vérifiée.

---

## 2. Démarche

```text
Événement
   ↓
Sources disponibles
   ↓
Chronologie
   ↓
Actifs concernés
   ↓
Actions observées
   ↓
Cause probable
   ↓
Impact
```

---

## 3. Chronologie

La chronologie permet notamment de rapprocher :

* les événements système ;
* les événements applicatifs ;
* les alertes de supervision ;
* les décisions de protection ;
* les actions d'administration.

---

## 4. Corrélation

Une information isolée peut être insuffisante.

La corrélation de plusieurs sources permet de renforcer ou d'infirmer une hypothèse.

Exemple :

```text
Tentatives d'authentification
          +
alerte CrowdSec
          +
blocage
          +
événement Zabbix
```

Cette corrélation ne constitue toutefois pas automatiquement la preuve d'une compromission.

---

## 5. Conclusion

Une conclusion d'investigation doit distinguer :

* les faits établis ;
* les éléments probables ;
* les éléments non déterminés.

Cette distinction permet d'éviter les conclusions excessives.
