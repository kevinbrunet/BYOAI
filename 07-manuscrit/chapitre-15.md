# Chapitre 15 — Ceux qui en ont déjà fait la moitié

Un lecteur arrivé jusqu'ici a le droit de poser la question qui tue les livres d'idées : est-ce que quelqu'un l'a fait ? La réponse honnête — ce livre n'en a pas d'autre — est : personne n'a fait le tout, et ce chapitre ne vous racontera pas le déploiement miracle chez un client anonyme. Mais chaque moitié du modèle a été construite, à grande échelle, par des organisations qu'on ne soupçonnera pas de romantisme. Ce chapitre les passe en revue — non comme des preuves d'autorité, mais comme des pièces à conviction : chacune démontre qu'une partie du modèle tient en production, et chacune, par ce qui lui manque, désigne exactement ce que les autres apportent.

## La structure : le mandat de 2002

La première moitié — un socle intégralement exposé par API, sans porte dérobée — a été construite par Amazon, et le chapitre 6 a raconté l'histoire : le mémo de Bezos, les cinq règles, la menace finale, des années de chantier douloureux, et AWS en sous-produit — l'infrastructure conçue comme exposable devenue produit mondial. Ce que ce précédent prouve : le prérequis du modèle est atteignable, à une échelle et avec un héritage qui relativisent tous les nôtres, et il crée de la valeur au-delà de son intention.

Ce qui lui manque : le mandat organise des *équipes* qui se parlent par API — il ne dit rien des individus, de leurs outils, de la gouvernance du spécifique. Amazon a construit le socle ; la question de qui s'y branche et comment restait entière.

## La gouvernance du bricolage : les zones et les étages

La deuxième moitié — gouverner la production d'outils par les salariés eux-mêmes — tourne depuis des années dans l'écosystème low-code, et le chapitre 11 en a extrait les mécanismes. Shell[^15-1] fait produire des outils internes par plusieurs milliers de salariés, encadrés par un zonage à trois niveaux et des coaches professionnels distribués dans les équipes — la préfiguration du développeur de terrain. Microsoft[^15-2] a institutionnalisé, sur sa Power Platform, les environnements par étages avec exigences croissantes — la préfiguration du cycle de promotion — et documenté malgré lui la leçon négative la plus précieuse du domaine : le bac à sable sans élagage qui devient décharge.

Ce que ces précédents prouvent : des salariés qui construisent leurs outils, à des milliers, sous gouvernance par zones et par étages — ça marche, c'est documenté, les directions dorment. Ce qui leur manque, le chapitre 4 l'a établi : tout se passe dans un atelier propriétaire — plafond de contraintes et captivité — et personne ne sait jeter. Le code pur et la descente : précisément ce que le reste du modèle apporte.

## L'organisation : quatre-vingt mille personnes en périphérie autonome

La troisième moitié est organisationnelle, et c'est la plus contre-intuitive : une grande entreprise peut-elle vraiment fonctionner en "socle commun + périphérie autonome" sans se dissoudre ? Le fabricant chinois Haier — l'un des premiers groupes d'électroménager au monde, quatre-vingt mille personnes — l'a fait, depuis 2005, sous le nom de RenDanHeYi[^15-3] : l'entreprise découpée en milliers de micro-entreprises de quelques dizaines de personnes, dotées des trois droits qu'une hiérarchie classique réserve au sommet — décider, recruter, distribuer leurs profits —, qui se coalisent par contrat autour d'un besoin client et se recomposent selon le résultat. Le groupe central ne dirige plus : il fournit la plateforme — services partagés, capital, marque, données, mécanismes contractuels. Et la rémunération y suit la valeur créée pour l'utilisateur, pas l'évaluation du supérieur — la version ressources humaines des métriques d'usage du chapitre 11 : dans les deux cas, c'est l'usage réel qui arbitre, pas l'organigramme.

Ce que ce précédent prouve : "structure commune + périphérie autonome" n'est pas une utopie d'informaticien — c'est un modèle industriel qui tient depuis vingt ans à une échelle que peu de lecteurs auront à affronter. Ce qui lui manque, pour notre propos : Haier organise des équipes et des contrats, pas des outils et des API — et sa transposition hors de son contexte (culturel, social, juridique — le chapitre 14 suffit à mesurer l'écart avec le droit français) serait naïve. On en retient la preuve de faisabilité du principe, pas un modèle à copier.

## La vision individuelle : le logiciel malléable

La dernière moitié n'est pas une entreprise mais un courant d'idées, et c'est la filiation que ce livre revendique. Depuis quelques années, des chercheurs — autour notamment de Geoffrey Litt et du laboratoire Ink & Switch — développent la vision du **logiciel malléable**[^15-4] : la promesse originelle de l'informatique personnelle était une argile que chacun remodèle ; nous avons eu des appareils scellés, construits ailleurs, immuables. Leur formule la plus mordante : les applications sont des coupe-avocats — des gadgets monofonction qu'on nous vend au lieu du couteau qui s'adapte. Leur métaphore centrale : le logiciel devrait être une cuisine de maison, pas un restaurant où l'on subit le menu. Et leur constat technique rejoint le chapitre 4 : les modèles de langage sont la technologie qui manquait à quarante ans de tentatives d'*end-user programming*.

