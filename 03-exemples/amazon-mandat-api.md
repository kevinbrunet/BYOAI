# Exemple — Le mandat API d'Amazon (2002)

## Le fait

✓ Vers 2002, Jeff Bezos impose par mémo interne une règle absolue à toutes les équipes d'Amazon. Le texte n'a jamais été publié officiellement — il est connu par le "platform rant" de Steve Yegge (ingénieur ex-Amazon, 2011, publié par accident depuis Google+), considéré comme fiable par toute l'industrie. Les règles :

1. Toutes les équipes exposent leurs données et fonctionnalités **uniquement via des interfaces de service** (API).
2. Les équipes communiquent entre elles **uniquement** à travers ces interfaces.
3. **Aucune autre forme de communication autorisée** : pas de lien direct, pas de lecture directe de la base d'une autre équipe, pas de mémoire partagée, pas de porte dérobée. Tout passe par le réseau, par l'API.
4. La technologie utilisée est indifférente (HTTP, Corba, pubsub, protocole maison) — Bezos s'en moque.
5. Toutes les interfaces, sans exception, doivent être conçues dès le départ pour être **exposables à l'extérieur**.

Et la conclusion du mémo, restée célèbre : *"Anyone who doesn't do this will be fired. Thank you; have a nice day!"*

## Ce que ça a produit

✓ En quelques années, Amazon s'est transformée en architecture orientée services de bout en bout — Yegge témoigne que la pensée "service d'abord" est devenue culturelle, appliquée même aux systèmes internes qui ne seront jamais exposés. La règle 5 (exposable à l'extérieur) est celle qui a rendu AWS possible : l'infrastructure interne était déjà conçue comme un produit.

## Pourquoi c'est le précédent fondateur du BYOIA

1. **C'est l'[approche data-centrique](../01-concepts/approche-datacentrique.md) prouvée à l'échelle** : quand la structure (données, règles, fonctionnalités) est intégralement accessible par API et *seulement* par API, n'importe quel organe de production peut s'y brancher — une autre équipe, un produit externe... ou demain le harnais IA d'un collaborateur. Le BYOIA ne demande rien de plus que ce qu'Amazon s'est imposé en 2002.
2. **La règle 3 est la doctrine de la frontière, version 2002** : interdire les portes dérobées, c'est dire que tout [changement d'état passe par le SI](../05-questions-ouvertes/doctrine-frontiere-si-interface.md). Amazon l'a fait pour des équipes ; le BYOIA le fait pour des agents.
3. **La valeur est venue d'où on ne l'attendait pas** : le mandat visait la dette d'intégration interne ; il a produit AWS. Argument pour les DSI : préparer le SI au BYOIA (API partout, zéro porte dérobée), c'est créer une option sur des usages non anticipés, pas seulement répondre à la mode IA.

## Limites de l'exemple

- ⚠ Pas de source primaire : le mémo lui-même n'a jamais fui — tout repose sur Yegge et les récits concordants d'anciens d'Amazon. Citer comme "récit établi de l'industrie", pas comme document.
- Le coût a été réel (Yegge décrit des années difficiles : découpage des services, pièges de la distribution, quotas, monitoring). L'honnêteté du livre exige de le dire : le prérequis API n'est pas gratuit — c'est un investissement pluriannuel pour une DSI qui part de loin.

## Sources

- [Steve Yegge — Google Platforms Rant (copie)](https://gist.github.com/kislayverma/d48b84db1ac5d737715e8319bd4dd368)
- [Kong — API Mandate: How Bezos' memo changed software](https://konghq.com/blog/enterprise/api-mandate)
- [Axway — Jeff Bezos' API mandate: les cinq règles](https://blog.axway.com/learning-center/digital-strategy/api-first/jeff-bezos-api-mandate)
- [API Evangelist — The Secret to Amazon's Success](https://apievangelist.com/2012/01/12/the-secret-to-amazons-success-internal-apis/)
