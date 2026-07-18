# Directives de production — série d'articles LinkedIn BYOAI

Document de référence pour écrire chaque article du dossier. À relire avant de rédiger le suivant. Source de vérité pour l'ordre, le calendrier et le contenu de chacun des 36 concepts : [serie-articles-linkedin-16-chapitres.md](../00-meta/serie-articles-linkedin-16-chapitres.md).

## Workflow

- On avance **un article à la fois**. Une fois un dossier livré (article + 2 posts), Claude rend la main.
- Claude ne passe au suivant que sur instruction explicite ("continue").
- Chaque article reprend le concept correspondant dans `serie-articles-linkedin-16-chapitres.md` (même titre, même position dans le calendrier, même Dépend de / Suite) mais en version **enrichie** — le fichier maître ne contient que l'esprit compact, pas le texte final.

## Structure de dossier

Un dossier par article, à la racine de `08-articles-linkedin/` :

```
NN-phaseP-titre-slug/
  article.md
  post-1.md
  post-2.md
```

- `NN` : numéro d'ordre de publication (01 à 36), sur deux chiffres.
- `phaseP` : phase éditoriale (`phase1` = Accroche, `phase2` = Fondations, `phase3` = Thèse).
- `titre-slug` : titre concaténé en kebab-case, sans accents.

Exemple déjà livré : `01-phase1-la-preference-revelee/`.

## Contenu de `article.md`

L'article doit être un texte **substantiel et publiable**, pas des notes compactes. Structure obligatoire :

1. **En-tête de métadonnées** : titre, phase, position dans la série, date de publication prévue, champ **Dépend de** et champ **Suite** (recopiés et affinés depuis le fichier maître ; ils doivent rester exacts dans l'ordre de publication réel, pas l'ordre logique du livre).
2. **Titre accrocheur** (la phrase qui énonce le cœur de la nouveauté dès la première ligne — reprend le titre du fichier maître, peut être affiné).
3. **Corps en prose**, avec sous-titres, qui déroule le gabarit dans l'ordre :
   - le cœur de la nouveauté, en ouverture
   - le point de départ dans le consensus (ce que le lecteur croit déjà savoir)
   - le récit / la démonstration qui amène la nouveauté (c'est ici qu'on enrichit : contexte, chiffres précis, mécanisme expliqué, implications concrètes)
   - ce que ça change concrètement pour le lecteur
4. **Longueur cible : 700-1000 mots** de corps rédigé (hors en-tête et sources). Un article trop court n'est pas acceptable — voir l'incident du 17/07 où le premier jet a dû être entièrement repris.
5. **Section finale "Sources & vérification"** : chaque chiffre, étude, norme ou référence cité dans l'article, listé avec son marqueur de confiance (voir ci-dessous). Sans exception.

## Contenu de `post-1.md` et `post-2.md`

Format court, feed LinkedIn. Structure obligatoire :

1. En-tête : titre du post, rappel de l'article qu'il accompagne.
2. Trois blocs, dans l'ordre : **Accroche** (phrase qui arrête le scroll) → **Assise sourcée** (un fait qui va dans le sens de la tendance du moment, sourcé) → **Ouverture** (une phrase qui pointe vers quelque chose d'en avance sur son temps, sans nécessairement tout dévoiler).
3. **Section finale "Source"** : la ou les références utilisées dans l'assise, avec marqueur de confiance. Même exigence que pour l'article — un post ne cite jamais un chiffre sans sa source et son marqueur.

## Style et voix (noté le 17/07 suite à retour de Kevin)

