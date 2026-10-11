# Cycle de vie d'une protection Fail2ban

| Élément | Valeur |
|---|---|
| **Nom du document** | `10-Cycle-de-vie.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Gestion du cycle de vie |
| **Objectif** | Décrire les étapes de conception, validation, exploitation, évolution et retrait d'une protection Fail2ban. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

Le cycle de vie formalise la gestion d'une jail ou d'un filtre, depuis le besoin initial jusqu'au retrait. Il évite que des règles sans propriétaire, non testées ou devenues inutiles restent actives.

## 2. Étapes

### 2.1 Besoin et analyse

- Décrire le service et les journaux disponibles.
- Identifier le comportement à détecter et le risque ciblé.
- Vérifier si un filtre fourni par le projet ou la distribution répond déjà au besoin.
- Définir les impacts possibles des faux positifs et les moyens d'accès de secours.

### 2.2 Conception

- Choisir le filtre, les paramètres de jail et l'action de réponse.
- Justifier les seuils et les durées selon le contexte.
- Limiter les exclusions à ce qui est nécessaire.
- Définir les contrôles de supervision et les critères de réussite.

### 2.3 Test et validation

- Tester les motifs sur des exemples de journaux représentatifs.
- Inclure des cas positifs, négatifs et des variations de format.
- Vérifier que les événements légitimes ne déclenchent pas de bannissement injustifié.
- Vérifier les droits d'accès, les journaux et l'action de pare-feu.
- Enregistrer la version, les résultats et les limites connues.

### 2.4 Déploiement

- Sauvegarder la configuration actuelle.
- Appliquer la modification dans une fenêtre adaptée.
- Valider la configuration et le service.
- Confirmer la présence de la jail attendue et le fonctionnement de la supervision.
- Documenter le changement et son responsable.

### 2.5 Exploitation et réévaluation

Revoir les règles après changement du service, des formats de journaux, du système, du pare-feu ou des versions. Analyser les faux positifs et confirmer que la protection répond toujours au besoin.

### 2.6 Retrait

Désactiver la jail ou le filtre selon une procédure contrôlée, confirmer qu'aucune autre jail ne dépend du composant et retirer uniquement les fichiers et droits devenus inutiles. Contrôler les règles de pare-feu résiduelles et mettre à jour la documentation.

## 3. Critères de décision

| Décision | Critères indicatifs |
|---|---|
| Conserver | Besoin toujours présent, comportement compris, tests concluants |
| Corriger | Besoin valable mais couverture ou comportement insuffisant |
| Remplacer | Une solution mieux maintenue ou plus adaptée existe |
| Retirer | Service supprimé, risque traité autrement ou règle devenue inutile |

La décision doit être fondée sur le risque et les preuves disponibles, et non uniquement sur l'ancienneté d'une règle.

## 4. Traçabilité minimale

Conserver l'identifiant de la règle, le service concerné, le risque ciblé, le propriétaire, les fichiers modifiés, les tests, les résultats, la date de révision et la justification de toute exception.

## 5. Références

- [Fail2ban — Documentation du projet](https://github.com/fail2ban/fail2ban/wiki)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [ANSSI — Publications](https://cyber.gouv.fr/publications)
