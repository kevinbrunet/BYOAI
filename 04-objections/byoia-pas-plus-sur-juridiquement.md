# Objection centrale — Le BYOIA n'est pas plus sûr juridiquement

## L'hypothèse initiale testée (et invalidée)

L'hypothèse de départ : une entreprise qui ne déploie pas l'IA elle-même, mais fournit des connecteurs et un proxy qui filtre, pourrait échapper à la notion de "déploiement formel" d'un nouvel outil — et donc à l'obligation de consultation du CSE. Cette hypothèse s'est révélée fragile, puis explicitement invalidée au fil de la discussion.

## Pourquoi ça fragilise le BYOIA plutôt que ça ne le sert

C'est précisément le proxy/gateway qui devient l'objet juridique le plus exposé : en filtrant, en connectant, en traçant l'usage, l'entreprise organise l'usage de l'IA de façon active — ce qui est potentiellement plus qu'un simple outil neutre. C'est un système de gouvernance qui a lui-même des effets sur les conditions de travail (surveillance des usages, contrôle des accès, modification des pratiques). Un juge pourrait considérer que l'infrastructure de filtrage constitue elle-même le "nouvel outil" introduit, indépendamment du modèle d'IA sous-jacent.

## Le seul angle où un avantage subsiste — et pourquoi il s'effondre vite

Si le proxy reste strictement défensif (DLP, blocage de fuite de données, sans façonner les usages ni introduire de nouvelles fonctionnalités de travail), l'argument que ce n'est pas un "outil de travail" mais un dispositif de sécurité générique (comme un antivirus ou un firewall) pourrait tenir. Mais dès qu'on ajoute des connecteurs métier (CRM, ticketing, etc.), on recrée fonctionnellement un outil de travail augmenté par IA, et l'argument s'effondre.

### Variante testée : REST + anonymisation + DLP, sans MCP ni connecteurs

Changement de nature de l'objet, mais pas nécessairement de qualification juridique :

- **L'anonymisation de prompt n'est jamais neutre.** Détecter des entités à anonymiser (noms, données de santé, secrets industriels) embarque nécessairement une logique métier — savoir ce qui compte comme donnée sensible dans le contexte de l'entreprise. Ça introduit un paramétrage propre à l'activité, donc un impact potentiel sur "l'organisation du travail" au sens du CSE — pas parce que ça facilite le travail, mais parce que ça contraint ce que le salarié peut écrire, comment, avec quel niveau de friction (blocage, reformulation automatique = charge cognitive, surveillance de contenu).
- **La vérification de fuite de données implique de la lecture du contenu.** Même sans stockage, même sans IA côté entreprise, on fait transiter et analyser les prompts des salariés — structurellement proche de la supervision des communications, terrain où le corpus CNIL/Cour de cassation est déjà dense.

### Variante testée : extension d'un proxy web de filtrage déjà existant

Argument séduisant mais fragile : le proxy web de filtrage existe déjà (et a normalement déjà été soumis à consultation CSE) ; ajouter une fonction d'analyse de contenu IA ne serait qu'une extension technique, pas un nouvel outil.

Le critère judiciaire n'est généralement pas "est-ce le même boîtier/logiciel" mais "est-ce que la finalité change et est-ce qu'il y a un impact nouveau sur les conditions de travail". Un proxy web filtrant des URL a une finalité de sécurité/conformité générique. Un proxy qui lit et analyse le contenu des prompts a une finalité qualitativement différente : il inspecte le contenu produit par le salarié dans le cadre de son activité intellectuelle, pas juste la destination réseau. ⚠ Aucune décision précise identifiée qui tranche spécifiquement ce distinguo proxy-web vs proxy-contenu-IA — extrapolation de la logique générale de la jurisprudence sur l'évolution des outils de surveillance, à vérifier avant tout argumentaire public. Voir [distinguo filtrage URL vs inspection de contenu](../05-questions-ouvertes/distinguo-filtrage-url-inspection-contenu.md).

Point important : même si l'argument "extension" passait sur le terrain CSE (L.2312-8), il ne sauve pas sur le terrain proportionnalité du contrôle de l'activité (L.1121-1/L.1222-4). Ce sont deux terrains indépendants — un dispositif peut être une extension légitime du point de vue CSE et disproportionné du point de vue surveillance individuelle si l'analyse de contenu est plus intrusive que ce qui précédait. Le fait que ce soit techniquement "le même proxy" n'immunise pas contre ce second examen.

## Le constat final

Le risque ne vient pas de l'endroit où on le cherchait. Que le filtrage/anonymisation soit fait côté BYOIA (proxy d'entreprise vers IA externe) ou côté IA fournie par l'entreprise, le fait générateur de l'obligation CSE reste le même : impact sur les conditions de travail. Le fait générateur de l'obligation de proportionnalité reste aussi le même : inspection de contenu produit par le salarié. Le BYOIA ne supprime aucun des deux faits générateurs — il change seulement qui héberge la brique technique.

Le déplacement de risque recherché ("je fournis des connecteurs, l'entreprise n'introduit rien") suppose que le risque juridique est attaché à qui possède l'infrastructure IA. Mais la jurisprudence sociale s'attache à l'effet sur le salarié, pas à la couche technique qui le produit. Un salarié dont les prompts sont filtrés, anonymisés, tracés a la même expérience de travail que le filtrage vienne d'un SaaS interne ou d'un proxy BYOIA.

## Ce qui reste vrai et vendable malgré cette correction

Voir [conformité par design comme argument de positionnement](../01-concepts/conformite-par-design.md) — le repositionnement honnête de l'argumentaire après cette correction.
