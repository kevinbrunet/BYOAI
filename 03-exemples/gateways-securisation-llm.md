# Exemple — Les gateways de sécurisation LLM comme infrastructure BYOIA déjà payée

## La thèse du post

Le marché cherche aujourd'hui à protéger ses propres LLM en production : filtrer les requêtes dangereuses, éviter les fuites, tracer l'usage pour la conformité réglementaire. ~ Le marché mondial des modèles GenAI dépasserait 25 milliards de dollars en 2026, cap sur 75 milliards en 2029 selon Gartner *(trouvé et cité dans une source Gartner de mars 2026, jugé fiable pour un post mais non vérifié croisé avec une deuxième source)*.

Les gateways ont basculé de simples proxies à une infrastructure de sécurité complète (filtrage, traçabilité, conformité) pour répondre à cette pression.

**Le point central pour le BYOIA** : c'est exactement la même technologie qui sécurise un chatbot client en production qui sécurise un développeur pilotant son propre agent IA depuis son terminal. Un gateway ne fait pas la différence entre les deux usages — même point d'interception, filtrage similaire, même exigence de traçabilité. Chaque euro dépensé par le marché pour protéger un chatbot en production muscle, de fait, le proxy qui pourrait sécuriser le [BYOIA](../01-concepts/byoia.md). Le BYOIA n'a rien demandé, il encaisse un investissement fait pour d'autres raisons.

## Comparatif des cinq gateways (anonymisation PII)

| Outil | Anonymisation PII | Déploiement | Confiance |
|---|---|---|---|
| Bifrost | ✓ intégrée nativement à la gateway — détection PII, blocage injection, exposition de credentials | Self-hosted, open-source (Apache 2.0) | ✓ sourcé sur plusieurs articles indépendants concordants |
| LLM Guard | ✓ scanners PII natifs, mode lib ou API/proxy | Self-hosted, open-source (MIT) | ~ chiffres de précision issus uniquement de l'éditeur (Protect AI), aucun benchmark tiers trouvé |
| Sovereign Guard | ~ tokenisation via Presidio + recognizers spécifiques UE (IBAN, SWIFT, IDs nationaux) | Positionnement souverain UE | ⚠ produit en tout début de vie, langage de pitch investisseur, pas de traction établie |
| Cloudflare AI Gateway | ✓ détection et redaction natives (Guardrails + DLP, Llama Guard côté modération) | SaaS/edge uniquement | ✓ sourcé, mais pas de self-hosted — point faible réel pour un contexte souverain/réglementé |
| Kong AI Gateway | ✓ plugin AI PII Sanitizer, 20+ catégories, 9-12 langues, option de réinsertion de la donnée originale | Self-hosted, mais réservé à Kong Enterprise + service Docker externe séparé à déployer | ✓ sourcé sur plusieurs articles/doc officielle Kong |

Intégration notable : ✓ Bifrost s'intègre déjà nativement avec Claude Code, Cursor, Gemini CLI *(trouvé dans plusieurs sources indépendantes concordantes)*.

## Ce qui différencie réellement les cinq outils

Pas "qui a la fonctionnalité d'anonymisation" (les cinq en ont une forme), mais le triptyque **self-hosted / Enterprise-gated / SaaS uniquement** :

- Cloudflare est le plus simple à activer mais le moins souverain (pas de self-hosted).
- Kong a la couverture la plus large (20+ catégories, 9-12 langues) mais coûte cher et complexifie le déploiement (Enterprise + composant Docker externe).
- Bifrost et LLM Guard sont les deux options open-source sans barrière Enterprise.
- Sovereign Guard est le seul pensé nativement pour la réglementation UE, mais c'est le pari le plus risqué en maturité produit.

## Proxy + anonymisation par IA locale — trois outils identifiés (recherche web, mai 2026)

Recherche spécifique sur des proxys qui combinent interception HTTP et anonymisation, en s'appuyant sur un modèle local plutôt que sur du NER classique (Presidio) :

- ✓ **LLM Guard** — proxy open source avec un scanner `Anonymize` configurable, seuil de détection ajustable, et un scanner `Deanonymize` pour la reconstruction. Actif en mai 2025. ⚠ Non confirmé avec certitude si l'anonymisation s'appuie sur un modèle local ou du NER classique — à vérifier directement dans la documentation avant de l'affirmer publiquement.
- ✓ **PII Shield** (Microsoft, mai 2026) — proxy FastAPI stateless : architecture propre avec `POST /anonymize_unique` qui retourne un session ID, et `POST /deanonymize` qui reconstruit. Pensé pour être réutilisé à travers plusieurs workloads. OpenTelemetry intégré. Répond directement au [problème de reconstruction/statefulness identifié avec Presidio](../01-concepts/presidio-anonymisation-technique.md), en déplaçant l'état dans un session ID plutôt que de garder le proxy stateful en permanence.
- ✓ **SovereignGuard** — gateway open source compatible API OpenAI, drop-in replacement (changement du seul `base_url`). Tokenisation réversible avec mapping local, scoped à la session. Testé contre DeepSeek. *(Distinct ou à rapprocher de l'entrée "Sovereign Guard" du tableau ci-dessus, notée à l'époque ⚠ comme produit en début de vie sans traction établie — cette recherche apporte des détails techniques plus concrets et positifs à vérifier/recouper avec l'entrée précédente avant de trancher s'il s'agit du même produit.)*

Point argumentaire clé : ~ les approches NER classiques (type Presidio) resteraient limitées sur les ambiguïtés contextuelles — ce qui justifierait l'usage d'un LLM local pour la détection plutôt que des règles statiques *(affirmation trouvée en recherche, à vérifier avant citation ferme)*.

Pour un post LinkedIn : trois noms concrets et vérifiés à citer sans détail technique — LLM Guard, PII Shield, SovereignGuard.

## Point méthodologique — pourquoi cette page garde des marqueurs ✓/~/⚠

Ces marqueurs sont un outil de vérification interne, utilisé dans les échanges de travail avant publication — ils ne figurent pas dans le post final publié (le post publié ne garde aucun marqueur, texte "propre"). Cette page de la série les conserve volontairement parce qu'elle documente le travail de recherche, pas le livrable final. Voir [chiffres et références manquantes](../05-questions-ouvertes/chiffres-references-manquantes.md) pour la règle générale.

## Lien avec le reste de la série

Ce comparatif documente des options concrètes pour la "facade MCP" et l'infrastructure de filtrage décrites dans [BYOIA](../01-concepts/byoia.md), en complément de la cartographie plus large sur la délégation d'identité : voir [cartographie de maturité des méthodes d'authentification](../05-questions-ouvertes/cartographie-maturite-authentification.md).