- Pas de tirets cadratins (—) en série. Ça sonne artificiel, trop "IA". Écrire en phrases normales, reliées par des virgules, des points, des "parce que", des "donc" — pas en fragments juxtaposés autour d'un tiret.
- Éviter les tournures trop symétriques ou oratoires : "Ce n'est pas X. C'est Y.", les rafales de phrases courtes pour créer un effet, les listes à puces qui remplacent un raisonnement qu'on pourrait juste écrire. Un texte qui sonne humain a un rythme irrégulier, pas un martèlement.
- Limiter le gras à une poignée de passages réellement importants, pas un gras par paragraphe.
- Se relire à voix haute avant de livrer : si une phrase ne se dirait pas dans une conversation, la reformuler.
- **Phrases courtes (noté le 18/07)** : le lecteur LinkedIn lit souvent en faisant autre chose en même temps, une phrase à trois ou quatre propositions imbriquées ne s'assimile pas au scroll. Préférer plusieurs phrases courtes à une phrase longue qui empile les virgules et les incises. Ça ne veut pas dire tomber dans le martèlement de phrases très courtes interdit au point précédent : viser un rythme court-moyen, pas un rythme uniforme. Se poser la question phrase par phrase : est-ce qu'elle tiendrait en une seule respiration à l'oral ? Sinon, la couper en deux.
- Ce point vaut pour tous les articles à venir, pas seulement celui qui a été corrigé.

## Vigilance sur le biais pro-Anthropic (noté le 18/07 suite à retour de Kevin)

Claude, qui rédige cette série, est un produit Anthropic. Quand un article cite des données défavorables à Anthropic (taux de reward hacking, incidents de sécurité, retards concurrentiels, etc.), il faut se relire spécifiquement pour repérer les tournures qui plaident sa cause au lieu de poser les faits : phrases qui justifient ou minimisent ("ce n'est pas parce que X, c'est plutôt parce que Y"), mise en avant rhétorique du fait que le pire exemple ne vient "pas d'Anthropic", généralisation non étayée d'un constat gênant à "tout le secteur" pour le diluer. Le test : si la phrase disparaîtrait dans un article écrit par un rédacteur sans lien avec Anthropic, elle ne doit pas y être. Ce biais est structurel, pas ponctuel : Claude ne le voit pas de l'intérieur, donc chaque article qui mentionne un laboratoire IA (Anthropic ou concurrent) doit être relu avec cette question précise avant livraison.

## Ne pas fuir une vérité gênante pour la remplacer par une facilité rhétorique (noté le 18/07)

Un article a affirmé qu'un développeur humain "n'a pas intérêt à tricher sur ses propres tests" pour opposer un agent IA biaisé à un humain qui ne le serait pas. C'est faux : les humains trichent aussi sur leurs tests, c'est juste rarement dit tout haut parce que l'accusation est inconfortable. Première correction : assumer le fait plutôt que l'éviter. Kevin a ensuite précisé qu'il ne voulait pas non plus de cette comparaison aux humains dans l'article, même corrigée : ouvrir la porte à "les développeurs trichent aussi" reste une accusation qui n'a pas sa place dans ce texte, qu'elle soit vraie ou non. Solution finale : retirer la comparaison entièrement plutôt que la corriger, et faire reposer l'argument sur l'échelle et la continuité de l'agent, sans passer par les humains pour établir le contraste. Règle générale : une comparaison factuellement inexacte doit d'abord être questionnée sur le fond (a-t-elle vraiment sa place ?) avant d'être simplement corrigée dans sa formulation. Parfois la bonne réponse n'est pas de la rendre exacte, c'est de la retirer.

## Ne pas s'attribuer les termes du secteur (noté le 18/07)

