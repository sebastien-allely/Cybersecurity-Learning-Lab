| **Nom du document**               | `README.md`                                                                                         |
| --------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Technologie**                   | CrowdSec et Fail2ban                                                                                |
| **Catégorie**                     | Protection                                                                                          |
| **Objectif**                      | Présenter les mécanismes de protection complémentaires étudiés et mis en œuvre dans le laboratoire. |
| **Auteur**                        | Sebastien Allely                                                                                    |
| **Version**                       | 1.0                                                                                                 |
| **Date de dernière modification** | 27/09/2026                                                                                          |

# Protection

Cette section documente les mécanismes de protection complémentaires utilisés dans le laboratoire.

Ces mécanismes interviennent après ou en complément du durcissement des systèmes et services. Ils ne remplacent pas les mesures de réduction de surface d'attaque, de contrôle d'accès, de mise à jour ou de supervision.

## Mécanismes documentés

| Mécanisme | Documentation                      |
| --------- | ---------------------------------- |
| CrowdSec  | [Protection CrowdSec](./CrowdSec/) |
| Fail2ban  | [Protection Fail2ban](./Fail2ban/) |

## Relation avec le hardening

Le durcissement vise notamment à réduire la surface d'attaque et les possibilités d'exploitation.

Les mécanismes de protection documentés ici ajoutent des capacités de détection ou de réaction face à certains comportements observables.

```text
Réduction de la surface d'attaque
            ↓
       Hardening
            ↓
Détection / protection complémentaire
            ↓
        Monitoring
            ↓
   Incident Response
```

## Principe

Chaque mécanisme doit être utilisé pour un besoin identifié et faire l'objet d'une validation technique.

Les configurations détaillées doivent rester cohérentes avec les documents d'architecture, de durcissement et de supervision associés.
