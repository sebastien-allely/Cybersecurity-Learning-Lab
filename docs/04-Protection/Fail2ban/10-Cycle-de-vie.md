# Cycle de vie d'une protection Fail2ban

| Élément | Valeur |
|---|---|
| **Nom du document** | `10-Cycle-de-vie.md` |
| **Technologie** | Fail2ban |
| **Catégorie** | Cycle de vie et gestion des changements |
| **Objectif** | Décrire les étapes de décision, de mise en œuvre, de validation et de retrait d'une configuration Fail2ban. |
| **Auteur** | Sébastien Allely |
| **Version** | 1.1 |
| **Date de dernière modification** | 11/10/2026 |

## 1. Objectif

Ce document définit un cycle de vie pour toute nouvelle jail, tout filtre personnalisé et toute modification importante de Fail2ban. L'objectif est d'éviter l'ajout de règles sans besoin démontré et de rendre les changements traçables.

## 2. Étapes du cycle de vie

### 2.1 Besoin et analyse

- Décrire le service et l'actif à protéger.
- Identifier la menace ou le scénario de risque.
- Vérifier si les contrôles existants répondent déjà au besoin.
- Définir les effets attendus, les faux positifs acceptables et les limites.

### 2.2 Conception

- Choisir un filtre et un backend adaptés aux journaux disponibles.
- Définir les paramètres de la jail et l'action de bannissement.
- Vérifier les interactions avec le pare-feu, les accès d'administration et les autres outils de sécurité.
- Définir les critères de réussite et de retour arrière.

### 2.3 Implémentation

- Utiliser des fichiers de configuration locaux et versionnés selon les conventions de la distribution.
- Limiter la portée de la règle aux services réellement concernés.
- Documenter les paramètres non évidents et les exceptions.
- Ne pas copier de secrets, d'adresses réelles ou de journaux identifiants dans le dépôt public.

### 2.4 Vérification

- Tester les motifs positifs et négatifs du filtre.
- Vérifier le chargement de la jail.
- Contrôler les journaux et l'absence d'erreurs.
- Valider la supervision si elle est prévue.
- Vérifier que les accès légitimes ne sont pas bloqués.

### 2.5 Exploitation et revue

- Surveiller les erreurs, les bannissements et les faux positifs.
- Réévaluer les seuils et exclusions à partir des événements observés.
- Revoir la règle après un changement de service, de journalisation ou de distribution.
- Documenter les écarts et les actions correctives.

### 2.6 Retrait

Une règle peut être retirée si le service n'existe plus, si le besoin a disparu ou si une solution mieux adaptée la remplace. Le retrait doit être approuvé, documenté et suivi d'une vérification de la protection restante.

## 3. Critères d'acceptation

Une modification n'est considérée comme validée que si :
- le besoin et le risque sont documentés ;
- le filtre et la configuration ont été testés ;
- la jail attendue est chargée ;
- aucun blocage injustifié n'est constaté lors des tests définis ;
- la supervision et les journaux sont cohérents ;
- le retour arrière est réalisable ;
- la documentation et les références sont à jour.

## 4. Traçabilité

Conserver dans la documentation de changement : objectif, actifs concernés, fichiers modifiés, date, version, tests exécutés, résultat, risques résiduels, responsable de validation et référence à la Pull Request. Ne pas enregistrer d'informations sensibles dans les journaux de changement publics.

## 5. Références

- [Fail2ban — Documentation](https://www.fail2ban.org/wiki/index.php/Main_Page)
- [NIST SP 800-128 — Configuration Management](https://csrc.nist.gov/pubs/sp/800/128/upd1/final)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
