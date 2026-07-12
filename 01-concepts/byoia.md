# BYOIA — Bring Your Own IA

## Définition

Le BYOIA n'est pas un gadget RH ni une mode. C'est l'infrastructure qui permet à chaque collaborateur de connecter sa propre équipe IA (ses "conseillers", ses "intérimaires" personnels) aux API de l'entreprise, pour produire le travail demandé — sans exposer l'entreprise aux risques d'un Shadow IT généralisé et sans accès direct et autonome au SI.

**Positionnement intellectuel** : le BYOIA est le versant organisationnel du courant *malleable software* (Litt, Ink & Switch) — voir [positionnement](./positionnement-malleable-software.md).

## Le piège que le BYOIA doit éviter

Si chaque salarié se met à coder son outil "parfait" avec un LLM connecté à ses données métier, sans cadre, on recrée en pire tous les problèmes déjà connus avec le Shadow IT — sauf que cette fois l'outil a un accès direct et autonome au SI.

## Les briques d'infrastructure identifiées

- Facade MCP pour contrôler ce à quoi l'IA a réellement accès
- Allowlist de modèles (OAuth 2.1) plutôt que blocage binaire
- Couche d'enrichissement contextuel qui reste sous gouvernance IT
- Traçabilité pour la conformité (RGPD, chaîne d'approvisionnement logicielle)

## Comment ça fonctionne concrètement

Le collaborateur connecte les API de l'entreprise (structure, données, règles de gestion) à son équipe IA personnelle pour réaliser la tâche qui lui est demandée. Il fournit en retour les données nécessaires à son suivi via ces mêmes API vers la partie commune.

Exemple DSI : le collaborateur branche son harnais IA personnel sur Git/Jira/Teams — la structure (rôles, sécurité, DoD/DoR) reste commune, la réalisation de l'étape est individuelle. Voir [Git, DoD, DoR dans la DSI](../03-exemples/git-dod-dor-dsi.md).

## Distinction importante avec Claude Tag

Claude Tag (Anthropic, Slack) illustre un principe voisin mais différent : c'est l'entreprise qui possède et configure l'agent partagé du canal, pas le collaborateur qui apporte son IA personnelle. Ce n'est pas du BYOIA à proprement parler — c'est le même principe de séparation structure/interface, mais appliqué à l'accès entrant plutôt qu'à la production sortante. Voir [accès conversationnel](./acces-conversationnel.md) et [exemple Claude Tag](../03-exemples/claude-tag-slack.md).

## Ce que le BYOIA ne résout pas — correction importante

L'hypothèse "BYOIA = plus sûr juridiquement, échappatoire à la consultation du CSE" a été testée et invalidée : le risque juridique (obligation de consultation CSE, proportionnalité de la surveillance de l'activité) est attaché à l'effet réel sur le salarié, pas à la couche technique qui l'héberge. Voir [pourquoi le BYOIA n'est pas plus sûr juridiquement](../04-objections/byoia-pas-plus-sur-juridiquement.md) et le repositionnement honnête : [conformité par design](./conformite-par-design.md).

## Implémentation technique possible

La facade MCP et l'allowlist de modèles décrites plus haut peuvent s'appuyer sur des mécanismes concrets de délégation d'identité (séparation transport/application, chaîne `act` imbriquée, intersection de permissions) — voir [délégation d'identité pour agents](./delegation-agents-jwt-mtls.md), [exemple Kagenti/AuthBridge](../03-exemples/kagenti-authbridge-red-hat.md) et la [cartographie de maturité des méthodes d'authentification](../05-questions-ouvertes/cartographie-maturite-authentification.md).

Sur le volet filtrage/anonymisation spécifiquement, le marché des gateways de sécurisation LLM (Bifrost, LLM Guard, Sovereign Guard, Cloudflare AI Gateway, Kong AI Gateway) produit déjà, pour d'autres raisons (sécuriser des chatbots en production), l'infrastructure que le BYOIA peut réutiliser telle quelle — voir [gateways de sécurisation LLM](../03-exemples/gateways-securisation-llm.md).

## Le débat que ça déplace

Le débat n'est plus "faut-il autoriser l'IA pour créer des outils métier". Il est "comment on architecture le fait que ça va arriver de toute façon". Uniformiser était une solution à un problème de coût ; ce problème a largement disparu. La solution doit se transformer en gouvernance de la diversité, pas en fabrique du consensus mou.
