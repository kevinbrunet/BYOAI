# Plan chapitré du livre — v3 (2026-07-12)

Genre : essai de philosophie d'architecture, descente jusqu'aux principes de fonctionnement des protocoles (jamais le code). Lecteur : DSI, CTO, RSSI, DPO, DevSecOps, architectes d'entreprise. Langue : français. Nom du concept : à trouver ("BYOIA" = nom de travail, positionné comme extension du BYOAI). Chaque chapitre indique sa question-lecteur et ses sources. La table de correspondance complète fichiers → chapitres est en fin de document : **chaque fichier de l'ontologie a une destination explicite** (chapitre, annexe, ou hors livre).

**Changement v2 → v3 (décision Kevin, option B)** : création du ch. 5 "Aucun harnais n'est parfait" — la section harnais du ch. 4 migre et devient un chapitre complet (anatomie, pièges classiques, décorrélation). Anciens ch. 5-15 renumérotés 6-16. Répartition diversité : mécanique au ch. 5, organisationnelle au ch. 13. ⚠ Les fiches d'ontologie peuvent encore référencer la numérotation v2 ; en cas de doute, la table ci-dessous fait foi.

## Introduction — Ce que ce livre est, et n'est pas

Le genre annoncé : une proposition d'architecture, pas un retour d'expérience — les preuves sont empruntées (cas tiers documentés, jurisprudence, méta-analyse des données publiques) et ce qui n'a pas de données est formulé en prédiction falsifiable avec son protocole de mesure. Le positionnement : le BYOAI est le phénomène documenté ; ce livre est l'étage au-dessus — ce qu'on construit pour l'accueillir. La thèse en une phrase (à formuler — dernier chantier ouvert) et la promesse au lecteur : en refermant le livre, savoir quoi garder, quoi rendre, quoi exiger, et comment vérifier.
Sources : [questions-restantes — genre et nom](./questions-restantes.md), [nom-byoia-vs-byoai](../05-questions-ouvertes/nom-byoia-vs-byoai.md), [objectif-serie](./objectif-serie.md).

## Partie I — Le constat (pourquoi vos salariés ont déjà tranché)

**Ch. 1 — Le logiciel qu'on ne peut pas quitter.** ✍ RÉDIGÉ — [chapitre-01](../07-manuscrit/chapitre-01.md)
Le test du pire logiciel ; la captivité (Hirschman : ni exit ni voice → contournement) ; la colle humaine (recettes de cuisine, wiki mort, le collègue qui sait) ; le happy path sédimenté ; la résistance au changement comme calcul juste ; la recette de cuisine qui trouve un moteur ; le refus de la fausse alternative bloquer/laisser-faire. *Question-lecteur (DSI) : pourquoi mes utilisateurs détestent-ils mon SI alors qu'il fonctionne ?*
Sources : [captivite-logicielle](../01-concepts/captivite-logicielle-happy-path-social.md).

**Ch. 2 — Le happy path n'existe pas.** ✍ RÉDIGÉ — [chapitre-02](../07-manuscrit/chapitre-02.md)
L'illusion statistique du 20/80 (0,9¹⁰ ≈ 35 %) ; le générique comme implémentation du seul nominal — inadaptation par propriété mathématique, pas par incompétence ; la colle humaine du ch. 1 comme gestion des 65 % ; l'armoire à fibre optique en illustration. Pivot du livre : pourquoi le générique échoue, pourquoi le spécifique est nécessaire — et l'annonce que le spécifique naïf ne suffira pas (renvoi ch. 13). *Question-lecteur (DSI/CTO) : pourquoi chaque refonte reproduit-elle le problème ?*
Sources : [happy-path-illusion-statistique](../01-concepts/happy-path-illusion-statistique.md), [paradoxe-armoire-fibre-optique](../01-concepts/paradoxe-armoire-fibre-optique.md).

