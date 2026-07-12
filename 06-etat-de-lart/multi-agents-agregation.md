# État de l'art — Agrégation multi-agents (recherche web, juillet 2026)

## Ce que la recherche a produit depuis les notes de la série

- ✓ **Mixture-of-Agents (MoA)** : schéma en couches proposeurs → agrégateur, souvent plus fiable qu'un seul modèle plus fort — confirme la piste "gating" des [architectures de référence](../03-exemples/architectures-agregation-references.md).
- ✓ **Multi-agent debate pour LLM-as-judge** avec détection adaptative de stabilité (NeurIPS 2025) : formalisation mathématique montrant que le débat amplifie la justesse par rapport aux ensembles statiques, avec critère d'arrêt adaptatif.
- ✓ **Limites documentées, directement alignées avec les réserves de la série** : le vote majoritaire échoue quand les agents partagent les mêmes biais ou quand la bonne réponse est minoritaire (= la condition de décorrélation de [Condorcet](../01-concepts/sagesse-des-foules-condorcet.md)) ; le débat peut produire de la **sycophancie** — convergence vers un consensus faux sous pression sociale ; une étude parle d'« illusion délibérative » (attrition factuelle + homogénéisation des positions).
- ✓ Piste nouvelle : sélectionner un **sous-ensemble d'agents maximisant l'information mutuelle** bat le partage de toutes les réponses — écho direct à la pondération du [conseil d'agents](../01-concepts/conseil-agents-ponderation-bayesienne.md).
- ✓ Émergence d'agents **referee/reviewer** qui évaluent les trajectoires de raisonnement des pairs (audit des arbres de raisonnement, qui surpasserait vote majoritaire et LLM-as-judge) — matière directe pour [chef-arbitre vs chef-détecteur](../05-questions-ouvertes/chef-arbitre-vs-detecteur.md) : la recherche penche vers le chef-auditeur, un troisième terme.

## Lecture critique pour la série

1. Les intuitions de la série (décorrélation nécessaire, danger du consensus, chef comme fonction et non comme agent) sont **toutes confirmées** par la littérature 2025-2026 — les fichiers peuvent passer d'hypothèses à synthèse sourcée.
2. La question 4 de [questions-livre](../00-meta/questions-livre.md) reste entière : ce cluster est solide mais son lien avec la thèse BYOIA n'est toujours pas explicité. La recherche le rend publiable — pas forcément dans *ce* livre.

## Sources

- [arXiv — Multi-Agent Debate for LLM Judges (NeurIPS 2025)](https://arxiv.org/pdf/2510.12697)
- [arXiv — Mixture of Complementary Agents](https://arxiv.org/pdf/2605.24048)
- [arXiv — When AIs Judge AIs: Agent-as-a-Judge](https://arxiv.org/pdf/2508.02994)
- [arXiv — Auditing Multi-Agent Reasoning Trees](https://arxiv.org/html/2602.09341v1)
- [arXiv — The Deliberative Illusion](https://arxiv.org/pdf/2606.03032)
- [arXiv — When Does Delegation Beat Majority?](https://arxiv.org/pdf/2606.08098)
