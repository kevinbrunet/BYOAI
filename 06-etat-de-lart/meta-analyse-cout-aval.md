# Méta-analyse — Le coût aval du code généré par IA (recherche web, juillet 2026)

Répond à la question 5 de [questions-restantes](../00-meta/questions-restantes.md) (ex-Q7). Croisement de toutes les données publiques trouvées : essais randomisés, télémétrie à grande échelle, rapports sécurité, étude longitudinale. Chaque source est typée — RCT (essai contrôlé, preuve forte), télémétrie (corrélationnel), vendeur (à décoter).

## 1. Ce qui accélère — les gains de production sont réels mais mesurés sur des tâches isolées

- ✓ **RCT laboratoire (Peng et al., 2023, arXiv 2302.06590)** : +55,8 % de vitesse (IC 95 % : 21-89) — mais sur UNE tâche greenfield isolée (serveur HTTP en JS). Bénéfice plus fort pour les développeurs moins expérimentés.
- ✓ **RCT terrain GitHub × Accenture (2024)** : jusqu'à ~55 % plus rapide, 85 % se sentent plus confiants — co-écrit par le vendeur, mesures partiellement déclaratives.
- ~ **ANZ Bank** : +42 % sur six semaines (étude interne).
- **Lecture** : le gain de vitesse de production initiale est le résultat le plus répliqué — sur des tâches courtes, nouvelles, peu dépendantes d'un existant.

## 2. Ce qui ralentit — le résultat contre-intuitif le plus solide

- ✓ **RCT METR (juillet 2025, arXiv 2507.09089)** : 16 développeurs open source expérimentés, 246 tâches réelles sur des repos mûrs (>1 M lignes), méthodologie type essai clinique : **19 % PLUS LENTS avec l'IA** — alors qu'ils s'estimaient 20 % plus rapides après coup. L'écart perception/réalité est le second résultat de l'étude, aussi important que le premier : les développeurs ne sentent pas le ralentissement.
- ✓ METR qualifie depuis le résultat d'"historique" (outils début 2025) — mais aucun RCT contraire sur code mûr n'a été trouvé.
- **Lecture** : le modérateur clé est la **maturité et la familiarité du code**. L'IA accélère le neuf isolé, ralentit l'intervention dans l'existant complexe.

## 3. La qualité à l'échelle — la télémétrie converge vers la dégradation

- ✓ **GitClear (211 M lignes analysées, 2020-2024)** : code dupliqué ×4 à ×8 ; le copié-collé dépasse le code déplacé pour la première fois de l'histoire de leur mesure ; refactoring effondré de 25 % des lignes modifiées (2021) à <10 % (2024) ; churn à 2 semaines passé de 3,1 % à 5,7 %. Le rapport 2026 parle de "maintainability gap".
- ✓ **DORA 2025 (Google, la plus grosse enquête du domaine)** : 90 % d'adoption ; le débit de livraison monte (renversement vs 2024) mais **la stabilité continue de se dégrader**. Conclusion textuelle du rapport : l'IA n'améliore pas une équipe, elle **amplifie** ce qui existe — les équipes avec tests automatisés solides et petits lots absorbent le volume ; les autres accumulent l'instabilité.

## 4. La sécurité — le coût aval le plus documenté

