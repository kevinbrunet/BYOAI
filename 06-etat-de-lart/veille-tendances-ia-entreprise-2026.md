# Veille — Tendances IA en entreprise (juillet 2026) vs. thèses du manuscrit

Note de veille, pas un chapitre. Objectif : confronter les 16 chapitres du manuscrit (07-manuscrit) aux tendances IA entreprise des derniers mois. Marqueurs de confiance appliqués à chaque donnée : ✓ présent avec confiance raisonnable, ~ approximatif/à vérifier, ⚠ incertain ou à ne pas citer sans revérification. Sources en fin de document.

---

## 1. Concepts en résonance forte

### 1.1 Le Shadow AI n'est plus un frémissement, c'est le paysage de référence
Le ch. 3 s'appuyait sur le Work Trend Index 2024 (~78 % des utilisateurs d'IA apportent leurs outils). La veille 2026 confirme et durcit le constat : ~ 65-80 % des organisations rapportent un usage modéré à généralisé de Shadow AI, et ~ seulement 25 % ont une visibilité complète dessus. Le nombre d'agents actifs dans l'écosystème Microsoft 365 aurait été multiplié par ~ 15 en un an. Le diagnostic du ch. 3 ("la gouvernance n'a pas suivi l'adoption") est repris presque mot pour mot dans la presse spécialisée 2026 ("visibility accelerated adoption, but governance did not move at the same speed").

### 1.2 Le trou d'identité des agents — validation quasi littérale du ch. 8
C'est la résonance la plus frappante. Le ch. 8 diagnostique l'anti-pattern de l'impersonation (donner à l'agent le jeton nu de l'utilisateur) comme la faute la plus commune, et bâtit toute son architecture (mTLS + échange de jeton + claim `act`) pour l'éviter. La veille 2026 documente exactement ce trou, non résolu, à l'échelle du marché : ~ seulement 18 % des RSSI se disent confiants dans la capacité de leurs systèmes d'identité à gérer des identités d'agents, et les équipes "partagent des identifiants humains avec les agents faute d'alternative". Le "gap d'identité" est cité comme *la* raison pour laquelle les agents restent bloqués en pilote. Le ch. 8 ne décrit pas un problème résolu ailleurs qu'on tarderait à adopter — il décrit le problème non résolu du moment.

### 1.3 MCP comme standard émergent — confirme l'architecture "socle par API"
Le Model Context Protocol s'impose en 2026 comme le connecteur de fait entre agents et systèmes d'entreprise, avec gouvernance, permissions et audit trail présentés comme "first-class concepts". C'est très exactement la logique du ch. 7 (exposer données et règles par API stable) et du ch. 10 (gateway comme point de passage unique) — le marché construit, sous un autre nom, la brique que le livre appelle "le socle".

### 1.4 Le tampon humain (rubber-stamping) — la faille du ch. 9 est devenue un sujet de fond 2026
Le ch. 9 nomme lui-même sa propre limite : "le régime humain-uniquement est nécessaire, pas suffisant" face au risque de validation vide. La littérature 2026 ("Human Override Theater", "The Rubber Stamp Problem") développe indépendamment la même critique, avec la même formule presque : la supervision humaine devient une fiction qui sert à distribuer la responsabilité plutôt qu'à filtrer les erreurs. Le livre a l'avantage d'avoir anticipé la critique et d'y répondre par la ré-authentification à l'acte — un point différenciant à valoriser.

