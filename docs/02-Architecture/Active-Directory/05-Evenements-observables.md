# 05 - Événements observables


| Élément | Valeur |
| **Nom du document** | `05-Evenements-observables.md` |
| **Technologie** | Active Directory Domain Services |
| **Catégorie** | Architecture |
| **Objectif** | Identifier les événements Active Directory utiles à la détection et à l'investigation. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


---

# 1. Objectif

Les événements observables permettent de détecter une activité anormale, une tentative de compromission ou une dégradation du fonctionnement d'Active Directory.

Ils constituent les événements prioritaires à superviser.

---

# 2. Authentification

Les événements suivants présentent une valeur opérationnelle :

- échec d'authentification ;
- verrouillage d'un compte ;
- ouverture de session administrateur ;
- authentification Kerberos anormale.

---

# 3. Administration

Les événements critiques sont notamment :

- création d'un utilisateur ;
- suppression d'un utilisateur ;
- ajout dans Domain Admins ;
- modification d'une GPO ;
- création d'un compte de service.

---

# 4. Infrastructure

Les événements suivants doivent être détectés :

- arrêt du service Active Directory ;
- indisponibilité DNS ;
- erreur SYSVOL ;
- échec de sauvegarde ;
- problème de réplication (si plusieurs contrôleurs).

---

# 5. Sécurité

Les événements présentant une forte valeur opérationnelle sont :

- modification des stratégies d'audit ;
- modification des privilèges ;
- suppression de journaux ;
- tentative d'accès non autorisée.

---

# 6. Conclusion

Seuls les événements permettant une décision opérationnelle ou une investigation sont retenus dans le référentiel.