- ✓ **Veracode 2025 (100+ LLM testés, 4 langages)** : ~45 % du code généré contient des vulnérabilités OWASP Top 10 ; ~2,74× plus de vulnérabilités que le code humain ; Java le pire (~72 % d'échec).
- ~ **Apiiro (Fortune 50)** : vulnérabilités CVSS ≥7 ×2,5 ; +322 % de chemins d'escalade de privilèges ; +40 % d'exposition de secrets ; >10 000 findings/mois mi-2025 (×10 vs déc. 2024) ; cycles de revue ×2, corrections post-merge ×3.

## 5. Le long terme — la première étude longitudinale existe

- ✓ **"Debt Behind the AI Boom" (arXiv 2603.28592)** : 302 600 commits vérifiés comme écrits par IA, 6 299 repos GitHub, 5 assistants suivis dans le temps. Résultats : la dette non résolue passe de quelques centaines d'issues début 2025 à **>100 000 issues survivantes en février 2026** ; **22,7 % des problèmes introduits par l'IA sont toujours présents à la dernière révision** ; le type dominant est le code smell — invisible en revue, cumulatif en maintenance.
- ⚠ Estimations circulantes type "coûts ×4 en année 2" ou "+12 % de coût total année 1" : blogs vendeurs, méthodologie non publiée — ne pas citer.

## 6. Synthèse méta-analytique

Le tableau est cohérent d'une source à l'autre, et il n'est PAS "l'IA c'est bien/mal" :

| Contexte | Effet mesuré | Preuve |
|---|---|---|
| Tâche neuve, isolée, courte | +40 à +55 % de vitesse | RCT ×3 |
| Code mûr, partagé, complexe | −19 % (et perception inversée) | RCT |
| Qualité structurelle à l'échelle | duplication ×4-8, refactoring ÷2,5, churn +80 % | télémétrie 211 M lignes |
| Stabilité de livraison | dégradée, amplification des faiblesses | DORA n>30k |
| Sécurité | ~45 % vulnérable, ×2,5-2,7 | tests systématiques + télémétrie |
| Survie de la dette | 22,7 % persiste | longitudinal 302k commits |

**La variable qui sépare les deux régimes est toujours la même : le code est-il neuf et isolé, ou partagé et durable ?**

## 7. Ce que ça change pour la série — la donnée dessine exactement la frontière

1. **L'argument 1 doit être reformulé, pas abandonné** : le coût de *production* s'effondre (prouvé), le coût de *validation et de maintenance* ne s'effondre pas (prouvé aussi). L'économie ne disparaît pas — elle se déplace de la production vers la validation. Dire ça d'emblée immunise le livre contre l'objection.
2. **Les données donnent raison à la frontière fiduciaire, empiriquement** : tous les résultats négatifs (METR, GitClear, DORA, dette survivante) sont mesurés sur du code **partagé et durable** — la couche SI. Tous les résultats positifs sont sur du code **neuf et isolé** — la couche interface. La [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) place le code généré librement exactement dans le régime où il performe, et impose la validation exactement dans le régime où elle manque. Ce n'est plus un principe d'architecture, c'est une lecture des données.
3. **Le coût de promotion est maintenant chiffrable** : revue ×2, tests ×1,7-3 (Apiiro) donnent un ordre de grandeur du "coût de mise au standard" du [cycle de promotion](../01-concepts/cycle-promotion-specifique.md) — le transfert de maintenance a un prix mesuré, pas théorique.
4. **DORA fournit la condition de viabilité** : l'IA amplifie ce qui existe → le BYOIA suppose un SI avec tests, CI et petits lots. À dire honnêtement : une DSI sans ces fondations doit les construire d'abord (écho au coût du mandat Amazon).
5. ⚠ **Le trou dans la littérature** : personne n'a mesuré "régénérer au lieu de maintenir" (le régime jetable). Toutes les études mesurent du code généré *puis maintenu de façon classique*. L'hypothèse jetable/régénérable reste sans données — le livre doit la présenter comme hypothèse à instrumenter (les métriques du cycle de promotion sont précisément l'instrument), pas comme fait établi. C'est aussi une opportunité : le premier qui publie ces données existe pas encore.

## Sources

- [Peng et al. — Impact of AI on Developer Productivity (arXiv 2302.06590)](https://arxiv.org/abs/2302.06590)
- [GitHub × Accenture — Quantifying Copilot's impact in the enterprise](https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-in-the-enterprise-with-accenture/)
- [METR — Measuring the Impact of Early-2025 AI (arXiv 2507.09089)](https://arxiv.org/abs/2507.09089)
- [GitClear — AI Copilot Code Quality 2025](https://www.gitclear.com/ai_assistant_code_quality_2025_research) et [Maintainability Gap 2026](https://www.gitclear.com/the_ai_code_quality_maintainability_gap)
- [DORA — State of AI-assisted Software Development 2025](https://dora.dev/dora-report-2025/)
- [Veracode — 2025 GenAI Code Security Report](https://www.veracode.com/blog/genai-code-security-report/)
- [CSA — Vibe Coding's Security Debt](https://labs.cloudsecurityalliance.org/research/csa-research-note-ai-generated-code-vulnerability-surge-2026/)
- [Debt Behind the AI Boom (arXiv 2603.28592)](https://arxiv.org/abs/2603.28592)