**Ch. 3 — Le BYOAI est déjà dans vos murs.** ✍ RÉDIGÉ — [chapitre-03](../07-manuscrit/chapitre-03.md)
Le phénomène documenté (Work Trend Index, ~78 %, Shadow AI) ; l'échec de l'interdiction ; les six réponses du marché (interdire, surveiller, canaliser, fournir, enfermer, certifier) et la faille de chacune ; la case vide : personne n'architecture le SI lui-même. *Question-lecteur (RSSI) : pourquoi mon blocage ne marche-t-il pas, et que vaut ce qu'on me vend ?*
Sources : [byoai-shadow-ai-marche](../06-etat-de-lart/byoai-shadow-ai-marche.md), [byoai-solutions-existantes](../06-etat-de-lart/byoai-solutions-existantes.md).

## Partie II — Le changement de régime (l'économie, l'outillage et la frontière)

**Ch. 4 — L'économie du code s'est inversée — mais pas là où on croit.** ✍ RÉDIGÉ — [chapitre-04](../07-manuscrit/chapitre-04.md)
Pourquoi le logiciel de gestion existe et pourquoi on imposait l'outil ; ce que l'IA effondre exactement : le coût de production (+40-55 %, RCT), pas le coût de validation (METR −19 % sur code mûr, GitClear, DORA, Veracode) ; les deux régimes neuf/isolé vs partagé/durable ; le générique/spécifique revisité ; les 4 premiers arguments reformulés ; pourquoi le low-code n'a pas tenu cette promesse ; l'objection du coût aval traitée de front avec les données. Chute : les études mesurent l'IA-assistant — industrialiser la validation est la seule stratégie rationnelle → ch. 5. *Question-lecteur (DSI) : quel est le vrai coût, où est le vrai gain ?*
Sources : [meta-analyse-cout-aval](../06-etat-de-lart/meta-analyse-cout-aval.md), [frontiere-structure-interface](../01-concepts/frontiere-structure-interface.md), [generique-vs-specifique](../01-concepts/generique-vs-specifique.md), [02-arguments/01-04](../02-arguments/), [deplacement-cout-aval](../04-objections/deplacement-cout-aval.md), [destin-low-code](../04-objections/destin-low-code-no-code.md), [bilan-low-code](../06-etat-de-lart/bilan-low-code-citizen-developer.md).

