# 01 - Justification des décisions


| Élément | Valeur |
| **Nom du document** | `01-Justification-des-decisions.md` |
| **Technologie** | Apache HTTP Server |
| **Catégorie** | Hardening |
| **Objectif** | Définir les principes guidant les décisions de durcissement d'Apache HTTP Server. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.0 |
| **Date de dernière modification** | 01/08/2026 |


Chaque mesure est mise en œuvre parce qu'elle répond à un risque identifié, et non parce qu'elle figure dans une liste de bonnes pratiques.

---

# 6. Vérification

Avant d'appliquer une mesure de durcissement, il convient de répondre aux questions suivantes :

- Quel actif protège-t-elle ?
- Quel risque réduit-elle ?
- Introduit-elle une nouvelle dépendance ?
- Peut-elle être contrôlée ?
- Peut-elle être supervisée ?
- Est-elle compatible avec les futures mises à jour ?

Si ces questions ne trouvent pas de réponse satisfaisante, la mesure doit être réévaluée.

---

# 7. Conclusion

Le référentiel ne cherche pas à appliquer un durcissement maximal.

Il cherche à appliquer un durcissement justifié.

Chaque décision doit être comprise, documentée, vérifiée et maintenable afin de garantir la pérennité de la sécurité du serveur Web.

---

# Références

## Référentiels

- ANSSI – Guide d'hygiène informatique.
- EBIOS Risk Manager.
- NIST Cybersecurity Framework.

## Documentation officielle

- Apache HTTP Server Documentation.

## Guides techniques

- SOCLE – Stéphane Robert (durcissement des services Linux et des serveurs Web).

## Veille

Toute nouvelle mesure de durcissement devra être évaluée selon les principes définis dans ce document avant d'être intégrée au référentiel.
