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
- Ce point vaut pour tous les articles à venir, pas seulement celui qui a été corrigé.

## Marqueurs de confiance (obligatoires, sans exception)

Devant chaque chiffre, statistique, référence normative ou citation :

- **✓** = présent dans la connaissance de Claude avec confiance raisonnable
- **~** = approximatif ou partiellement incertain, à vérifier avant publication
- **⚠** = incertain ou extrapolé, ne pas publier tel quel sans vérification

Jamais de chiffre précis ou de référence sans marqueur, y compris dans les posts courts.

## Rappels de la logique éditoriale (voir fichier maître pour le détail complet)

- **Phase 1 (art. 1-8, 1er-24 sept. 2026)** : accroche pure. Chaque article se lit seul, sans vocabulaire du livre. Certains évoquent des idées (le harnais, l'échelle de rigueur) qui ne seront nommées et démontrées qu'en phase 3 — c'est un effet voulu, pas une dette à combler tout de suite.
- **Phase 2 (art. 9-22, 29 sept.-12 nov. 2026)** : fondations, matériau plus consensuel, sert de rattrapage.
- **Phase 3 (art. 23-36, 17 nov. 2026-14 janv. 2027)** : le cœur original du livre (Assurance Level, décorrélation à l'aveugle, architecture de délégation, cycle de promotion, épidémiologiste du backlog).
- Pause de fin d'année : 18 décembre 2026 → 4 janvier 2027.
- Cadence : 2 publications/semaine, mardi et jeudi.
- Quand l'ordre de publication s'écarte de l'ordre logique du livre (un article s'appuie sur une idée publiée plus tard, ou revient sur une idée publiée des semaines plus tôt), le signaler explicitement dans le champ Dépend de / Suite plutôt que le masquer.

## Sourcing

Pour la veille 2026 et les données de marché : [veille-tendances-ia-entreprise-2026.md](../06-etat-de-lart/veille-tendances-ia-entreprise-2026.md). Pour les arguments et exemples du livre : dossiers `01-concepts`, `02-arguments`, `03-exemples` et le manuscrit dans `07-manuscrit`.
