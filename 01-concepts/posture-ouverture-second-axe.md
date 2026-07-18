# La posture d'ouverture — un second axe, orthogonal à l'Assurance Level

Concept formulé par Kevin (2026-07-17), en réaction à une question : le BYOIA suppose-t-il forcément une ouverture totale, ou peut-il se faire "à la carte" ? Recherche et formalisation par Claude le même jour.

## Le principe

L'Assurance Level (voir [cycle de promotion du spécifique](./cycle-promotion-specifique.md) et le chapitre 6) répond à une question par artefact : *combien de rigueur celui-ci exige-t-il, vu ce qui en dépend ?* C'est un axe vertical, et il s'applique quel que soit le contexte organisationnel.

La posture d'ouverture répond à une question différente, en amont, au niveau de l'organisation entière : *combien de liberté accorde-t-on à la tuyauterie qui produit les artefacts ?* Ce n'est pas une question par artefact, c'est un choix de configuration que chaque entreprise fait une fois (ou peu souvent), et qui détermine le point de départ et le coût de la montée en Assurance Level pour tout ce qui suivra.

Les deux axes sont indépendants. Une entreprise très ouverte sur la posture peut quand même exiger l'Assurance Level 3 pour un artefact donné ; elle paiera juste plus cher pour l'atteindre, parce que la surface à auditer est plus large. Une entreprise très fermée peut promouvoir plus vite, parce que les briques de départ sont déjà pré-vérifiées.

## Le menu (à la carte, par curseur indépendant)

Quatre curseurs, réglables séparément :

