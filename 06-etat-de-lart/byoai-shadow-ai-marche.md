# État de l'art — BYOAI, Shadow AI et le marché (recherche web, juillet 2026)

## Le terme existe déjà : BYOAI

Le terme anglophone établi est **BYOAI (Bring Your Own AI)**, extension du concept BYOD. Il est utilisé par la presse RH/tech, les vendeurs de sécurité et la recherche académique. Tranche la question 5 de [questions-livre](../00-meta/questions-livre.md) : "BYOIA" est une francisation d'un terme installé — à assumer explicitement ou à aligner.

- ✓ Un cadre de gouvernance académique existe déjà : **BYOAI-Gov™** (Anthuvan et al., SSRN), modèle "behavior-aware" avec zonage de risque par tâche (Enable / Regulate / Restrict) et échelle de maturité à 4 niveaux — à lire absolument : c'est le concurrent conceptuel direct du livre côté gouvernance.
- ~ Chiffres circulants (sources vendeurs/presse, à re-sourcer vers l'étude primaire — probablement Microsoft Work Trend Index) : 78 % des utilisateurs d'IA apportent leurs propres outils au travail ; 82 % des DSI déclarent que les salariés créent agents et apps plus vite que l'IT ne peut gouverner ; seuls 21 % des salariés ont reçu des consignes IA claires pour leur rôle.

## Vibe coding en entreprise : l'explosion et le gap de gouvernance

- ~ 63 % des utilisateurs d'outils de vibe coding seraient des **non-développeurs** ("State of Vibe Coding 2026", marché estimé à 4,7 Md$) — chiffre vendeur, à vérifier, mais la tendance est corroborée par plusieurs sources.
- ~ 92 % des développeurs US utilisent des outils de codage IA quotidiennement, mais seuls 29 % font confiance au code produit — le "governance gap" est nommé comme LE défi 2026.
- ~ 93 % des dirigeants C-suite se disent préoccupés par la prolifération d'applications non gouvernées construites avec des outils IA (sondage 300+ exécutifs, relayé par Retool).
- ✓ Le discours "2026 : le Shadow IT devient Shadow AI" est devenu un lieu commun du marché (Cloud Security Alliance, LayerX, Retool).
- ✓ Des offres "governed vibe coding" apparaissent : Retool (gouvernance au niveau plateforme), Databricks ("Enabling Governed Vibe Coding for Enterprise Apps") — le marché converge vers le problème que le BYOIA prétend résoudre, mais par la plateforme propriétaire, pas par l'architecture.

## Lecture critique pour la série

1. **Validation massive du diagnostic** : l'adoption sauvage précède la gouvernance, exactement le "piège" décrit dans [byoia.md](../01-concepts/byoia.md).
2. **Le risque de banalisation** : le constat n'est plus original en 2026. La valeur du livre n'est pas dans "le BYOAI arrive" (tout le monde le dit) mais dans la **réponse architecturale** (frontière fiduciaire, cycle de promotion, fenêtre de complexité) — aucune source trouvée ne propose ça.
3. **Le concurrent à traiter** : BYOAI-Gov™ zone les *tâches par risque* ; le BYOIA zone les *artefacts par frontière SI/interface*. Différenciation à écrire noir sur blanc.
4. **La réponse plateforme (Retool, Databricks) est la nouvelle uniformisation** : gouverner le vibe coding en l'enfermant dans un runtime propriétaire = recréer la [captivité](../01-concepts/captivite-logicielle-happy-path-social.md) et le [plafond low-code](../04-objections/destin-low-code-no-code.md) un cran plus haut. Argument offensif fort pour le livre.

## Sources

- [BYOAI-Gov™ (SSRN)](https://papers.ssrn.com/sol3/Delivery.cfm/5394886.pdf?abstractid=5394886&mirid=1&type=2)
- [HR Dive — Rising BYOAI trend](https://www.hrdive.com/news/rising-bring-your-own-ai-trend-can-spell-trouble-for-employers/824319/)
- [Venn — BYOAI risks & best practices](https://www.venn.com/learn/byod/byoai/)
- [LayerX — What is BYOAI](https://layerxsecurity.com/generative-ai/bring-your-own-ai/)
- [Fast Company — BYOAI threat](https://www.fastcompany.com/91399902/byoai-serious-threat-to-your-company)
- [CSA — Shadow AI Apps](https://labs.cloudsecurityalliance.org/research/csa-research-note-shadow-ai-apps-enterprise-20260530-csa-sty/)
- [Retool — State of AI Governance 2026](https://retool.com/blog/ai-governance-report-2026)
- [Keyhole — Vibe Coding Trends 2026](https://keyholesoftware.com/vibe-coding-trends-2026/)
- [Databricks — Governed Vibe Coding](https://www.databricks.com/blog/enabling-governed-vibe-coding-enterprise-apps-databricks)
