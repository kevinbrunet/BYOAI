# L'argument IA locale — éviter le problème d'anonymisation à la source

## Le principe

L'anonymisation (Presidio ou équivalent) est une précaution nécessaire quand les données doivent transiter vers un modèle distant. Mais si le modèle tourne en local, le proxy d'anonymisation devient une précaution supplémentaire, pas le seul rempart — les données ne sortent jamais du périmètre.

C'est un argument fort pour le [BYOIA](./byoia.md) : proxy local + modèle local = les données ne quittent jamais le périmètre de l'entreprise. L'anonymisation redevient une option pour les cas où un modèle frontier (plus puissant, mais distant) est quand même nécessaire — pas une brique obligatoire du système.

## Outils d'IA locale identifiés

- ✓ Ollama — serveur local, compatible API OpenAI.
- ✓ llama.cpp — inference locale.
- ✓ LM Studio — interface + serveur local.
- ~ Jan.ai — alternative à LM Studio.

## Nuance à garder

L'IA locale résout le problème de fuite vers un tiers non maîtrisé, mais elle ne résout pas à elle seule la gouvernance interne (qui peut accéder à quoi, traçabilité, conformité CSE/surveillance — voir [cadre juridique CSE](./cadre-juridique-cse-consultation.md)). Un modèle local mal gouverné en interne reste exposé aux mêmes questions de [délégation d'identité pour agents](./delegation-agents-jwt-mtls.md) et d'[intersection de permissions](./conseil-agents-ponderation-bayesienne.md) que n'importe quel autre déploiement.

## Lien avec le reste de la série

Voir [Presidio et le problème de reconstruction](./presidio-anonymisation-technique.md) pour le cas où l'anonymisation reste nécessaire (modèle distant), et [gateways de sécurisation LLM](../03-exemples/gateways-securisation-llm.md) pour les outils qui combinent proxy et anonymisation par IA locale (LLM Guard, PII Shield, SovereignGuard).
