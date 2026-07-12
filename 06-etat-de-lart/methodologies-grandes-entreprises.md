# État de l'art — Méthodologies de gouvernance des grandes entreprises (recherche web, juillet 2026)

Comment les grosses boîtes gouvernent déjà la production d'outils par les utilisateurs — principalement autour de Microsoft Power Platform (Power Automate, ex-Flow). Ces méthodes précèdent l'IA générative mais sont directement transposables (et leurs échecs instructifs).

## Microsoft — la méthode officielle Power Platform

- ✓ **CoE Starter Kit** (Center of Excellence) : kit de référence Microsoft pour gouverner l'adoption — inventaire tenant-wide, analytics, dashboards, patterns. Fait notable : ✓ Microsoft **ne le fait plus évoluer** et rapatrie les capacités nativement dans le Power Platform admin center — la gouvernance migre de l'outillage bricolé vers la plateforme elle-même.
- ✓ **Stratégie d'environnements par étages** : default, sandbox, développeur, test, production — avec pipelines ALM et "managed solutions" pour franchir les étages. C'est un **cycle de promotion institutionnalisé** : structurellement identique au [cycle de promotion](../01-concepts/cycle-promotion-specifique.md) de la série (perso → équipe → prod, avec exigences croissantes).
- ✓ **DLP par classification de connecteurs** : Business / Non-Business / Blocked — l'équivalent plateforme de la façade MCP.
- ✓ **Le problème du default environment** : indélétable, tous les utilisateurs y sont "makers" par défaut — documenté comme la première source de Shadow IT Power Platform. ~ Une organisation mid-market moyenne découvrirait 40 à 60 environnements non gérés lors de son premier audit (source vendeur, à vérifier). Leçon : un espace d'expérimentation sans chemin de promotion ni élagage devient un dépotoir — argument direct pour la fenêtre de complexité.

## Shell — le programme DIY (le meilleur cas documenté)

- ✓ Programme "DIY" (Do IT Yourself) : ~ plus de 4 000 citizen developers, CoE centralisé + des centaines de **DIY coaches** distribués (Forrester, Microsoft Customer Stories).
- ✓ **Gouvernance par trois zones** : verte "full DIY" (le citizen developer porte tout le cycle de vie), ambre "partnered DIY" (assistance formelle d'un coach), rouge "professional development" (réservé à l'IT pour le gros/risqué).
- ~ Résultat cité : temps d'approbation réduit de ~40 % (2,5 h → ~1 h) sur un cas mobile.
- ✓ Clés de succès identifiées par Forrester : zonage des cas d'usage, communautés locales, sponsoring exécutif.

## Autres références

- ✓ **Deutsche Bahn** : cas d'étude Microsoft officiel sur l'empowerment de citizen developers.
- ✓ **Gartner — fusion teams** : équipes multidisciplinaires business + tech partageant la responsabilité des résultats, organisées par capacité métier ; ~ 84 % des grandes/moyennes entreprises en auraient (Gartner). Gouvernance recommandée : **co-créée avec les équipes**, pas imposée top-down.

## PMI — le framework indépendant des éditeurs

- ✓ Le **Project Management Institute** propose "PMI Citizen Developer™" : un cadre de gouvernance **vendor-agnostic** avec trois niveaux de certification — Foundation (sensibilisation), Practitioner (méthodes de projet "hyper-agile"), Business Architect (gouvernance, structures organisationnelles, collaboration IT/métier, maturité).
- Intérêt : c'est la seule méthode trouvée qui ne vend pas de plateforme. Elle certifie des *personnes* et des *processus*. Faiblesse : pensée pour le low-code d'avant l'IA générative.

## ServiceNow — le développement délégué

- ✓ **Delegated Development** : on donne à des salariés désignés le droit de construire leurs applications **dans un périmètre prédéfini** (data models pré-approuvés, bibliothèques de composants curées par les platform engineers, revue des changements à risque). L'**App Engine Management Center** trace tout le cycle de vie.
- C'est la version plateforme de la frontière : le périmètre délégué ≈ la couche interface, le socle curé ≈ le SI. Même logique que la [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md), mais figée dans un produit propriétaire.

## Amazon — le mandat API (le précédent fondateur)

- ~ Le "mandat Bezos" (~2002, connu via le texte de Steve Yegge, 2011 — pas de document primaire public) : toutes les équipes exposent leurs données et fonctionnalités **uniquement via des API**, conçues comme exposables à l'extérieur, sous peine de licenciement. Résultat : AWS.
- C'est le précédent historique le plus fort de l'[approche data-centrique](../01-concepts/approche-datacentrique.md) : quand la structure est intégralement accessible par API, n'importe quel organe de production peut s'y brancher. Le BYOIA suppose exactement ce prérequis — Amazon prouve qu'il est atteignable et qu'il crée de la valeur au-delà de l'intention initiale.