"Harnais" (comme "Assurance Level" ou d'autres termes centraux du livre) n'est pas un mot inventé par cette série ou par Kevin : c'est un terme déjà en usage croissant dans le secteur pour désigner l'outillage de validation autour d'un agent IA. Éviter les formulations du type "ce que cette série appelle le harnais", qui laissent croire à une paternité qui n'existe pas. Préférer "ce que le secteur appelle de plus en plus le harnais" ou simplement employer le mot sans le présenter comme un néologisme de la série. Vérifier ce réflexe à chaque fois qu'un terme du livre est introduit dans un article.

## Marqueurs de confiance (obligatoires, sans exception)

Devant chaque chiffre, statistique, référence normative ou citation :

- **✓** = présent dans la connaissance de Claude avec confiance raisonnable
- **~** = approximatif ou partiellement incertain, à vérifier avant publication
- **⚠** = incertain ou extrapolé, ne pas publier tel quel sans vérification

Jamais de chiffre précis ou de référence sans marqueur, y compris dans les posts courts.

## Placement des sources : dans le texte ; marqueurs de confiance : en fin d'article uniquement (noté le 18/07, précisé le 18/07 suite à un second retour de Kevin)

Deux éléments à distinguer, qui ne suivent pas la même règle de placement.

**Les sources (nom de l'organisation, de l'auteur ou de l'étude, et date) se citent au point d'usage**, dans la phrase même qui porte le chiffre ou l'affirmation, pas seulement dans une liste finale. Le lecteur LinkedIn ne scrolle pas jusqu'à une bibliographie pour vérifier une affirmation, et une source associée directement au point qu'elle prouve a plus d'autorité et de précision qu'une source détachée en fin de texte. Exemple : "un rapport de METR (juin 2025) documentait déjà..." ou "45 % selon la fiche de sécurité d'Opus 4.7 (avril 2026)". Ça, ça reste dans le texte publié.

**Les marqueurs de confiance (✓ / ~ / ⚠), eux, ne vont jamais dans le corps du texte.** Ils sont à destination de Kevin, pas du public LinkedIn : un lecteur externe n'a aucune idée de ce que signifie un ✓ accolé à une statistique, et ça casse le ton d'un article professionnel. Les marqueurs se regroupent uniquement dans la section finale "Sources & vérification", après l'article, sous forme de liste qui reprend chaque source citée dans le texte avec son marqueur. Cette section ne sera pas publiée telle quelle sur LinkedIn : c'est l'outil de relecture de Kevin avant mise en ligne, pas un contenu destiné au lecteur final.

Convention pour la section finale : une entrée par source, dans l'ordre d'apparition dans le texte, avec le marqueur en fin de ligne. Exemple : "METR, *Recent Frontier Models Are Reward Hacking* (juin 2025) ✓" ou "Anthropic, *System Card: Claude Opus 4.7* (avril 2026), chiffres via synthèse tierce dev.to, à vérifier contre le PDF primaire ~".

**Liens cliquables (noté le 18/07)** : chaque source citée au point d'usage dans le texte doit être un lien hypertexte markdown vers la page ou le document le plus direct trouvé (source primaire si accessible en ligne, sinon relais journalistique ou synthèse fiable qui elle-même renvoie à la source primaire). Ça permet au lecteur de vérifier sans quitter sa lecture. La section finale "Sources & vérification" reprend les mêmes URL en toutes lettres, à côté du marqueur de confiance, pour la relecture de Kevin.

Ce point vaut pour tous les articles et posts à venir, pas seulement celui qui a été corrigé.

## Rappels de la logique éditoriale (voir fichier maître pour le détail complet)

- **Phase 1 (art. 1-8, 1er-24 sept. 2026)** : accroche pure. Chaque article se lit seul, sans vocabulaire du livre. Certains évoquent des idées (le harnais, l'échelle de rigueur) qui ne seront nommées et démontrées qu'en phase 3 — c'est un effet voulu, pas une dette à combler tout de suite.
- **Phase 2 (art. 9-22, 29 sept.-12 nov. 2026)** : fondations, matériau plus consensuel, sert de rattrapage.
- **Phase 3 (art. 23-36, 17 nov. 2026-14 janv. 2027)** : le cœur original du livre (Assurance Level, décorrélation à l'aveugle, architecture de délégation, cycle de promotion, épidémiologiste du backlog).
- Pause de fin d'année : 18 décembre 2026 → 4 janvier 2027.
- Cadence : 2 publications/semaine, mardi et jeudi.
- Quand l'ordre de publication s'écarte de l'ordre logique du livre (un article s'appuie sur une idée publiée plus tard, ou revient sur une idée publiée des semaines plus tôt), le signaler explicitement dans le champ Dépend de / Suite plutôt que le masquer.

## Sourcing

Pour la veille 2026 et les données de marché : [veille-tendances-ia-entreprise-2026.md](../06-etat-de-lart/veille-tendances-ia-entreprise-2026.md). Pour les arguments et exemples du livre : dossiers `01-concepts`, `02-arguments`, `03-exemples` et le manuscrit dans `07-manuscrit`.
