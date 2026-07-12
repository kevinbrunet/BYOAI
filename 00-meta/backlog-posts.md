# Backlog des posts — enrichissements et nouveaux posts

Ce fichier suit les allers-retours éditoriaux identifiés suite à l'introduction du concept [DCB (décisions comme events)](../01-concepts/dcb-decisions-comme-events.md). Les posts référencés ici (11, 12, -1b) sont numérotés dans la série existante de Kevin, en dehors de cette arborescence markdown — ils ne sont pas encore présents comme fichiers dans ce dossier.

## Posts existants à enrichir

### Post 11 — "On ne documente pas la solution"

La succession des choix comme actif architectural gagne une mécanique concrète : le stream de décisions DCB. La phrase "sans ça l'IA optimise sur la solution courante" devient "sans ça l'IA ne peut pas naviguer dans le graphe de décisions actives".

### Post 12 — "Une base de données aplatit les décisions"

Suite naturelle : DCB comme modèle de stockage des décisions elles-mêmes, pas seulement des données métier. C'est une couche au-dessus de ce que le post dit actuellement.

### Post -1b — "On ne cherche pas la solution, on balise son périmètre"

"Transformer chaque décision en point de contrôle" devient concret : un point de contrôle est un event dans le stream, avec un début, une fin, une projection activable.

## Nouveau post à créer

### "Les décisions ont une durée de vie"

**Citations sources (à retravailler, pas à publier telles quelles) :**

> "On se retrouve avec une série d'essais qui dit oui avant 2000 ça voulait dire ça et après 2000 on traite comme ça."
> "Chaque décision a une mission. Et un début et une fin."
> "L'important c'est pas d'oublier c'est de pouvoir naviguer là dedans en ne voyant que ce que l'on a besoin."
> "Ce qui tient du passé continuera de fonctionner si on s'applique sur le changement présent."

**Structure proposée :**

- Une décision n'est pas un document — c'est un nœud dans un graphe avec des propriétés temporelles
- Chaque décision a une mission, un début, une fin — et des dépendances vers d'autres décisions
- Changer une décision sans connaître ses dépendances, c'est opérer à l'aveugle
- Le stream de décisions permet de rejouer, d'essayer, de faire un rollback — sans perdre le passé

**Audience :** architectes, tech leads seniors

**Plus-value :** donne une mécanique concrète à l'axiome "on documente les choix, pas les solutions" — pose DCB comme outil de gouvernance architecturale, pas seulement de données métier.

## Nouveau post à créer — PRIORITAIRE

### "Des API interdites à l'IA" (titre de travail)

**Marqué critique par Kevin (2026-07-11).** Source conceptuelle : [délégation d'identité — section humain/agent](../01-concepts/delegation-agents-jwt-mtls.md).

**La thèse en une phrase :** la chaîne de délégation doit typer chaque maillon — humain ou agent — pour que certaines API puissent refuser l'IA, même munie d'une délégation valide.

**Structure proposée :**

- L'angle d'attaque : tout le monde se demande ce que l'IA a le droit de *lire*. La vraie question est ce qu'elle a le droit d'*acter*.
- Les trois régimes par endpoint : ouvert / agent sous délégation / humain uniquement.
- Le point décisif : "l'IA prépare, l'humain décide" existe partout comme slogan de gouvernance — ici c'est l'API qui refuse. La règle devient exécutoire.
- Le bonus réglementaire : la supervision humaine exigée par l'AI Act (art. 26, haut risque emploi) devient une propriété prouvable par les logs, pas un processus déclaré. Conformité démontrable à l'audit.
- L'honnêteté qui crédibilise : deux limites à nommer dans le post — le rubber-stamping (l'humain qui clique OK sur tout) et la difficulté de prouver l'humain (un agent sait cliquer aussi ; piste : ré-authentification forte type passkey au moment de l'acte).

**Audience :** DSI, RSSI, architectes sécurité — plus large que les posts techniques habituels car le sujet touche conformité et gouvernance.

**Plus-value / timing :** fenêtre AI Act (haut risque reporté à déc. 2027 — 17 mois pour construire) ; le marché parle identité d'agents (drafts IETF, RSAC 2026) mais personne ne formule le régime "humain uniquement" comme objet architectural de premier ordre.

**Connexion série :** c'est le verrou technique de la frontière fiduciaire — le post peut vivre seul mais prépare le chapitre doctrine.

## Post déjà rédigé — "Post 1 — Le happy path n'existe pas"

Post fondateur de la série (numéro 1), déjà rédigé en entier. Argument statistique : sur un parcours à 10 étapes avec 90% de chance de rester nominal à chaque étape, la probabilité de traverser tout le parcours sans déviation n'est que de ~35%. Le mode dégradé est le régime par défaut, pas l'exception. Audience : product owners, tech leads. Contenu conceptuel extrait dans [happy path — illusion statistique](../01-concepts/happy-path-illusion-statistique.md), qui relie ce post à des concepts déjà présents dans la série (sagesse des foules, taxonomie des angles morts, paradoxe de l'armoire à fibre) sans que le lien ait été posé explicitement au moment de leur rédaction.

## Post déjà publié — "Le BYOIA ne coûte quasiment rien à sécuriser. C'est déjà payé."

Post sur le marché des gateways de sécurisation LLM (Bifrost, Portkey, LiteLLM, Cloudflare AI Gateway, Kong AI Gateway) et leur réutilisation directe pour sécuriser le BYOIA. Contenu de vérification et tableau comparatif détaillé conservés dans [gateways de sécurisation LLM](../03-exemples/gateways-securisation-llm.md) — le post publié lui-même ne garde aucun marqueur de confiance, contrairement à cette page de travail.

## Post déjà publié — "Réagir vite, c'est bien. Comprendre, c'est encore mieux."

Post LinkedIn en réaction à la conférence "Éloge de la simplicité" de Frédéric Leguédois, déjà publié. Contenu conceptuel extrait dans la série : [paradoxe de l'armoire à fibre optique](../01-concepts/paradoxe-armoire-fibre-optique.md) et [l'épidémiologiste du backlog](../01-concepts/epidemiologiste-du-backlog.md) (métaphore urgentiste/interniste/épidémiologiste).

Le conférencier a réagi publiquement en confirmant que la piste était juste mais hors du format de sa conférence (45 minutes) — point d'ouverture possible pour un prolongement ou une collaboration future, non formalisé à ce stade.

## Recommandation éditoriale

Ne pas surcharger les posts existants (calibrés pour LinkedIn). Créer le nouveau post séparément, et ajouter une simple note de renvoi dans les posts 11 et 12 pour signaler la connexion, plutôt que d'y injecter tout le contenu DCB.

## Point de vigilance — connexion à un autre projet

Le point ouvert sur la navigation guidée mentionne un lien naturel avec un agent qui saurait quelle projection demander selon la tâche en cours — évoqué dans la conversation source sous le nom "Alveus". Ce projet (BYOIA) est censé rester indépendant du travail sur Alveus/la cosmogonie. Cette note existe donc uniquement pour signaler le point de contact identifié dans la conversation source, sans développer Alveus ici — voir [navigation guidée et contexte de projection](../05-questions-ouvertes/navigation-guidee-contexte.md).