## Haier — RenDanHeYi (le versant organisationnel radical)

- ✓ Le groupe Haier (électroménager, ~80 000 salariés) s'est réorganisé en **milliers de micro-entreprises** autonomes qui contractent entre elles sur une plateforme commune — modèle "RenDanHeYi", étudié académiquement (souvent cité par Gary Hamel).
- Parallèle : l'entreprise comme plateforme (structure, contrats, données communes) + unités autonomes qui choisissent leurs outils et méthodes. C'est le [parallèle holacratique](../01-concepts/holacratie-parallele.md) version industrielle prouvée à grande échelle — utile pour montrer que "structure commune + périphérie libre" n'est pas une utopie d'informaticien.

## Lecture critique pour la série

1. **Le développeur-harnais existe déjà sous un autre nom** : les DIY coaches de Shell sont la validation terrain du [développeur de terrain](../01-concepts/equipe-agile-developpeur-harnais.md) — professionnel distribué au plus près des utilisateurs. Différence : le coach Shell aide à construire dans l'espace contraint Power Platform ; le développeur-harnais produit en code pur.
2. **Les zones Shell vs la frontière fiduciaire** : Shell zone par *niveau de risque du cas d'usage* (jugement humain, a priori) ; la [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) zone par *nature de l'artefact* (5 critères, mécaniques). Le test des cinq questions est plus reproductible — mais Shell prouve qu'un zonage, même grossier, fonctionne à 4 000 personnes. À citer comme précédent, à dépasser comme méthode.
3. **La stratégie d'environnements Microsoft est le précédent industriel du cycle de promotion** — avec sa leçon négative : sans élagage (default environment), l'étage du bas pourrit. Personne ne documente la descente ; la série si.
4. **Le mouvement de fond** : Microsoft absorbe la gouvernance dans la plateforme (fin du CoE Kit). C'est la réponse "plateforme propriétaire" déjà identifiée chez [Retool/Databricks](./byoai-shadow-ai-marche.md) : gouvernance excellente, captivité maximale. Le BYOIA propose l'alternative : les mêmes mécanismes (étages, DLP, inventaire, métriques) mais sur du code pur et des API ouvertes.
5. **Gartner converge avec le livre** sur un point : la gouvernance co-créée bat la gouvernance imposée — cohérent avec l'uniformisation a posteriori.

## Sources

- [Microsoft Learn — CoE Starter Kit overview](https://learn.microsoft.com/en-us/power-platform/guidance/coe/overview)
- [Microsoft Learn — Manage the default environment](https://learn.microsoft.com/en-us/power-platform/guidance/adoption/manage-default-environment)
- [Microsoft Learn — Migrating from the default environment](https://learn.microsoft.com/en-us/power-platform/guidance/white-papers/migrating-from-default-environment)
- [Forrester — Case Study: Shell's DIY Citizen Developer Program](https://www.forrester.com/report/case-study-shells-diy-citizen-developer-program/RES178358)
- [Forrester — How Shell Led A Citizen Developer Movement](https://www.forrester.com/blogs/how-shell-led-a-citizen-developer-movement/)
- [Microsoft Customer Stories — Shell](https://www.microsoft.com/en/customers/story/1699045592642116808-shell-energy-power-platform-uk)
- [Microsoft Learn — Deutsche Bahn case study](https://learn.microsoft.com/en-us/power-platform/guidance/case-studies/db-empowers-citizen-devs)
- [Gartner — Build a Better Fusion Team](https://www.gartner.com/en/articles/fusion-teams)
- [Microsoft Inside Track — Empowering citizen developers](https://www.microsoft.com/insidetrack/blog/empowerment-with-good-governance-how-our-citizen-developers-get-the-most-out-of-the-microsoft-power-platform/)
- [PMI — Citizen Developer](https://www.pmi.org/citizen-developer/)
- [MPUG — Les trois offres PMI Citizen Developer](https://mpug.com/webinar-highlights-master-citizen-devleopment-with-pmis-three-offerings-foundation-practitioner-and-business-architect/)
- [ServiceNow — Delegated Development](https://www.servicenow.com/products/delegated-development.html)
- [ServiceNow — Citizen Development Program](https://www.servicenow.com/solutions/creator-workflows/citizen-development-program.html)
- [Devoteam — App Engine Management Center](https://www.devoteam.com/webinar-on-demand/mastering-application-development-governance-with-servicenow-app-engine-management-center/)
