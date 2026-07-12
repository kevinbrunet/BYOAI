# Objection — Fiabilité des synchronisations écrites par l'IA

## Le problème

"L'IA écrit les synchronisations vite et à faible coût" ([argument 2](../02-arguments/02-interconnexion-facilitee.md)) mérite d'être nuancé, pas juste affirmé. Écrire une synchronisation, oui, c'est rapide. Mais garantir qu'elle reste correcte quand le schéma de données change côté API, qu'elle ne crée pas de duplication silencieuse, qu'elle respecte l'idempotence — l'IA ne résout pas ça par magie.

Un lecteur DSI qui lit l'argument tel quel va immédiatement penser "oui mais la maintenance".

## Deux options

1. Assumer explicitement le risque : il existe, il est mitigé par le fait que l'API reste la source de vérité et que la synchro est reproductible/jetable.
2. Couper l'argument pour ne pas donner prise à la critique facile.