Le lecteur reconnaît la métaphore — elle ouvre ce livre. La recette de cuisine de la machine à café du chapitre 1, c'était la cuisine de maison à l'état sauvage : le besoin de spécifique, réel depuis toujours, exprimé dans le pire médium possible. Le courant du logiciel malléable donne à ce besoin sa dignité théorique et ses prototypes. Ce qui lui manque — et il ne prétend pas l'avoir — c'est l'entreprise : la conformité, la traçabilité, l'audit, le droit du travail, la mutualisation, tout ce que les chapitres 6 à 14 ont construit. Ce livre est, très exactement, le versant organisationnel du logiciel malléable : la cuisine de maison, avec les règles d'hygiène qui permettent d'inviter les autres à table — et le chemin par lequel un plat réussi entre à la carte commune.

## L'assemblage

Posez les quatre pièces côte à côte et regardez le motif. Amazon a prouvé le socle — mais sans les individus. Le monde low-code a prouvé la gouvernance des individus — mais sans le code pur ni l'élagage. Haier a prouvé l'organisation — mais sans les outils. Le logiciel malléable a prouvé la vision individuelle — mais sans l'organisation. Chaque précédent s'arrête exactement là où un autre commence ; aucun ne contredit les autres ; et leur assemblage est ce que ce livre a construit, chapitre après chapitre : le socle par API qui expose, mémorise et refuse en expliquant ; la délégation typée qui sait qui agit et pour qui ; les actes réservés aux humains ; le trajet sécurisé par une infrastructure déjà payée ; le cycle qui fait monter ce qui le mérite et descendre ce qui ne sert plus ; la fenêtre qui borne le tout ; les rôles qui l'opèrent ; et le droit qui, bien pris, le récompense.

Ce modèle a besoin d'un nom, et le phénomène qui le rend nécessaire en a déjà un : le BYOAI — les salariés apportent leur IA, c'est un fait, il est massif, il est documenté. Ce que ce livre propose est l'étage au-dessus du fait : non pas subir l'IA apportée, ni la combattre, mais construire l'entreprise qui l'accueille. Le fait vous arrive ; l'architecture, elle, se choisit.

Reste la question que tout essai honnête doit affronter en dernier : puisque personne n'a encore assemblé le tout — comment saurez-vous, chez vous, si ça marche ? C'est l'objet du dernier chapitre, et il ne se dérobera pas.

## Notes et sources

[^15-1]: Shell — programme « DIY » (*Do IT Yourself*) : voir la note détaillée et les sources (Forrester, Microsoft Customer Stories) au chapitre 13. ~ Plusieurs milliers de créateurs d'outils, coaches distribués, zonage à trois niveaux.

[^15-2]: Microsoft — environnements par étages de la Power Platform et leçon de l'« environnement par défaut » : voir la note et les sources au chapitre 11.

[^15-3]: ✓ Haier, modèle *RenDanHeYi* (depuis ~ 2005) : groupe d'électroménager, ~ 80 000 personnes, découpé en milliers de micro-entreprises dotées des droits de décision, de recrutement et de distribution des profits. ~ Ordres de grandeur (effectif, nombre de micro-entreprises) à revérifier ; littérature académique plus nuancée sur la transposabilité — cité comme preuve de principe, non comme modèle à copier.

[^15-4]: ✓ Courant du *logiciel malléable* (*malleable software*) : Geoffrey Litt et le laboratoire Ink & Switch (travaux 2025). Images « coupe-avocats » et « cuisine de maison » créditées à leurs auteurs ; les modèles de langage y sont présentés comme la brique manquante de quarante ans d'*end-user programming*.

---

## Notes de rédaction (hors manuscrit)

- Structure "pièces à conviction" : chaque précédent = ce qu'il prouve + ce qui lui manque, le manque de chacun étant couvert par un autre — le motif d'assemblage est l'argument du chapitre.
- **Dé-anonymisation 2026-07-12 (décision sourcing)** : Shell et Microsoft sont désormais nommés dans le corps (comme aux ch. 11 et 13), avec notes de renvoi — cohérence d'anonymisation inter-chapitres rétablie dans le sens du nommage. Amazon, Haier, Litt/Ink & Switch étaient déjà nommés — figures publiques documentées, indispensables à la crédibilité.
- ✓ Haier/RenDanHeYi : [haier-rendanheyi](../03-exemples/haier-rendanheyi.md) — les réserves du fichier (études critiques plus nuancées, transposition) sont rendues par "pas un modèle à copier". ~ "quatre-vingt mille personnes", "milliers de micro-entreprises" : ordres de grandeur à re-vérifier.
- ✓ Malleable software : [positionnement-malleable-software](../01-concepts/positionnement-malleable-software.md), [logiciel-malleable-jetable](../06-etat-de-lart/logiciel-malleable-jetable.md) — "coupe-avocats" et "cuisine de maison" sont leurs images (Ink & Switch 2025, Litt), créditées nominalement. La boucle avec la recette de cuisine du ch. 1 est le sommet émotionnel du chapitre.
- Le positionnement "extension du BYOAI" est posé ici en clôture ("le fait vous arrive ; l'architecture se choisit") — cohérent avec la décision de nommage (nom final à trouver, la formule fonctionne sans lui).
- Le "schéma d'architecture complet" prévu au plan est rendu en une phrase-fleuve récapitulative — le schéma graphique reste à dessiner (chantier ouvert n° 3 du plan).
- Grille lecteur : tous ("est-ce que quelqu'un l'a fait ?") — la réponse honnête d'entrée ("personne n'a fait le tout") est la condition de crédibilité du chapitre.
- Sources ontologie : amazon-mandat-api, methodologies-grandes-entreprises, haier-rendanheyi, positionnement-malleable-software, logiciel-malleable-jetable, innersource-golden-paths.
