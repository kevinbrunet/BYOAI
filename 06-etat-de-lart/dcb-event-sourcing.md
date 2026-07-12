# État de l'art — DCB et event sourcing (recherche web, juillet 2026)

## DCB est un terme établi de l'event sourcing — attention à la collision

- ✓ **"Dynamic Consistency Boundary" (DCB)** est un concept installé dans la communauté event sourcing, popularisé par **Sara Pellegrini**, avec un site dédié (dcb.events), une implémentation dans **Axon Framework 5**, dans **EventSourcingDB** et dans la lib Python `eventsourcing`.
- ✓ Le DCB "officiel" : définir la frontière de cohérence forte **à l'exécution, par opération**, au lieu de la figer dans des agrégats — "la cohérence devient une condition, pas une structure". Les events sont tagués et un event peut affecter plusieurs entités du même bounded context.
- ✓ Mécanique standard : une commande lit une sélection d'events, les projette en **decision model**, puis génère de nouveaux events — la requête définit la frontière.

## Implication directe pour la série

⚠ **Collision de sigle** : le fichier [dcb-decisions-comme-events](../01-concepts/dcb-decisions-comme-events.md) utilise "DCB" pour "décisions comme events" — ce n'est PAS le sens établi. Un lecteur event sourcing comprendra "Dynamic Consistency Boundary". Trois options : (a) renommer le concept de la série, (b) adopter le DCB officiel et reformuler "décisions comme events" comme son application à la gouvernance architecturale, (c) assumer et désambiguïser dès la première page. L'option (b) est la plus forte : le "decision model" de Pellegrini est déjà à mi-chemin, et la doctrine de la [frontière fiduciaire](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) (écritures = SI, projections = interface) s'exprime naturellement dans ce cadre.

- Bonus : le DCB officiel renforce l'emboîtement doctrine/architecture — frontières de cohérence dynamiques côté SI, projections libres côté interface, exactement la lecture CQRS déjà posée.

## Sources

- [dcb.events — site de référence](https://dcb.events/)
- [AxonIQ — DCB in Axon Framework 5](https://www.axoniq.io/blog/dcb-in-af-5)
- [eventsourcing.dev — Dynamic Consistency Boundaries](https://www.eventsourcing.dev/best-practices/dynamic-consistency-boundaries)
- [EventSourcingDB — DCBs](https://docs.eventsourcingdb.io/best-practices/dynamic-consistency-boundaries/)
- [JAVAPRO — Dynamic consistency boundaries](https://javapro.io/2025/10/28/dynamic-consistency-boundaries/)