1. **Fondations** (le SI, voir [approche datacentrique](./approche-datacentrique.md)) : périmètre de données et de règles largement exposé, ou restreint à un sous-ensemble gouverné.
2. **Harnais** (voir [chapitre 5](../07-manuscrit/chapitre-05.md)) : libre choix de l'outillage de validation, ou cadré dans un framework de harnais imposé par l'entreprise.
3. **Skills & tools** (voir [skills SI vs skills personnelles](./skills-si-vs-skills-personnelles.md)) : import libre par le collaborateur, ou puisé dans une bibliothèque d'entreprise curatée.
4. **Modèle** (voir [l'argument IA locale](./argument-ia-locale-souverainete.md)) : IA du marché (cloud), ou IA locale à l'entreprise.

Une entreprise règle chacun de ces curseurs selon le compromis qu'elle peut ou veut faire. Il n'y a pas de réglage "correct" dans l'absolu, c'est un choix de gouvernance, comme le choix d'un niveau d'Assurance Level pour un artefact donné.

## Châssis standardisé, diversité de modèles

Un curseur restrictif sur le harnais (point 2) ressemble, à première vue, à une contradiction avec la [diversité des harnais comme défense contre les angles morts](./responsabilite-pilote-diversite-harnais.md) : imposer *un* framework de harnais, n'est-ce pas recréer la monoculture que le livre dénonce par ailleurs ?

Non, si on distingue deux couches à l'intérieur du harnais lui-même :

- le **châssis** : le mécanisme d'import et d'exécution (comment un skill ou un tool se déclare, s'autorise, se journalise, s'audite) ;
- ce qui roule dessus : le **modèle**, les **skills**, les **tools** effectivement branchés.

Standardiser le châssis ne standardise pas ce qui roule dessus. Une entreprise peut imposer un seul framework de harnais (pour la gouvernance, l'audit, la portabilité de la configuration) tout en laissant une pleine diversité de modèles et de skills à l'intérieur de ce châssis. La formule à retenir : **châssis standardisé, diversité de modèles**. Ça ne contredit pas l'argument du chapitre 13, ça le précise : ce que l'entreprise a le droit d'uniformiser, c'est la plomberie, jamais le jugement qui circule dedans.

## Confinement, pas prévention

Kevin a proposé que le problème des skills vérolées et de l'injection de prompt se gère par le proxy, la délégation d'identité surveillée et l'humain obligatoire. C'est vrai, mais il faut être précis sur ce que ça garantit : ces trois mécanismes **bornent le rayon d'action** d'un agent compromis, ils ne l'empêchent pas d'agir. Un skill vérolé ou une injection de prompt qui pousse un agent à mal utiliser un périmètre qu'il détient déjà légitimement (lire ce qu'il a le droit de lire, mais pour la mauvaise raison, ou l'envoyer au mauvais endroit) reste possible dans le régime "ouvert" et dans le régime "agent sous délégation" du [chapitre 9](../07-manuscrit/chapitre-09.md). Seul le régime "humain uniquement" ferme vraiment la porte, et seulement sur les actions qui y sont explicitement rattachées.

C'est du confinement de dégâts, pas de la prévention du problème à la source. Le livre doit le présenter ainsi plutôt que comme une solution complète.

## Ancrage état de l'art : MCP, nouvelle mouture (2026)

Le "framework suffisamment paramétrable dans lequel le salarié importe ses skills et ses tools" a un équivalent concret en train de se standardiser sous nos yeux : le Model Context Protocol (MCP). Vérifié le 17/07/2026 :

- MCP a été donné par Anthropic à l'Agentic AI Foundation, sous la Linux Foundation, en décembre 2025 : c'est devenu un standard neutre, gouverné par la communauté, pas par un fournisseur. Bon exemple concret de "châssis" au sens du livre : une plomberie standardisée que chacun peut brancher différemment ✓
- La feuille de route 2026 du protocole cible explicitement la maturité entreprise : audit et observabilité connectés aux SIEM/APM existants, authentification gérée par l'entreprise avec flux SSO, patterns de gateway et de proxy (propagation d'autorisation, affinité de session), portabilité de la configuration entre clients ✓
- Le pattern de gateway n'est plus un simple add-on : il devient une infrastructure formalisée du protocole lui-même — convergence directe avec l'architecture de gateway déjà décrite au chapitre 10 du livre (LinkedIn : article 29, *La sécurisation est déjà payée*) ✓
- Spécification 2026-07-28 (candidate de sortie, plus grosse révision depuis le lancement) : cœur sans état ("stateless"), qui passe à l'échelle sur infrastructure HTTP ordinaire ; extension "MCP Apps" pour des interfaces serveur rendues dans un bac à sable ; extension "Tasks" pour le travail de longue durée ; autorisation alignée sur OAuth 2.1 et OpenID Connect, avec PKCE et jetons liés à une audience précise ; extension "Enterprise-Managed Authorization" passée au statut stable, qui centralise le contrôle d'accès via le fournisseur d'identité de l'entreprise, remplaçant les popups de consentement serveur par serveur par un flux "zéro contact" une fois connecté ✓
- Les en-têtes `Mcp-Method` et `Mcp-Name` permettent de router différents appels d'outils vers différentes politiques d'autorisation **au niveau de la gateway**, avant même d'atteindre le code du serveur — exactement le mécanisme de policy déportée que le livre défend depuis le chapitre 7 (refuser en expliquant, hors du code métier) ✓

Une phrase de Microsoft (blog sécurité, juin 2026) résume l'esprit exact de la posture d'ouverture telle que définie ici, et vaut d'être citée telle quelle dans le livre : *« the protocol deliberately does not enforce security for you. It defines how clients and servers talk; the locks are yours to fit »* — le protocole ne fait pas le choix de sécurité à la place de l'entreprise, il expose la plomberie standardisée ; les verrous restent à poser, et c'est précisément la posture d'ouverture qui décide où les poser ✓

## Les risques documentés, et leur contrôle correspondant

Synthèse d'un état des lieux Microsoft (juin 2026) et de la littérature académique 2026, vérifiée le 17/07 :

1. **Injection de prompt et empoisonnement d'outils (tool poisoning)** : un agent traite tout ce qui est dans son contexte comme fiable, y compris les descriptions d'outils. Des instructions cachées dans une description ou un schéma peuvent détourner l'agent. Taux de réussite d'attaque mesuré jusqu'à 72 % sur des agents populaires, et fait notable, les modèles les plus capables suivent parfois *mieux* les instructions malveillantes cachées, précisément parce qu'ils suivent mieux les instructions en général ✓. Incident réel documenté en avril 2026 : des chercheurs (Aonan Guan et une équipe de Johns Hopkins) ont détourné Claude Code, Gemini CLI et GitHub Copilot en injectant des instructions dans des titres de pull request GitHub, provoquant l'exfiltration de secrets GitHub Actions ✓. Une divulgation 2026 a recensé jusqu'à 200 000 instances MCP vulnérables exposées ✓. Contrôle : traiter les descriptions et sorties d'outils comme une entrée non fiable, validation humaine de la liste d'outils, afficher l'appel d'outil complet plutôt qu'un résumé, isoler les serveurs sensibles des serveurs généralistes.
2. **Autorisation et "confused deputy"** : un serveur agit avec ses propres privilèges larges pour le compte d'un utilisateur qui ne les a pas. Contrôle : OAuth 2.1 + PKCE, jetons liés à une audience, gateway qui rejette tout appel sans jeton valide — convergence quasi totale avec l'architecture mTLS + RFC 8693 déjà proposée aux chapitres 7-8 du livre ✓.
3. **Accès trop large et agrégation de identifiants** : un seul serveur MCP détient souvent les accès à plusieurs systèmes à la fois, avec des scopes plus larges que nécessaire. Contrôle : moindre privilège par ressource, jetons de courte durée, identité gouvernable par classe d'agents (ex. Microsoft Entra Agent ID, qui permet une politique groupée ou un arrêt d'urgence sur toute une classe d'agents) ✓.
4. **Chaîne d'approvisionnement et "rug pulls"** : un serveur approuvé lors d'une revue peut changer de comportement une fois que des workflows en dépendent déjà. Contrôle : catalogue de référence au moment de la conception, empreinte des définitions d'outils avec alerte sur dérive, gateway qui revérifie identité et politique à chaque appel, pas seulement à l'approbation initiale ✓.
5. **MCP fantôme (Shadow MCP)** : l'équivalent du Shadow AI pour l'ère des agents — un serveur monté vite pour débloquer une démo, jamais enregistré. Contrôle : registre de ce qui existe, gateway par lequel tout doit obligatoirement transiter ✓. Rejoint directement l'argument du chapitre 3 sur le Shadow AI, décliné une échelle plus bas.
6. **Injection de commande et évasion de bac à sable** : de nombreux serveurs MCP tournent en local, manipulent des sous-processus et le système de fichiers. Contrôle : conteneurs avec accès minimal, sortie réseau bloquée par défaut, validation systématique des entrées et sorties ✓.

Le fil conducteur, qui vaut d'être répété dans le livre : chaque contrôle mentionné ci-dessus est une déclinaison d'un mécanisme déjà présent dans l'architecture du livre (gateway, délégation d'identité, régimes par endpoint, catalogue/bibliothèque gouvernée). MCP ne invente pas une nouvelle doctrine de sécurité, il confirme, par la pratique et sous la pression de vraies attaques en production, que la doctrine déjà posée dans ce livre est la bonne échelle de réponse.

## Où ça s'insère dans le livre

- **Ch. 5 (harnais)** et **ch. 6 (gradient)** : la posture d'ouverture comme second axe, à croiser avec l'Assurance Level. Potentiellement une nouvelle section ou un nouveau chapitre court, pas encore tranché.
- **Ch. 7-8 (délégation)** : MCP 2026 comme validation externe de l'architecture proposée (OAuth 2.1/PKCE/audience-bound tokens ≈ mTLS + RFC 8693 + claim `act`).
- **Ch. 9 (régimes par endpoint)** : le "confused deputy" et l'injection de prompt confirment que le régime humain-uniquement n'est pas une précaution excessive, c'est la seule porte qui ferme vraiment.
- **Ch. 13 (diversité des harnais)** : formalisation "châssis standardisé, diversité de modèles" à intégrer pour prévenir toute lecture contradictoire avec ce nouveau concept.

## Statut

Intégré en transversal le 2026-07-17 (décision Kevin : "transversale ça impacte tout"), sans chapitre dédié :

- **Ch. 6** : nouvelle section "La posture d'ouverture : un second axe" — le menu à quatre curseurs, la distinction châssis/diversité, le confinement/prévention, l'ancrage MCP.
- **Ch. 5** : paragraphe de transition posant la distinction châssis/diversité avant la clôture du chapitre, pour anticiper le ch. 6.
- **Ch. 8** : paragraphe sur la spec MCP du 28/07/2026 comme validation externe de l'architecture de délégation (OAuth 2.1/PKCE/audience-bound tokens).
- **Ch. 9** : paragraphe "confused deputy" avec l'incident réel d'avril 2026 et les statistiques d'attaque, à l'appui du régime humain-uniquement.
- **Ch. 13** : formalisation "châssis standardisé, diversité de modèles" ajoutée après "Uniformiser le socle, jamais le harnais".
