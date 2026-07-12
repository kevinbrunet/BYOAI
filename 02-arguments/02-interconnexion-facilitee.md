# Argument 2 — L'interconnexion cesse d'être le goulot d'étranglement

## Le raisonnement ancien

"Il faut un outil unique pour que l'information circule" supposait que synchroniser plusieurs systèmes était coûteux et fragile.

## Ce que l'IA change

L'IA écrit ces synchronisations vite et à faible coût. L'intégration n'est plus un projet, c'est une tâche.

## À nuancer

Écrire une synchronisation est rapide, mais garantir qu'elle reste correcte quand le schéma de données change côté API, qu'elle ne crée pas de duplication silencieuse, qu'elle respecte l'idempotence — ça, l'IA ne le résout pas par magie. Voir [fiabilité des synchronisations écrites par l'IA](../04-objections/synchronisation-fiabilite.md). Deux options pour tenir cet argument sans donner prise à la critique facile : l'assumer explicitement (le risque existe, mitigé par le fait que l'API reste source de vérité et que la synchro est reproductible/jetable), ou couper l'argument.