### 1.5 Le platform engineering et les golden paths sont devenus mainstream
Le ch. 11 s'appuie sur les golden paths pour construire le cycle de promotion. En 2026, ~ 80 % des organisations d'ingénierie logicielle auraient une équipe plateforme (prévision Gartner), et le principe "l'adoption volontaire bat l'imposition" est confirmé par les chiffres cités (>80 % d'adoption volontaire avec golden paths bien conçus, <20 % sans). Convergence forte avec la thèse du ch. 11 ("la plateforme choisie bat la plateforme décrétée").

### 1.6 "Governed enablement" plutôt que blocage — confirme le rejet des six stratégies du ch. 3
La tendance 2026 identifie les organisations matures comme celles qui remplacent interdiction/surveillance par un chemin sanctionné et gouverné — exactement la troisième voie que le ch. 3 appelle "la case vide" (ni interdire, ni surveiller seul, ni laisser faire).

### 1.7 La décorrélation appliquée en production, presque littéralement
Le ch. 5 (aucun harnais n'est parfait, la parade est un regard décorrélé) et le ch. 13 (diversité comme défense de population, "cent copies du même juge") trouvent un écho concret : des systèmes de sécurité agentique 2026 utilisent explicitement des ensembles de modèles différents (un raisonneur, un "debater" économique, un contre-pouvoir indépendant) où le désaccord entre modèles sert de signal de confiance — c'est la mécanique du ch. 5 implémentée telle quelle par un éditeur de sécurité.

### 1.8 Le report de l'AI Act "emploi" à décembre 2027 — confirmé et précisé
Le ch. 14 pose ce report avec un marqueur ⚠ (encore provisoire à la date d'écriture) et une incohérence à trancher ("dix-sept mois" vs 16 mois de report). La veille 2026 confirme : le report est désormais **définitif et contraignant**, adopté par le Parlement (16 juin) et le Conseil (29 juin), publié au Journal officiel. Le manuscrit peut lever son propre marqueur ⚠ sur ce point — mais l'incohérence de calendrier (dix-sept vs seize mois) reste à corriger.

### 1.9 Le problème du pipeline junior — confirmé indépendamment de la note Trésor
Le ch. 13 s'appuie sur une note Trésor-Éco pour établir le risque sur les juniors. La veille 2026 confirme par une autre voie : ~ baisse de 60 % des offres entry-level depuis 2022, chômage des jeunes diplômés en informatique à ~ 6-7 %. Et le réencadrement proposé par le marché — "les juniors doivent apprendre à superviser et valider l'IA plutôt qu'à écrire du code simple" — est exactement le compagnonnage que le ch. 13 propose comme réponse (prédiction 6 du ch. 16).

### 1.10 Le low-code s'estompe dans l'IA-native — confirme la critique du plafond low-code (ch. 4)
Le marché documente en 2026 un flou volontaire entre "low-code" et "développement assisté par IA", et surtout l'argument même du ch. 4 : "rester natif pour éviter la maintenance" s'affaiblit à mesure que l'IA comprend et corrige du code sur mesure plus vite qu'elle ne navigue la documentation d'une plateforme propriétaire. C'est la thèse du ch. 4 dans le vocabulaire du marché.

---

## 2. Concepts en tension ou en opposition

### 2.1 ⚠ Le pilier empirique du ch. 4 a été partiellement rétracté par ses propres auteurs — point critique à traiter avant publication
Le ch. 4 s'appuie sur l'étude METR 2025 (−19 % de vitesse sur dépôts mûrs, écart de perception de 40 points) comme preuve centrale que l'IA ralentit les experts sur du code partagé et durable. La veille 2026 révèle que **METR a publié une révision en février 2026** : la méthodologie originale souffrait d'un biais de sélection sérieux — 30 à 50 % des développeurs invités ont refusé de participer à la condition "sans IA", y compris contre rémunération, ce qui suggère que les développeurs qui bénéficient le plus de l'IA étaient sous-représentés dans l'échantillon "avec IA". Sur une cohorte élargie (~800 tâches, 57 développeurs), le nouveau résultat est de **−4 %, avec un intervalle de confiance de −15 % à +9 %** — statistiquement indiscernable de zéro. Le manuscrit qualifie déjà METR d'étude "historique" (note du ch. 4, à mettre en note finale) mais ne mentionne nulle part cette révision de février 2026. Comme le −19 % est l'exhibit A du chapitre le plus cité du livre pour la thèse "la variable qui sépare les deux mondes", c'est plus qu'une nuance : c'est une fragilisation du chiffre le plus dur du chapitre 4. À traiter avant publication — soit en intégrant la révision et en modérant la formulation, soit en gardant le chiffre original mais en signalant honnêtement la controverse (ce qui est cohérent avec l'éthique de sourcing déjà pratiquée ailleurs dans le manuscrit).

### 2.2 La tendance CIO 2026 pousse vers la "cohérence de plateforme", pas vers la diversité délibérée
Le ch. 13 défend la diversité des harnais comme défense de population contre la monoculture. Le discours dominant des CIO en 2026 va dans le sens inverse : l'absence de "plateforme IA unifiée" est présentée comme *le* risque structurel de 2026 ("architectural fragmentation", "unclear accountability"), et la recommandation est de construire une architecture cohérente — même si celle-ci reste multi-modèles en interne. La nuance sauve en partie le livre (les sources elles-mêmes déconseillent le lock-in sur un seul fournisseur), mais le vocabulaire et la préoccupation numéro un du marché ("coherence") s'opposent frontalement à l'argument central du ch. 13 selon lequel c'est l'uniformité, et non la fragmentation, qui est le risque systémique. Point de friction rhétorique à anticiper face à un lecteur CIO.

### 2.3 La recherche 2026 nuance sérieusement le mécanisme de décorrélation du ch. 5
Le ch. 5 affirme que multiplier les agents ne multiplie pas les points de vue *sauf* si les modèles sont réellement différents — et que le désaccord entre modèles décorrélés est un signal fiable. Une partie de la recherche multi-agents 2026 va plus loin que ce que le livre anticipe : même avec des agents véritablement différents, la "pression majoritaire supprime la correction indépendante" — les agents ont tendance à converger vers le consensus plutôt qu'à se contredire utilement, et ce que la structure de discussion elle-même (ordre de parole, visibilité de la confiance) compte peu face à cet effet de conformité. Ce n'est pas une contradiction frontale du ch. 5 — le livre a déjà anticipé la sycophancie des consensus en note (multi-agents-agregation) — mais c'est un signal que le "regard décorrélé" est plus fragile à opérationnaliser que ne le suggère la formule "cent copies du même juge votent comme un seul juge" : même des juges différents peuvent s'aligner sous pression sociale simulée.

### 2.4 Le vocabulaire du marché brouille la distinction nette low-code / code pur du ch. 4
Le ch. 4 construit une frontière nette entre le low-code (plafonné, captif) et la génération de code pur (sans plafond). Gartner et les analystes 2026 comptent désormais le développement assisté par IA *dans* la catégorie "low-code/no-code" (prévision reprise : 75 % des nouvelles applications d'entreprise "low-code/no-code" d'ici 2026, IA comprise). Le marché ne tranche pas la distinction du livre — il la dissout. Ce n'est pas un désaccord de fond, mais un risque de confusion terminologique dont le manuscrit devrait avoir conscience s'il cite des statistiques de marché sur le "low-code" : certaines incluent déjà ce que le livre appelle le code pur.

### 2.5 L'écart intention/production reste massif, y compris pour les initiatives officielles
Le ch. 11 attribue le blocage au stade pilote à l'absence de chemin de promotion outillé — un problème d'architecture. La veille 2026 montre un écart adoption/déploiement bien plus large qu'attendu même dans les initiatives *sanctionnées* : ~ seulement 17 % des organisations ont des agents pleinement déployés, avec un écart de ~ 68 points entre l'intention et la production. Cela peut se lire comme une confirmation du ch. 11 (pas de cycle = blocage), mais aussi comme un signal que la friction est plus organisationnelle et culturelle que ce que l'architecture seule peut résoudre — une nuance à intégrer si le livre veut éviter de sous-estimer le "chantier en années" qu'il annonce déjà au ch. 6 (mandat Bezos).

### 2.6 La confiance des développeurs dans l'IA se dégrade malgré l'usage croissant
Un signal faible mais notable : l'adoption des outils IA par les développeurs atteint des records (~84 % en 2025) alors que le sentiment positif recule (de ~70 % à ~60 %) et la confiance chute (de ~43 % à ~33 %). Le livre suppose implicitement qu'une architecture de confiance (frontière fiduciaire, délégation typée, verrous) restaure la confiance des utilisateurs. Rien dans la veille ne contredit ce pari, mais l'érosion actuelle du sentiment — malgré une adoption record — suggère que le problème de confiance est aussi émotionnel et culturel, pas seulement architectural. Un angle que le ch. 13 (métier augmenté) ou le ch. 16 pourrait reconnaître explicitement.

---

## 3. Synthèse

Le manuscrit est, dans l'ensemble, en avance sur son époque plutôt qu'en retard : la quasi-totalité de son diagnostic (Shadow AI massif, trou d'identité des agents, tampon humain, golden paths, décorrélation, pipeline junior, report AI Act) est confirmée, souvent presque mot pour mot, par la veille de ces derniers mois — ce qui est une bonne nouvelle pour la crédibilité du livre à sa sortie. Le point le plus urgent à traiter n'est pas une tendance qui contredit la thèse, mais une donnée du livre lui-même devenue fragile : la révision METR de février 2026 touche directement le chiffre le plus cité du chapitre 4. Les autres tensions (cohérence de plateforme vs diversité, conformité des agents sous pression, flou low-code/IA) sont des nuances à intégrer plutôt que des réfutations — elles renforcent l'intérêt d'une clause de falsifiabilité déjà présente au ch. 16.

---

## Sources (juillet 2026)

- [20 Shadow AI Statistics 2024–2026](https://technologyradius.com/statistic/shadow-ai-statistics-2024-2026)
- [Shadow AI stats for 2026 — Optro](https://optro.ai/blog/shadow-ai-stats)
- [Enterprise AI Governance 2026 — MarkTechPost](https://www.marktechpost.com/2026/05/13/enterprise-ai-governance-in-2026-why-the-tools-employees-use-are-ahead-of-the-policies-that-cover-them/)
- [The state of MCP 2026](https://truthifi.com/education/state-of-mcp-2026-ai-agents-custom-connectors)
- [Why Model Context Protocol is on every executive agenda — CIO](https://www.cio.com/article/4136548/why-model-context-protocol-is-suddenly-on-every-executive-agenda.html)
- [The AI Agent Identity Crisis: A 2026 Guide — Strata](https://www.strata.io/blog/agentic-identity/the-ai-agent-identity-crisis-new-research-reveals-a-governance-gap/)
- [AI and Identity in 2026 — SANS Institute](https://www.sans.org/webcasts/ai-identity-2026-defenders-field-guide-agents-copilot-governance)
- [The Rubber Stamp Problem — René Bulsing](https://rbulsing.medium.com/the-rubber-stamp-problem-how-ai-outpaces-the-oversight-it-promises-ff8372752673)
- [Human Override Theater Is the Next HR AI Audit Risk](https://digidai.github.io/2026/04/26/human-override-theater-hr-ai-audit-risk/)
- [Rubber Stamp Risk — Cybermaniacs](https://cybermaniacs.com/cm-blog/rubber-stamp-risk-why-human-oversight-can-become-false-confidence)
- [Platform Engineering in 2026 — DEV Community](https://dev.to/meena_nukala/platform-engineering-in-2026-the-numbers-behind-the-boom-and-why-its-transforming-devops-381l)
- [Platform Engineering in 2026 — Java Code Geeks](https://www.javacodegeeks.com/2026/05/platform-engineering-in-2026-what-it-actually-is-why-its-not-just-devops-renamed-and-how-to-build-an-internal-developer-platform.html)
- [AI Coding Productivity Myth: 19% Slower, Feeling 20% Faster](https://byteiota.com/ai-coding-productivity-myth-19-slower-feeling-20-faster/)
- [METR's AI productivity study is really good — Sean Goedecke](https://www.seangoedecke.com/impact-of-ai-study/)
- [The AI Productivity Paradox — DEV Community](https://dev.to/increase123/the-ai-productivity-paradox-why-developers-are-19-slower-and-what-this-means-for-2026-a14)
- [The Death of Entry-Level IT Jobs? — Joberty](https://www.joberty.com/blog/ai-entry-level-it-jobs-2026/)
- [AI vs Gen Z — Stack Overflow Blog](https://stackoverflow.blog/2025/12/26/ai-vs-gen-z/)
- [The Digital AI Omnibus — DLA Piper](https://knowledge.dlapiper.com/dlapiperknowledge/globalemploymentlatestdevelopments/2026/The-Digital-AI-Omnibus-Proposed-deferral-of-high-risk-AI-obligations-under-the-AI-Act)
- [EU AI Act Omnibus Agreement — Gibson Dunn](https://www.gibsondunn.com/eu-ai-act-omnibus-agreement-postponed-high-risk-deadlines-and-other-key-changes/)
- [EU AI Act Enforcement Is Here — Tech Times](https://www.techtimes.com/articles/320101/20260710/eu-ai-act-enforcement-here-chatbot-rules-live-high-risk-ai-delay-now-binding-law.htm)
- [Low-Code/No-Code Platforms in the AI Era — Medium](https://medium.com/@dinesh_vijay/low-code-no-code-platforms-in-the-ai-era-evolve-or-be-disrupted-be3b3947529e)
- [No Code Is Dead — The New Stack](https://thenewstack.io/no-code-is-dead/)
- [Enterprise Agentic AI Landscape 2026 — Kai Waehner](https://www.kai-waehner.de/blog/2026/04/06/enterprise-agentic-ai-landscape-2026-trust-flexibility-and-vendor-lock-in/)
- [Defense at AI speed — Microsoft Security Blog](https://www.microsoft.com/en-us/security/blog/2026/05/12/defense-at-ai-speed-microsofts-new-multi-model-agentic-security-system-tops-leading-industry-benchmark/)
- [An Outlook on the Opportunities and Challenges of Multi-Agent AI Systems (arXiv)](https://arxiv.org/pdf/2505.18397)
- [AI Agent Orchestration Goes Enterprise — FifthRow](https://www.fifthrow.com/blog/ai-agent-orchestration-goes-enterprise-the-april-2026-playbook-for-systematic-innovation-risk-and-value-at-scale)
