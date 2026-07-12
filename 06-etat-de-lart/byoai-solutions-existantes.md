# État de l'art — Les solutions existantes face au BYOAI (recherche web, juillet 2026)

Panorama des réponses du marché au phénomène BYOAI/Shadow AI, classées par stratégie. Complète [byoai-shadow-ai-marche](./byoai-shadow-ai-marche.md) (le phénomène) et [gateways-securisation-llm](../03-exemples/gateways-securisation-llm.md) (le comparatif détaillé des gateways).

## L'ampleur du problème (chiffres du marché)

- ~ Plus de 80 % des employés utiliseraient des outils IA non approuvés ; 665 applications GenAI distinctes tracées en moyenne dans les environnements d'entreprise ; ~223 violations de politique de données liées à l'IA par mois pour l'entreprise moyenne (sources vendeurs/CSA — ordres de grandeur plausibles, chiffres exacts à ne pas citer sans vérification).

## Stratégie 1 — Interdire (l'échec documenté)

Blocage des domaines IA par le proxy web classique. Constat unanime du marché : contourné massivement (comptes personnels, mobile, extensions navigateur, IA embarquée dans les SaaS déjà autorisés). C'est le régime qui produit le Shadow AI au lieu de l'empêcher. Plus personne ne le recommande seul — même les vendeurs de blocage vendent maintenant de la "visibilité".

## Stratégie 2 — Détecter et surveiller (Shadow AI discovery)

Le segment le plus actif. Grands acteurs réseau/SSE et spécialistes :

- ✓ **Netskope** : gouvernance IA via plateforme SSE, CASB, DLP, "AI guardrails", couverture des interactions agentiques.
- ✓ **Zscaler AI Protect** : visibilité GenAI, SaaS à IA embarquée, environnements de dev — limite reconnue : contrôle surtout les flux navigateur/proxy, pas les apps desktop natives ni les agents autonomes.
- ✓ **Palo Alto Networks** : Prisma AIRS + acquisition Protect AI + AI Access Security ; ~ couverture annoncée de 6 000+ applications GenAI.
- ✓ Spécialistes : LayerX (extension navigateur), WitnessAI, Aurascape, Harmonic, CloudEagle…
- ✓ Limite structurelle documentée (CSA) : l'inspection CASB/réseau rate les extensions, l'IA embarquée dans les SaaS, les comptes personnels sur postes gérés, les agents sur frameworks type LangChain.

**Lecture** : tout ce segment traite le salarié comme une menace à surveiller — et bute juridiquement en France sur la [proportionnalité de la surveillance](../04-objections/byoia-pas-plus-sur-juridiquement.md) (inspection du contenu produit par le salarié).

## Stratégie 3 — Canaliser (gateways et anonymisation)

Faire passer les flux IA par un point de contrôle qui filtre, anonymise, trace :

- ✓ Gateways LLM : Bifrost, Portkey, LiteLLM, Cloudflare AI Gateway, Kong AI Gateway — comparatif détaillé dans [gateways-securisation-llm](../03-exemples/gateways-securisation-llm.md). Thèse déjà publiée de la série : cette infrastructure est "déjà payée" par le marché des chatbots de production.
- ✓ Anonymisation : Presidio (Microsoft, open source) et équivalents — voir [presidio](../01-concepts/presidio-anonymisation-technique.md).
- C'est la brique technique la plus proche du BYOIA — mais vendue comme tuyauterie de sécurité, jamais comme architecture du SI.

## Stratégie 4 — Fournir l'alternative officielle

Donner un outil "béni" pour assécher le besoin : Microsoft 365 Copilot, ChatGPT Enterprise, Claude for Work, Gemini for Workspace. C'est la réponse majoritaire des grandes entreprises.

**Limite pour la thèse du livre** : l'outil béni est générique par construction — il reproduit le [consensus mou](../01-concepts/generique-vs-specifique.md) au niveau IA. Le Work Trend Index montre que les salariés apportent leur IA *malgré* la présence d'outils officiels : le besoin est le spécifique, pas l'IA en soi.

## Stratégie 5 — Encadrer la production dans une plateforme

Gouverner non pas l'usage de l'IA mais ce que les salariés *construisent* avec : Power Platform + environnements ([méthodologies grandes entreprises](./methodologies-grandes-entreprises.md)), Retool, Databricks, ServiceNow Delegated Development. Gouvernance réelle, captivité maximale — le [plafond low-code](../04-objections/destin-low-code-no-code.md) en héritage.

## Stratégie 6 — Gouverner par framework

- ✓ **ISO/IEC 42001** (système de management de l'IA, premier standard international) — de plus en plus exigé dans les due diligences achats.
- ✓ **NIST AI RMF** — volontaire mais devenu référence de facto (marchés fédéraux US, due diligence).
- ✓ **EU AI Act** (règlement 2024/1689) — le seul contraignant ; volet CSE/travailleurs détaillé dans [jurisprudence-cse-ia-2026](./jurisprudence-cse-ia-2026.md).
- ✓ **BYOAI-Gov™** (académique) : zonage de risque par tâche + maturité.
- Constat des analystes : les organisations combinent les trois premiers avec un seul jeu de processus.

## La case vide — où se loge le BYOIA

Cartographie des six stratégies : interdire (échoué), surveiller (le salarié comme menace), canaliser (tuyauterie sans doctrine), fournir (le générique reconduit), enfermer (la plateforme propriétaire), certifier (le processus sans l'architecture). **Aucune ne répond à la question : comment architecturer le SI lui-même — API, frontière fiduciaire, cycle de promotion — pour que l'IA apportée produise du spécifique gouverné ?** Toutes traitent l'IA comme un flux à contrôler ou un produit à distribuer ; aucune ne repense ce que le SI expose et garantit. C'est l'espace du livre, et cette cartographie peut en être un chapitre ("ce que le marché propose, et pourquoi ça ne suffit pas").

## Sources

- [Aurascape — The AI Security Landscape in 2026](https://aurascape.ai/answers/ai-security-landscape-2026/)
- [CSA — Shadow AI Apps](https://labs.cloudsecurityalliance.org/research/csa-research-note-shadow-ai-apps-enterprise-20260530-csa-sty/)
- [Vectra — Shadow AI explained](https://www.vectra.ai/topics/shadow-ai)
- [Palo Alto — What Is Shadow AI](https://www.paloaltonetworks.com/cyberpedia/what-is-shadow-ai)
- [TrueFoundry — Shadow AI Detection Tools 2026](https://www.truefoundry.com/blog/shadow-ai-detection-tools)
- [WitnessAI — Zscaler alternatives AI governance](https://witness.ai/blog/best-zscaler-alternatives-ai-security-governance/)
- [Trustible — AI Governance Frameworks Compared](https://trustible.ai/post/ai-governance-frameworks-compared/)
- [Vanta — NIST AI RMF vs ISO 42001](https://www.vanta.com/collection/iso-42001/nist-ai-rmf-and-iso-42001)
- [GAICC — EU AI Act vs NIST vs ISO 42001](https://gaicc.org/blog/ai-governance-comparison-eu-ai-act-nist-iso-42001/)
