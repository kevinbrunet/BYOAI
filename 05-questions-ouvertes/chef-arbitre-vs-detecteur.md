# Question ouverte — Chef-arbitre vs chef-détecteur

## La question

Un chef d'un conseil d'agents peut jouer deux rôles très différents :

1. **Arbitre** : il résout le désaccord, tranche une réponse finale.
2. **Détecteur** : il constate qu'il y a désaccord et route vers un humain, sans trancher lui-même.

Ce sont deux architectures différentes, pas une variante mineure l'une de l'autre.

## Élément de cadrage

La littérature sur la tolérance aux pannes byzantines penche fortement vers la seconde option (détecteur + routage humain) pour des systèmes à enjeu réglementaire élevé. Un arbitre automatique final sur un système à enjeu de conformité élevé complique probablement la justification de la traçabilité de décision, comparé à un simple routage vers revue humaine. ⚠ Position normative précise non vérifiée — à confirmer directement dans les textes réglementaires concernés avant affirmation.

## Statut

Non tranché. Voir [architectures de référence pour l'agrégation multi-agents](../03-exemples/architectures-agregation-references.md) et [conseil d'agents et pondération bayésienne](../01-concepts/conseil-agents-ponderation-bayesienne.md) pour le contexte complet.