**Ch. 5 — Aucun harnais n'est parfait.** ✍ RÉDIGÉ — [chapitre-05](../07-manuscrit/chapitre-05.md) *(nouveau, 2026-07-12)*
Le harnais défini (ligne de production autour du générateur : tests co-générés, analyse statique, non-régression, second agent, boucle) ; DORA relu comme variable d'action ; exécution automatisée ≠ jugement (DoD humaine → ch. 6) ; responsabilité au pilote. Puis les pièges structurels, aucun ne se corrigeant de l'intérieur : le happy path de la validation (ch. 2 appliqué au harnais) ; juge et partie (auto-correction sans signal externe — analogie du retour après un mois d'absence : œil neuf, mêmes instincts) ; la boucle qui n'enrichit plus rien (rééchantillonnage des mêmes priors, plateau de corrélation, changement de régime par décorrélation) ; Goodhart dans la boucle (reward hacking documenté — tests codés en dur, METR/system cards) ; les tests du même cerveau (cohérence interne ≠ conformité au besoin) ; la fenêtre qui se dégrade (contexte long). Parade : décorréler — vérificateur hors de portée du producteur, références extérieures, second modèle différent, désaccord-détecteur. Chute double : graine BYOIA (diversité par construction → ch. 13) et nécessité de la frontière (→ ch. 6). *Question-lecteur (CTO/DevSecOps) : puis-je confier la validation à la ligne de production elle-même ?*
Sources : [responsabilite-pilote-diversite-harnais](../01-concepts/responsabilite-pilote-diversite-harnais.md), [taxonomie-angles-morts-empirique](../01-concepts/taxonomie-angles-morts-empirique.md), [multi-agents-agregation](../06-etat-de-lart/multi-agents-agregation.md), [happy-path-illusion-statistique](../01-concepts/happy-path-illusion-statistique.md).

**Ch. 6 — La frontière fiduciaire.** ✍ RÉDIGÉ — [chapitre-06](../07-manuscrit/chapitre-06.md)
Le test des cinq questions ; la compression : si quelqu'un d'autre doit pouvoir s'y fier, c'est le SI ; la lecture écritures/lectures (CQRS) ; le cas RH matin/après-midi ; le cas vécu DSI : Git, DoD, DoR ; le mandat API d'Amazon ; l'objection "l'IA code des deux côtés" tranchée par le critère. *Question-lecteur (tous) : qu'est-ce qui reste à moi, qu'est-ce qui part au collaborateur ?*
Sources : [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md), [arbitrage — tranché](../04-objections/arbitrage-regle-gestion-vs-interface.md), [frontiere-si-ia-genere-code](../04-objections/frontiere-si-ia-genere-code.md), [git-dod-dor-dsi](../03-exemples/git-dod-dor-dsi.md), [amazon-mandat-api](../03-exemples/amazon-mandat-api.md), [05-garanties](../02-arguments/05-garanties-non-negociables.md). *(2026-07-15 : ajout [cicd-processus-comme-un-autre](../03-exemples/cicd-processus-comme-un-autre.md) et [skills-si-vs-skills-personnels](../01-concepts/skills-si-vs-skills-personnels.md) — nouvelle section « le workflow lui-même est un artefact du test ».)*

## Partie III — L'architecture (la descente dans les protocoles)

**Ch. 7 — La structure : tout passe par l'API.** ✍ RÉDIGÉ — [chapitre-07](../07-manuscrit/chapitre-07.md)
L'approche data-centrique en pratique ; les décisions comme events (DCB) ; projections libres ; la règle exécutable — la fin du wiki normatif ; l'économie de contexte ; l'accès conversationnel (Claude Tag en exemple). *Question-lecteur (CTO/architecte) : à quoi ressemble le SI cible ?*
Sources : [approche-datacentrique](../01-concepts/approche-datacentrique.md), [dcb-decisions-comme-events](../01-concepts/dcb-decisions-comme-events.md), [dcb-event-sourcing](../06-etat-de-lart/dcb-event-sourcing.md), [regle-executable-fin-du-wiki](../01-concepts/regle-executable-fin-du-wiki.md), [acces-conversationnel](../01-concepts/acces-conversationnel.md), [claude-tag-slack](../03-exemples/claude-tag-slack.md).

**Ch. 8 — La délégation : qui agit, pour le compte de qui.** ✍ RÉDIGÉ — [chapitre-08](../07-manuscrit/chapitre-08.md)
Les deux couches indépendantes (mTLS/SPIFFE ; JWT) ; le claim `act` et l'intersection sur toute la chaîne ; Biscuit en contraste ; l'infrastructure auth-unaware (sidecar) ; l'état des standards ; Kagenti/AuthBridge ; les cinq invariants. *Question-lecteur (DevSecOps/RSSI) : avec quelles briques, à quelle maturité ?*
Sources : [delegation-agents-jwt-mtls](../01-concepts/delegation-agents-jwt-mtls.md), [identite-agents-standards](../06-etat-de-lart/identite-agents-standards.md), [kagenti-authbridge](../03-exemples/kagenti-authbridge-red-hat.md), [cartographie-maturite-authentification](../05-questions-ouvertes/cartographie-maturite-authentification.md).

**Ch. 9 — Des API interdites à l'IA.** ✍ RÉDIGÉ — [chapitre-09](../07-manuscrit/chapitre-09.md)
Le typage humain/agent ; les trois régimes par endpoint ; "l'IA prépare, l'humain acte" rendu exécutoire ; la supervision humaine AI Act prouvable par les logs ; prouver l'humain (WebAuthn) ; les limites assumées : rubber-stamping. *Question-lecteur (RSSI/DPO) : comment garantir que l'IA n'acte jamais seule ?*
Sources : [delegation-agents-jwt-mtls — section humain/agent](../01-concepts/delegation-agents-jwt-mtls.md), [backlog-posts — post prioritaire](./backlog-posts.md).

**Ch. 10 — La sécurisation est déjà payée.** ✍ RÉDIGÉ — [chapitre-10](../07-manuscrit/chapitre-10.md)
Les gateways LLM ; Presidio et la reconstruction en sens inverse ; l'IA locale ; pourquoi la tuyauterie sans doctrine ne suffit pas. *Question-lecteur (RSSI/DevSecOps) : que déployer, que réutiliser de l'existant ?*
Sources : [gateways-securisation-llm](../03-exemples/gateways-securisation-llm.md), [presidio-anonymisation-technique](../01-concepts/presidio-anonymisation-technique.md), [argument-ia-locale-souverainete](../01-concepts/argument-ia-locale-souverainete.md).

## Partie IV — La gouvernance (le cycle et les humains)

**Ch. 11 — Le cycle de promotion.** ✍ RÉDIGÉ — [chapitre-11](../07-manuscrit/chapitre-11.md)
Utilisateur → équipe → service → entreprise ; contrats de stabilité ; périmètre de considération ; mise au standard chiffrée ; l'uniformisation a posteriori ; fork libre et incitation économique ; la descente comme opération de premier ordre. Précédents : Microsoft, golden paths/Backstage, InnerSource. *Question-lecteur (DSI) : comment ça ne devient pas le chaos ?*
Sources : [cycle-promotion-specifique](../01-concepts/cycle-promotion-specifique.md), [methodologies-grandes-entreprises](../06-etat-de-lart/methodologies-grandes-entreprises.md), [innersource-golden-paths](../06-etat-de-lart/innersource-golden-paths.md).

**Ch. 12 — La fenêtre de complexité.** ✍ RÉDIGÉ — [chapitre-12](../07-manuscrit/chapitre-12.md)
La capacité de maintenance comme budget explicite ; propagation cost × fréquence de changement ; SQALE, charge cognitive ; le signal et les deux leviers ; parenté WIP limits / error budgets. *Question-lecteur (CTO) : comment je pilote, avec quels nombres ?*
Sources : [cycle-promotion-specifique — pilotage](../01-concepts/cycle-promotion-specifique.md), [mesure-complexite-fenetre](../06-etat-de-lart/mesure-complexite-fenetre.md).

**Ch. 13 — Le métier augmenté.** ✍ RÉDIGÉ — [chapitre-13](../07-manuscrit/chapitre-13.md)
Le spécifique naïf réglé de face ; le développeur de terrain ; la question sociale (pipeline junior, compagnonnage) ; le continuum de délégation ; **la diversité comme politique** (monoculture = risque systémique, à partir de la mécanique du ch. 5) ; l'épidémiologiste du backlog ; les rôles et la limite de l'analogie orchestrateur ; Haier teasé. *Question-lecteur (DSI/RH) : qui fait quoi, avec quelles compétences — et qui arbitre ?*
Sources : [equipe-agile-developpeur-harnais](../01-concepts/equipe-agile-developpeur-harnais.md), [epidemiologiste-du-backlog](../01-concepts/epidemiologiste-du-backlog.md), [kubernetes-pods-roles](../03-exemples/kubernetes-pods-roles.md), [limite-analogie-kubernetes](../04-objections/limite-analogie-kubernetes.md), [taxonomie-angles-morts-empirique](../01-concepts/taxonomie-angles-morts-empirique.md), [haier-rendanheyi](../03-exemples/haier-rendanheyi.md), [responsabilite-pilote-diversite-harnais](../01-concepts/responsabilite-pilote-diversite-harnais.md).

**Ch. 14 — Le droit comme allié.** ✍ RÉDIGÉ — [chapitre-14](../07-manuscrit/chapitre-14.md)
L'hypothèse fausse démontée ; la jurisprudence 2025-2026 ; les deux terrains indépendants ; l'AI Act (calendrier omnibus déc. 2027) ; la zone grise du déployeur ; conformité par design ; gagner la consultation CSE. *Question-lecteur (DPO/DSI) : comment je déploie sans me faire suspendre ?*
Sources : [byoia-pas-plus-sur-juridiquement](../04-objections/byoia-pas-plus-sur-juridiquement.md), [cadre-juridique-cse](../01-concepts/cadre-juridique-cse-consultation.md), [jurisprudence-cse-ia-2026](../06-etat-de-lart/jurisprudence-cse-ia-2026.md), [eu-ai-act](../06-etat-de-lart/eu-ai-act.md), [conformite-par-design](../01-concepts/conformite-par-design.md), [distinguo-filtrage-url](../05-questions-ouvertes/distinguo-filtrage-url-inspection-contenu.md).
⚠ Chapitre à faire relire par un avocat en droit social avant publication.

## Partie V — La preuve et l'invitation

**Ch. 15 — Ceux qui en ont déjà fait la moitié.** ✍ RÉDIGÉ — [chapitre-15](../07-manuscrit/chapitre-15.md)
Amazon la structure, Shell/Microsoft la gouvernance du bricolage, Haier l'organisation, le malleable software la vision individuelle ; l'assemblage des moitiés est la proposition du livre. *Question-lecteur (tous) : est-ce que quelqu'un l'a déjà fait ?*
Sources : [amazon-mandat-api](../03-exemples/amazon-mandat-api.md), [methodologies-grandes-entreprises](../06-etat-de-lart/methodologies-grandes-entreprises.md), [haier-rendanheyi](../03-exemples/haier-rendanheyi.md), [positionnement-malleable-software](../01-concepts/positionnement-malleable-software.md), [logiciel-malleable-jetable](../06-etat-de-lart/logiciel-malleable-jetable.md).

**Ch. 16 — Les prédictions falsifiables.** ✍ RÉDIGÉ — [chapitre-16](../07-manuscrit/chapitre-16.md)
Six prédictions instrumentées (jetable/régénérable, écart naïf/harnaché, diversité vs monoculture, fenêtre, convergence des angles morts, compagnonnage) ; la feuille de route lundi/mois/trimestre/année. *Question-lecteur (tous) : par où je commence, et comment je saurai si ça marche ?*
Sources : [questions-restantes — genre](./questions-restantes.md), [meta-analyse — le trou](../06-etat-de-lart/meta-analyse-cout-aval.md), [taxonomie-angles-morts](../01-concepts/taxonomie-angles-morts-empirique.md).

## Annexes

- **Annexe A — Briques et références datées** : gateways, standards (drafts IETF, WIMSE, MCP), outils (Biscuit, Presidio, CodeScene…), études du ch. 5 (Huang et al. ICLR 2024, METR reward hacking 2025, Lost in the Middle), jurisprudences — tout ce qui périme, daté et marqué ✓/~/⚠.
- **Annexe B — Objections résiduelles** : fiabilité des synchronisations écrites par l'IA, limites de transposition (Haier/droit français), rubber-stamping développé.

## Hors livre (explicitement)

- **Cluster multi-agents** — [sagesse-des-foules-condorcet](../01-concepts/sagesse-des-foules-condorcet.md), [conseil-agents-ponderation-bayesienne](../01-concepts/conseil-agents-ponderation-bayesienne.md), [architectures-agregation](../03-exemples/architectures-agregation-references.md), [moussaid](../03-exemples/moussaid-a-t-on-besoin-dun-chef.md), [chef-arbitre-vs-detecteur](../05-questions-ouvertes/chef-arbitre-vs-detecteur.md), [typologie-moussaid](../05-questions-ouvertes/typologie-moussaid-explicite.md), [multi-agents-agregation (état de l'art)](../06-etat-de-lart/multi-agents-agregation.md) : matériau du livre suivant. Exceptions réintégrées dans CE livre (via [responsabilite-pilote-diversite-harnais](../01-concepts/responsabilite-pilote-diversite-harnais.md)) : la condition de décorrélation et le désaccord-détecteur au **ch. 5** (mécanique), la monoculture et le couple détecteur/arbitre au **ch. 13** (organisation), la divergence rétrospective aux ch. 13/16.
- **Navigation guidée / contexte de projection** — [navigation-guidee-contexte](../05-questions-ouvertes/navigation-guidee-contexte.md) : hors périmètre.
- **[holacratie-parallele](../01-concepts/holacratie-parallele.md)** : rétrogradé, remplacé par Haier ; matériau seulement.

## Table de correspondance fichiers → destination

| Fichier | Destination |
|---|---|
| captivite-logicielle | Ch. 1 ✍ |
| happy-path, paradoxe-armoire | Ch. 2 ✍ |
| byoai-shadow-ai-marche, byoai-solutions-existantes | Ch. 3 ✍ |
| meta-analyse-cout-aval, frontiere-structure-interface, generique-vs-specifique, arguments 1-4, deplacement-cout-aval, destin-low-code, bilan-low-code | Ch. 4 ✍ |
| responsabilite-pilote-diversite-harnais (mécanique), taxonomie-angles-morts (pièges), multi-agents-agregation (littérature) | Ch. 5 ✍ |
| doctrine, arbitrage, frontiere-si-ia-genere-code, git-dod-dor, amazon-mandat-api, argument 5, cicd-processus-comme-un-autre, skills-si-vs-skills-personnels | Ch. 6 ✍ |
| approche-datacentrique, dcb-decisions, dcb-event-sourcing, regle-executable, acces-conversationnel, claude-tag | Ch. 7 ✍ |
| delegation-agents, identite-agents-standards, kagenti, cartographie-maturite | Ch. 8 ✍ |
| delegation (section humain/agent) | Ch. 9 ✍ |
| gateways, presidio, argument-ia-locale | Ch. 10 ✍ |
| cycle-promotion, methodologies-grandes-entreprises, innersource-golden-paths | Ch. 11 ✍ |
| cycle-promotion (pilotage), mesure-complexite-fenetre | Ch. 12 ✍ |
| equipe-agile, epidemiologiste, kubernetes-pods-roles, limite-analogie-kubernetes, taxonomie-angles-morts, haier, responsabilite-pilote (organisation) | Ch. 13 ✍ |
| industrialisation-chaine-montage (chaîne de montage + biologie) | Ch. 13 ✍ (échos ch. 10 membrane/gateway, ch. 11 propagation latérale) |
| byoia-pas-plus-sur, cadre-cse, jurisprudence-cse, eu-ai-act, conformite-par-design, distinguo-url | Ch. 14 ✍ |
| amazon, methodologies, haier, positionnement-malleable, logiciel-malleable-jetable | Ch. 15 ✍ |
| meta-analyse (le trou), taxonomie (instrument), questions-restantes (genre) | Ch. 16 ✍ |
| synchronisation-fiabilite, limites diverses | Annexe B |
| byoia.md (concept central) | Intro + fil rouge de tous les chapitres |
| Cluster multi-agents (7 fichiers, hors exceptions ch. 5/13), navigation-guidee, holacratie | Hors livre |
| objectif-serie, serie-vs-article, trop-de-couches, chiffres-references, questions-livre/restantes, backlog, serie-linkedin, mindmap | Méta (pilotage du projet) |

## Correspondance série LinkedIn → chapitres (numérotation v3)

Post 1→Ch. 3 · Post 2→Ch. 1 · Post 3→Ch. 3 · Post 4→Ch. 14 · Post 5→Ch. 14/6 · Post 6→Ch. 6 · Post 7→Ch. 9 · Post 8→Ch. 11/15 · Post 9→Ch. 11-12 · Post 10→Ch. 15-16. La série teste les accroches ; les retours nourrissent la rédaction. Le ch. 5 (harnais/pièges) est un candidat naturel à un post supplémentaire ("la boucle n'enrichit plus rien").

## Convention de sourcing (décision Kevin, 2026-07-12)

Appliquée à tout le manuscrit (16 chapitres) le 2026-07-12.

- **Double appareil** : nom de la source *dans la phrase* (inline) + **note de fin numérotée** par chapitre au format Pandoc `[^ch-n]` (compile en vraies notes). Chaque chapitre a une section « ## Notes et sources » avant les notes de rédaction.
- **Marqueurs obligatoires** dans chaque note : ✓ (confiance raisonnable) / ~ (approximatif, à vérifier) / ⚠ (incertain ou extrapolé, ne pas publier sans vérif).
- **Dé-anonymisation des cas publics documentés** : Shell, Microsoft, Amazon, Haier, Spotify/Backstage, Ink & Switch/Litt sont nommés. Distinction maintenue : les **noms de produits périssables** (gateways, moteurs d'anonymisation, briques d'auth) restent en **Annexe A**, datés — stratégie anti-obsolescence, ce n'est pas de l'anonymisation de cas.
- **Clins d'œil de prose conservés** (« streamer suédois », « fabricant de frigos chinois ») mais la source réelle est nommée en note — à repasser en nom-dans-la-phrase si Kevin le préfère.

### Liste des ⚠ / ~ à vérifier en source primaire avant publication

- **Note Trésor-Éco 2026** (ch. 13 §Trésor, ch. 9, ch. 11, ch. 12) : n° et date exacts de la note, chiffres 4,5-6,2 % / 59 % / −3,8 pts / 51 % / 60 % / 10 % — lire le PDF DG Trésor.
- **Enquête Kéa × OpinionWay 2026** (ch. 3, 9, 11, 12) : méthodologie et formulations (28 % / 66 % / 16 % / 51 % / 60 % / 10 %) — lire le PDF.
- **Work Trend Index 78 %** (ch. 3) : formulation et périmètre exacts.
- **« Adoption plus rapide que cloud/mobile »** (ch. 3) : ⚠ non sourcé — étayer ou adoucir.
- **AI Act** (ch. 9, 14) : ✓ report annexe III au 2 déc. 2027 confirmé (Digital Omnibus, accord 7 mai 2026, vérifié web 2026-07 — mais adoption formelle pendante) ; ⚠ **incohérence « 16 mois » (report) vs « dix-sept mois » (corps ch. 14) à harmoniser** ; n° d'articles (14, 26, 4, annexe III) à valider avocat.
- **Jurisprudence CSE** (ch. 14) : TJ Nanterre 14/02/2025 ; TJ Nanterre 29/01/2026 n° 25/02856 ; CA Paris 21/05/2026 RG 25/13234 — vérifier sur les décisions ; articles L. 2312-8 / L. 1121-1 / L. 1222-4 sur Légifrance.
- **Kagenti/AuthBridge** (ch. 8) : ⚠ re-vérification obligatoire sur les publications Red Hat (hallucination partielle signalée).
- **« Lost in the Middle »** (ch. 5) : venue exacte (TACL) + études « context rot » Chroma.
- **Coût de propagation** (ch. 12) : référence exacte MacCormack/Baldwin/Rusnak.
- **Ordres de grandeur Haier** (ch. 15) : 80 000 personnes, milliers de micro-entreprises.
- **Auto-correction Huang et al.** (ch. 5) : proportion exacte « aussi souvent qu'elle répare ».
- **Chiffre Gartner marché gateways** (ch. 10, ~25/75 Md$) : source unique non recoupée.

## Chantiers ouverts du plan

0. **Passe « périmètre et risques » sur les 16 chapitres** (décision Kevin, 2026-07-15) : croyance populaire citée en exergue + section fermante vrai sur / faux sur / risque BYOIA / mitigation, à chaque chapitre. Grille complète et ordre de remaniement : [grille-perimetre-risques-par-chapitre](./grille-perimetre-risques-par-chapitre.md). Option d'insertion à valider (A recommandée). Un chapitre par commit git — rien ne se perd.
1. La thèse falsifiable en une phrase (introduction) — dernier gros chantier de formulation.
2. Relecture avocat du ch. 14.
3. Le schéma d'architecture complet (ch. 15 / post 10) n'est pas encore dessiné.
4. Confirmer la sortie du cluster multi-agents (décision par défaut — exceptions réintégrées aux ch. 5 et 13).
5. Vérifications Annexe A du ch. 5 : venue exacte de "Lost in the Middle", études "context rot" (Chroma), proportion exacte dans Huang et al.
6. Passe de mise à jour v2→v3 sur les fiches d'ontologie qui citent des numéros de chapitres (fait : responsabilite-pilote ; restent : regle-executable, frontiere-si-ia-genere-code, mesure-complexite-fenetre, ia-emploi-note-tresor, ai-readiness-kea-2026, serie-linkedin-10-posts, index).
