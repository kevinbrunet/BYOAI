# Grille périmètre / risques — la méthode appliquée à chaque étage (2026-07-15)

Généralisation du [constat des manquements avant la proposition](../02-arguments/06-constat-manquements-avant-proposition.md) : la structure croyance → périmètre → manquement → proposition ne vaut pas que pour l'ouverture du livre — elle s'applique **à chaque chapitre**. Et elle est à double sens :

1. **Sens aller (la croyance d'en face)** : citer la croyance populaire que le chapitre affronte, puis établir son périmètre — *vrai sur ça et ça, mais pas ça ; faux sur ça et ça, mais pas ça*. Jamais de réfutation en bloc : une croyance populaire est toujours partiellement vraie, c'est pour ça qu'elle circule.
2. **Sens retour (l'auto-critique)** : pour la facette BYOIA que le chapitre propose, énoncer le **risque associé à la pensée BYOIA elle-même** et sa **mitigation**. Le livre qui ne fait que critiquer les croyances des autres devient un manifeste ; celui qui borne ses propres affirmations devient une doctrine.

## Stratégie d'insertion — décision à prendre

Trois options, une recommandée :

- **Option A (recommandée) — rituel intégré à chaque chapitre** : la croyance citée en exergue d'ouverture ; une section fermante normalisée « Périmètre et risques » (4 blocs : vrai sur / faux sur / risque BYOIA / mitigation) avant les notes. Additive — rien du texte existant n'est perdu, remaniement léger, et le rituel devient une signature de lecture (le lecteur DSI sait qu'il trouvera l'auto-critique en fin de chapitre, ce qui crédibilise tout le reste).
- **Option B — interludes** : pages courtes insérées entre les chapitres. Plus visible, mais double la table des matières (16 → ~30 entrées) et devient mécanique à la lecture continue.
- **Option C — chapitre unique « risques et limites »** : contredit frontalement le « à chaque étage » — rejeté.

⚠ Règle de sécurité quel que soit le choix : **commit git avant chaque remaniement de chapitre**, un chapitre par commit — c'est la garantie « rien perdre ».

## La grille, chapitre par chapitre

Format : **Croyance citée** (avec marqueur d'attribution) → **Vrai sur / Faux sur** → **Risque BYOIA** → **Mitigation** → **Matériau existant** (ce que le manuscrit contient déjà — à déplacer/renforcer, pas à réécrire).

### Ch. 1 — Le logiciel qu'on ne peut pas quitter

- **Croyance** : ⚠ « Les utilisateurs résistent au changement » — proverbe managérial sans auteur, à citer comme tel (c'est sa force : tout le monde l'a entendu en comité).
- **Vrai sur** : l'existence de la résistance ; le coût réel d'apprentissage d'un nouvel outil.
- **Faux sur** : sa cause — ce n'est pas de l'irrationalité, c'est un calcul juste (le chapitre le démontre) ; et sur sa cible — on résiste au générique imposé, pas au changement.
- **Risque BYOIA** : romantiser le contournement — si toute colle humaine est légitime, tout Shadow IT l'est ; le ch. 1 lu seul autorise n'importe quoi.
- **Mitigation** : renvoi explicite vers la frontière (ch. 6) dès la fin du ch. 1 : le contournement est un symptôme à écouter, pas une pratique à bénir.
- **Matériau existant** : le refus de la fausse alternative bloquer/laisser-faire est déjà dans le chapitre — le transformer en bloc « périmètre » formalisé.

### Ch. 2 — Le happy path n'existe pas

- **Croyance** : ~ « Couvrez les 80 % des cas, le reste est marginal » — Pareto appliqué au produit, croyance de product management (pas de citation canonique unique ; citer la règle 80/20 comme doxa).
- **Vrai sur** : la priorisation par fréquence, cas d'usage par cas d'usage pris isolément.
- **Faux sur** : la session composée — 0,9¹⁰ ≈ 35 % ; l'inadaptation est une propriété mathématique de la composition, pas un défaut d'exécution.
- **Risque BYOIA** : le spécifique n'échappe pas au happy path — chaque outil personnel a le sien, construit sur les cas que SON auteur a rencontrés.
- **Mitigation** : c'est exactement le ch. 5 (le happy path de la validation) — annoncer la récursion dès le ch. 2 : « ce théorème s'appliquera aussi à ce que je vous propose ».
- **Matériau existant** : l'annonce « le spécifique naïf ne suffira pas (renvoi ch. 13) » existe — la renforcer en auto-application explicite du théorème.

### Ch. 3 — Le BYOAI est déjà dans vos murs

- **Croyance** : ⚠ « Il suffit d'interdire » / « il suffit de fournir l'outil officiel » — les deux réflexes du marché, citables via les argumentaires des six familles de solutions (vendeurs, pas auteurs).
- **Vrai sur** : l'interdiction réduit l'usage *visible* ; l'outil fourni capte une partie réelle des usages simples.
- **Faux sur** : l'usage *réel* (~78 %) ; et surtout l'inférence « moins visible = moins de risque » — c'est l'inverse.
- **Risque BYOIA** : être lu comme le troisième réflexe symétrique — « laissez faire ». Le laisser-faire est l'échec jumeau de l'interdiction.
- **Mitigation** : la case vide du marché n'est pas « aucune règle », c'est « l'architecture comme règle » — le chapitre doit fermer cette lecture explicitement.
- **Matériau existant** : les six failles sont déjà là ; ajouter le bloc périmètre qui accorde à chaque stratégie sa part de vrai (aucune des six n'est absurde — elles sont incomplètes).

### Ch. 4 — L'économie du code s'est inversée

- **Croyance** : ✓ *« The hottest new programming language is English »* (Karpathy, janv. 2023) ; ✓ *« Everyone is a programmer now »* (Huang, Computex mai 2023) ; ⚠ « 90 % contexte / 10 % modèle » (doctrine praticienne anonyme).
- **Vrai sur** : le coût de *production* (+40-55 %, RCT) ; la barrière d'entrée ; la vitesse sur code neuf/isolé.
- **Faux sur** : le coût de *validation/maintenance* (METR −19 % sur code mûr, GitClear) ; le régime partagé/durable ; et « programmer » confondu avec « répondre de ».
- **Risque BYOIA** : fonder le modèle économique sur un gain surestimé — le trou de données du coût aval (Q5 des [questions restantes](./questions-restantes.md)) est LE talon d'Achille chiffré du livre.
- **Mitigation** (correction Kevin 2026-07-15) : **le harnais lui-même** — le coût qui ne s'effondre pas (validation) est précisément celui que le harnais industrialise ; la chute du ch. 4 (« industrialiser la validation est la seule stratégie rationnelle → ch. 5 ») EST la mitigation, pas un simple enchaînement narratif. En second rang : prédiction falsifiable + protocole de mesure (ch. 16), fenêtre de complexité comme garde-fou budgétaire (ch. 12) pour instrumenter le résiduel.
- **Matériau existant** : le chapitre traite déjà le coût aval de front — il manque les citations d'ouverture (Karpathy/Huang) et le bloc risque-BYOIA explicite.

### Ch. 5 — Aucun harnais n'est parfait

- **Croyance** : ✓ *« Thin harness, fat skills »* (Garry Tan) ; ⚠ « un bon harnais rend l'agent fiable » (doctrine praticienne, ex. guide "Coder avec l'IA" — trust-but-verify réduit à l'outillage).
- **Vrai sur** : l'industrialisation de l'exécution de la validation ; les skills Markdown comme actif durable.
- **Faux sur** : l'idée qu'un harnais se corrige de l'intérieur — juge et partie, Goodhart, tests du même cerveau ; le harnais couvre les déviations *prévues*.
- **Risque BYOIA** : la confiance dans le harnais devient le rubber-stamping de deuxième génération — on ne clique plus « OK » sur le diff, on clique « OK » sur le harnais.
- **Mitigation** (formulation Kevin 2026-07-15) : **la selle** — *« chaque cavalier a sa propre selle ; il n'y a pas de selle idéale, c'est pareil pour l'IA ; donc en tolérer plusieurs, et en avoir une au sein de l'équipe, garante de la cohésion et de la qualité produite par les autres »*. La décorrélation cesse d'être une bonne pratique individuelle et devient un organe : selles personnelles diverses en production, harnais d'équipe en vérification. Détail et tension (monoculture de vérification) : [selle-personnelle-harnais-equipe](../01-concepts/selle-personnelle-harnais-equipe.md). S'y ajoutent désaccord-détecteur et responsabilité au pilote (« le harnais est un outillage, pas un alibi »).
- **Matériau existant** : le chapitre EST déjà l'auto-critique la plus aboutie du livre — il peut servir de gabarit du rituel « périmètre et risques » pour tous les autres. La selle lui donne l'image qui manquait à sa parade.

### Ch. 6 — La frontière fiduciaire

- **Croyance** : ~ « 80 % des produits technologiques seront construits par des non-professionnels de la tech » (prédiction Gartner ~2021 pour 2024, formulation exacte à revérifier) — la doxa citizen developer.
- **Vrai sur** : la capacité individuelle de produire ses outils (l'IA la rend réelle, le low-code l'avait promise).
- **Faux sur** : l'absence de limite — dès que quelqu'un d'autre s'y fie, ce n'est plus un outil personnel ; le low-code est mort précisément d'avoir ignoré cette ligne.
- **Risque BYOIA** : une frontière mal administrée — soit re-centralisation rampante (tout finit « partagé » et on a reconstruit l'ancien monde), soit fuite de responsabilité (rien n'est jamais « partagé » et personne ne répond de rien). Et le trou connu : **l'arbitre humain des cas limites n'est pas défini** (Q11, toujours vide).
- **Mitigation** : le test des 5 questions comme critère mécanique + la nomination explicite de l'arbitre — ce chapitre est l'endroit où fermer Q11, sinon le bloc risques du ch. 6 l'affiche comme chantier assumé.
- **Matériau existant** : le test et ses cas ; manque le régime d'administration de la frontière.

### Ch. 7 — La structure : tout passe par l'API

- **Croyance** : ⚠ *« Ne pas connaître MCP = avoir deux ans de retard »* (discours praticien 2026, guide anonyme — symptôme citable).
- **Vrai sur** : la standardisation de l'accès outillé (MCP à la Linux Foundation, 10K+ serveurs — l'infrastructure est réelle).
- **Faux sur** : brancher ≠ gouverner — un connecteur n'est pas une doctrine d'exposition ; « tout-MCP » sans typage des endpoints reproduit le SI ouvert à tous les vents.
- **Risque BYOIA** : la façade enrichie devient surface d'attaque — l'injection indirecte via le contexte enrichi déclenche des tool calls légitimes (risque résiduel IA-spécifique déjà identifié dans l'architecture).
- **Mitigation** : la gateway (ch. 10) + le typage des endpoints (ch. 9) ; dire explicitement que la façade API *augmente* une surface en même temps qu'elle en ferme une autre.
- **Matériau existant** : l'accès conversationnel et la règle exécutable ; le risque injection n'est probablement pas traité dans ce chapitre — à vérifier à la passe de remaniement.

### Ch. 8 — La délégation : qui agit, pour le compte de qui

- **Croyance** : ⚠ « L'agent agit pour moi » — croyance implicite universelle du discours praticien (le guide "Coder avec l'IA" branche des agents sur tout sans un mot sur l'identité).
- **Vrai sur** : la délégation est techniquement réalisable et vérifiable (claim `act`, intersection des droits).
- **Faux sur** : sans chaîne de délégation typée, « pour moi » est invérifiable — et l'audit le découvrira après l'incident, pas avant.
- **Risque BYOIA** : le coût d'entrée — SPIFFE/Keycloak/sidecars est un stack de grande organisation ; le BYOIA risque d'être une doctrine réservée aux DSI riches, inapplicable en ETI/PME.
- **Mitigation** : la cartographie de maturité (ce qui existe en managé vs à construire) + profils d'adoption gradués ; assumer que la partie III décrit la cible, pas le premier pas.
- **Matériau existant** : les cinq invariants ; ⚠ la re-vérification Kagenti/AuthBridge reste bloquante (hallucination partielle signalée).

### Ch. 9 — Des API interdites à l'IA

- **Croyance** : ~ « Il y a un humain dans la boucle » — la supervision déclarative, art. 14/26 AI Act lus comme cases à cocher (croyance de conformité, citable via les argumentaires fournisseurs).
- **Vrai sur** : l'exigence légale de supervision est réelle et opposable.
- **Faux sur** : un humain qui clique n'est pas une supervision — le rubber-stamping transforme l'exigence en théâtre.
- **Risque BYOIA** : le typage humain-only crée de la friction — et la friction, le livre l'a démontré au ch. 1, fabrique du contournement. Le BYOIA peut recréer chez lui la captivité qu'il dénonce.
- **Mitigation** : l'enrichissement plutôt que la restriction — le chemin conforme doit être le chemin le plus riche (préparation IA maximale en amont du geste humain), sinon le verrou sera contourné comme tous les verrous.
- **Matériau existant** : limites assumées (rubber-stamping, prouver l'humain) déjà dans le chapitre — les reformater en bloc rituel.

### Ch. 10 — La sécurisation est déjà payée

- **Croyance** : ⚠ « L'anonymisation nous protège » / « l'IA locale = souveraineté » (doxa RSSI/achats, sans auteur canonique).
- **Vrai sur** : les gateways et le masquage PII réduisent réellement le risque ; l'infrastructure existe et est mature.
- **Faux sur** : réduction ≠ élimination (la reconstruction en sens inverse) ; le local déplace la question de confiance, il ne la supprime pas.
- **Risque BYOIA** : la fausse assurance — la tuyauterie déployée devient l'alibi qui dispense de la doctrine ; « on a une gateway » comme fin de discussion.
- **Mitigation** : l'ordre des facteurs — doctrine d'abord, tuyauterie ensuite ; les outils présentés comme réduction de risque, jamais comme garantie.
- **Matériau existant** : « pourquoi la tuyauterie sans doctrine ne suffit pas » est déjà la chute du chapitre — c'est déjà le bloc risque, le nommer comme tel.

### Ch. 11 — Le cycle de promotion

- **Croyance** : ⚠ « Il faut standardiser » (a priori, par comité) — et sa jumelle praticienne récente : la hiérarchie de skills (perso/équipe/universel) constatée sans mécanisme (guide "Coder avec l'IA").
- **Vrai sur** : le besoin de convergence est réel — cent outils pour la même tâche est un vrai coût.
- **Faux sur** : le moment (a priori vs a posteriori) et le critère (le consensus vs l'usage mesuré).
- **Risque BYOIA** : la promotion politique — sans seuils définis (Q9, ouverte), l'outil du chef monte et celui du terrain descend ; le cycle dégénère en comité déguisé.
- **Mitigation** : métriques d'usage publiées + descente comme opération de premier ordre + fork libre (tranché) ; les seuils restent un chantier — l'assumer dans le bloc risques.
- **Matériau existant** : complet sur le mécanisme ; le risque de capture politique mérite d'être écrit noir sur blanc.

### Ch. 12 — La fenêtre de complexité

- **Croyance** : ✓ *« Code should be regenerated, not maintained »* (mouvement spec-driven, Codeplain/The New Stack) — le versant « la maintenance disparaît ».
- **Vrai sur** : les artefacts que personne d'autre n'utilise — régénérer y est réellement moins cher que maintenir.
- **Faux sur** : tout ce qui est partagé (la critique de Kirsch : les données d'usage montrent du code produit plus vite *dans* des workflows durables) ; la maintenance ne disparaît pas, elle se déplace vers la spec.
- **Risque BYOIA** : la fenêtre sans unité de mesure reste une image (Q8) — un DSI le verra en une réunion ; piloter avec une métaphore, c'est ne pas piloter.
- **Mitigation** : les proxys proposés (coût de propagation × fréquence de changement, SQALE) + prédiction falsifiable n° 4 ; présenter la fenêtre comme un budget à instrumenter, pas un indicateur sur étagère.
- **Matériau existant** : le chapitre a les proxys ; le bloc risques doit avouer l'absence d'unité native plutôt que la contourner.

### Ch. 13 — Le métier augmenté

- **Croyance** : ✓ *« AI won't take your job. It's somebody using AI that will take your job »* (Richard Baldwin, WEF, mai 2023).
- **Vrai sur** : le déplacement de l'avantage vers celui qui pilote — c'est le constat fondateur du chapitre.
- **Faux sur** : ce que la formule individualise — elle fait de l'adaptation une affaire de survie personnelle et évacue la question d'organisation : pipeline junior, compagnonnage, et le sort de la majorité non autonome (Q17).
- **Risque BYOIA** : creuser l'écart — une organisation à deux vitesses entre salariés-pilotes et salariés-spectateurs ; le BYOIA comme accélérateur d'inégalité interne.
- **Mitigation** : le continuum de délégation (le développeur-harnais comme accès indirect au bénéfice du spécifique) + la question sociale traitée de front (déjà dans le chapitre) + diversité comme politique.
- **Matériau existant** : le plus riche du livre sur ce plan — la citation Baldwin en exergue lui donnerait son adversaire.

### Ch. 14 — Le droit comme allié

- **Croyance** : ✓ « On n'a rien déployé, on ne risque rien » — croyance réelle et datée, démontée par la jurisprudence (~ Nanterre 2026, Paris 2026 — références à vérifier avant publication, déjà flaggé).
- **Vrai sur** : rien — c'est la croyance la plus intégralement fausse du livre, et c'est intéressant de le dire : *mettre à disposition, c'est déployer*.
- **Faux sur** : tout le périmètre, mais préciser ce que la jurisprudence ne dit PAS : elle n'interdit pas le déploiement, elle sanctionne l'absence de consultation — nuance capitale pour la thèse.
- **Risque BYOIA** : l'histoire du projet lui-même — l'hypothèse initiale « BYOIA = plus sûr juridiquement » a été invalidée. Si le livre l'oublie, un juriste le lui rappellera publiquement.
- **Mitigation** : le repositionnement honnête déjà acté (conformité par design, dossier CSE gagnable, pas d'échappatoire) ; raconter l'invalidation de l'hypothèse initiale EST la meilleure preuve d'honnêteté intellectuelle du livre.
- **Matériau existant** : « l'hypothèse fausse démontée » ouvre déjà le chapitre — c'est le seul chapitre qui applique déjà pleinement la méthode ; s'en servir comme second gabarit avec le ch. 5.

### Ch. 15 — Ceux qui en ont déjà fait la moitié

- **Croyance** : ⚠ double croyance symétrique à citer : « personne ne l'a jamais fait » (le scepticisme DSI) et « Shell/Haier prouvent que ça marche » (l'enthousiasme conférence).
- **Vrai sur** : chaque moitié existe, documentée (structure Amazon, gouvernance Shell/Microsoft, organisation Haier).
- **Faux sur** : l'assemblage — personne n'a fait le tout ; les cas cités prouvent la faisabilité des briques, pas du système.
- **Risque BYOIA** : le biais du survivant (Wald) — on cite Shell et Haier, pas les programmes DIY morts en silence dont personne ne publie le post-mortem ; preuves par cas d'usage = preuves par survivants.
- **Mitigation** : l'assumer en une phrase dans le chapitre + le genre position paper (annoncé en intro) + les limites de transposition (Haier/droit français, annexe B).
- **Matériau existant** : « l'assemblage des moitiés est la proposition » — il manque le paragraphe Wald.

### Ch. 16 — Les prédictions falsifiables

- **Croyance** : ⚠ « On verra bien » / « il est trop tôt pour juger » — le scepticisme paresseux, dernier adversaire du livre.
- **Vrai sur** : l'incertitude est réelle — le livre n'a pas de pilote terrain, il l'assume.
- **Faux sur** : l'inaction qu'elle justifie — l'incertitude s'instrumente, elle ne s'attend pas.
- **Risque BYOIA** : le risque terminal — que la thèse elle-même soit infalsifiable (Q2 des questions restantes, toujours ouverte : *quelle observation prouverait que le BYOIA est une mauvaise idée ?*). Sans réponse, les 15 chapitres précédents sont un manifeste.
- **Mitigation** : les six prédictions instrumentées + **proposition : une septième prédiction qui agrège les blocs risques des ch. 1-15** — si les mitigations échouent de façon mesurable (rubber-stamping de harnais généralisé, promotion capturée politiquement, écart à deux vitesses), le BYOIA aura été falsifié. La grille devient l'instrument de falsification de la thèse.
- **Matériau existant** : les six prédictions ; la septième est le débouché naturel de cette grille.

## Ce que la grille révèle en vue d'ensemble

1. **Deux chapitres appliquent déjà la méthode** (ch. 5 mécanique, ch. 14 juridique) — ils servent de gabarits ; le remaniement des autres est une mise au niveau, pas une réinvention.
2. **Les risques BYOIA ne sont pas décoratifs : trois pointent vers des questions encore ouvertes** (arbitre humain Q11 au ch. 6, seuils Q9 au ch. 11, unité de la fenêtre Q8 au ch. 12) et un vers la question bloquante Q2 (thèse falsifiable, ch. 16). La passe « périmètre et risques » force à trancher ou à assumer publiquement — dans les deux cas le livre y gagne.
3. **Un motif traverse tout** : le BYOIA risque à chaque étage de recréer ce qu'il dénonce (friction → contournement au ch. 9, comité déguisé au ch. 11, captivité du harnais au ch. 5, inégalité au ch. 13). Ce motif mérite d'être nommé une fois — probablement dans l'introduction : *la proposition est soumise aux mêmes lois que ce qu'elle remplace ; voici comment on s'en protège.*

## Ordre de remaniement proposé (après validation de la grille)

1. Valider l'option d'insertion (A recommandée) et les croyances citées chapitre par chapitre.
2. Commencer par les ch. 5 et 14 (gabarits — quasi rien à faire, formaliser le rituel).
3. Puis ch. 4, 6, 13 (les croyances vérifiées ✓ sont prêtes ; les enjeux sont les plus lourds).
4. Puis le reste, un chapitre par commit git.
5. Terminer par l'introduction (le motif transversal) et le ch. 16 (la septième prédiction) — ils dépendent de tous les autres.
