# État de l'art — "Coder avec l'IA", guide praticien du harnais (mai 2026)

Source : PDF de 29 slides ("Coder avec l'IA — Guide pratique", v1.0 interne mai 2026, version publique juillet 2026, diffusé via LinkedIn — ⚠ auteur non identifié dans le document). Intérêt : c'est la doctrine *praticien* du harnais, côté développeur individuel. Le vocabulaire du livre (harnais, skills, garde-fous) y apparaît stabilisé comme vocabulaire d'industrie — et les manques du guide sont exactement l'espace du BYOIA.

## Ce que le guide apporte (vérifié)

- ✓ **Le harnais comme modèle mental dominant** : "un LLM brut est un cheval sauvage ; chaque outil du marché est un harnais différent". Anatomie en 5 couches : modèle / harnais / skills / contexte / garde-fous. Confirme que la métaphore du ch. 5 n'est pas idiosyncratique — elle est devenue le cadre de lecture standard du marché.
- ✓ **"Thin harness, fat skills"** (attribué à Garry Tan) : harnais minimal en code, tous les processus dans des skills Markdown en langage naturel. Les frameworks lourds (LangChain 2024, AutoGPT) sont cités comme contre-modèle mort. Conséquence formulée par le guide : *"un dev qui écrit un bon SKILL.md apporte plus de valeur qu'un dev qui code un orchestrateur complexe"* — convergence directe avec la [règle exécutable](../01-concepts/regle-executable-fin-du-wiki.md) : le processus encodé en langage naturel exécutable est l'actif, pas le code.
- ✓ **GStack existe et pèse** : skill pack open-source de Garry Tan (CEO Y Combinator), 23 rôles (CEO, Eng Manager, QA, Security...), MIT, ~108K stars en quelques semaines (le PDF dit ~120K+ — ordre de grandeur cohérent). Vérifié : [github.com/garrytan/gstack](https://github.com/garrytan/gstack).
- ✓ **Conductor existe** : app Mac d'orchestration de sessions Claude Code parallèles, une par worktree Git. Vérifié : [conductor.build](https://www.conductor.build/).
- ✓ **Stats MCP confirmées** : don à l'Agentic AI Foundation (Linux Foundation) en décembre 2025, co-fondée Anthropic/Block/OpenAI ; 10K+ serveurs publics ; 97M téléchargements SDK mensuels. Sources : [Anthropic](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation), [Linux Foundation](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation).
- ✓ **Pyramide de maturité** : prompt engineering → context engineering → intent engineering → specification engineering. Le sommet ("corpus machine-readable de toutes les policies, standards, processus de l'org") est exactement la [conformité par design](../01-concepts/conformite-par-design.md) + la règle exécutable — le guide le présente comme horizon, le livre le traite comme architecture.
- ✓ **Les 4 pratiques de context engineering d'Anthropic** (offloading, retrieval, isolation, compression) — publiées fin 2025, devenues vocabulaire d'industrie.

## Chiffres à ne pas reprendre tels quels

- ⚠ "416 heures/an perdues à tester des outils" — arithmétique rhétorique (2×4h/semaine), pas une mesure.
- ⚠ Règle "90/10" (90 % contexte, 10 % modèle), "+5 % par saut de modèle vs +50 % par meilleur contexte" — assertions sans source, invérifiables.
- ~ "4-7x plus de tokens en multi-agent (selon Anthropic)" — l'étude Anthropic 2025 sur son système de recherche multi-agents donnait plutôt ~4x (agent vs chat) et ~15x (multi-agent vs chat). L'ordre de grandeur est bon, l'attribution est approximative.
- ⚠ "Ticket en 25 min vs 2h" — anecdote de démonstration, pas un benchmark.

## Lecture critique pour le livre

1. **Le guide pense le dev individuel, jamais l'organisation.** Zéro mot sur : conformité, traçabilité, délégation d'identité, CSE, responsabilité. Même angle mort que le [malleable software](./logiciel-malleable-jetable.md) : la littérature praticienne 2026 outille l'individu et laisse la gouvernance vide. Le BYOIA reste le versant organisationnel manquant.
2. **"Trust but verify" en 3 couches** (review cross-modèle, vérification fonctionnelle réelle, validation humaine sur les choix) : la couche 1 — *"biais différents = bugs attrapés qu'aucun ne trouverait seul"* — est exactement la décorrélation des angles morts de [responsabilité du pilote et diversité des harnais](../01-concepts/responsabilite-pilote-diversite-harnais.md), formulée indépendamment par les praticiens. Confirmation de terrain à citer au ch. 5.
3. **La "règle d'or de la délégation"** (*"vous ne pouvez déléguer à un agent que ce que vous sauriez déjà décrire à un humain"*) et le malentendu fondamental (*"plus d'autonomie = plus de cadrage en amont"*) : argument utile contre le fantasme low-code "l'IA fait ce que je veux sans formalisation" — rejoint [destin du low-code](../04-objections/destin-low-code-no-code.md).
4. **La hiérarchie de skills** (universels / équipe / personnels) est un [cycle de promotion](../01-concepts/cycle-promotion-specifique.md) implicite, lu de bas en haut : le skill personnel qui prouve sa valeur devient skill équipe. Le guide constate la hiérarchie sans penser le *mécanisme* de promotion (qui valide, qui maintient, qui répond) — c'est précisément ce que le livre ajoute.
5. **Validation humaine "sur le POURQUOI, pas le COMMENT"** (lire le plan, pas le diff) : formulation praticienne du problème du rubber-stamping du ch. 8 — mais le guide n'en voit pas le risque juridique (art. 26 AI Act), seulement le risque qualité.
6. Le guide confirme que le **développeur-harnais** ([équipe agile interne](../01-concepts/equipe-agile-developpeur-harnais.md)) est déjà l'état de l'art côté outillage : sub-agents natifs, orchestrateurs locaux, agents cloud asynchrones (3 tiers). Ce qui reste spéculatif dans le livre n'est pas l'outillage — c'est l'insertion organisationnelle.
7. Les slogans du guide sont du matériau citable comme croyances populaires dans le [constat des manquements avant la proposition](../02-arguments/06-constat-manquements-avant-proposition.md).

## Sources

- PDF source : "Coder avec l'IA — Guide pratique" (upload Kevin, 2026-07-15, ⚠ auteur non identifié)
- [GitHub — garrytan/gstack](https://github.com/garrytan/gstack)
- [Augment Code — Garry Tan open-sources gstack](https://www.augmentcode.com/learn/garry-tan-open-sources-gstack-claude-code)
- [Conductor](https://www.conductor.build/)
- [Anthropic — Donating MCP / Agentic AI Foundation](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation)
- [Linux Foundation — Formation of the AAIF](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation)
- [MCP Blog — MCP joins the Agentic AI Foundation](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/)
