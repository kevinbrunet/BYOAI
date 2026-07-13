# Chapitre 3 — Le BYOAI est déjà dans vos murs

Les deux premiers chapitres ont établi un diagnostic : le logiciel imposé ne couvre qu'un tiers du travail réel, et les salariés comblent l'écart par des contournements qui n'appartiennent qu'à eux. Puis une technologie est arrivée qui donne un moteur à ces contournements. Ce chapitre établit un fait : la rencontre a déjà eu lieu. Massivement, silencieusement, sans autorisation. Le phénomène a même un nom dans la littérature anglophone : le BYOAI — *Bring Your Own AI* — sur le modèle du BYOD qui désignait, il y a quinze ans, l'irruption des téléphones personnels au bureau.

## L'ampleur, chiffres en main

Le chiffre de référence vient de l'enquête annuelle Work Trend Index publiée par Microsoft et LinkedIn en 2024 : 78 % des utilisateurs d'IA en entreprise apportent leurs propres outils au travail[^3-1]. Pas les outils fournis, validés, contractualisés par leur employeur — les leurs : un compte personnel ChatGPT, Claude ou Gemini, ouvert avec une adresse privée, utilisé pour produire du travail professionnel.

Autour de ce chiffre pivot, les enquêtes sectorielles convergent : la grande majorité des salariés utilisateurs d'IA le font sans validation de leur DSI ; les directions informatiques déclarent massivement que leurs salariés créent des usages, des applications et maintenant des agents plus vite que l'IT ne peut les gouverner ; et une minorité seulement des salariés dit avoir reçu des consignes claires sur l'usage de l'IA dans son rôle. La télémétrie des éditeurs de sécurité, à prendre avec la prudence qui s'impose pour des chiffres de vendeurs, donne l'ordre de grandeur du paysage : plusieurs centaines d'applications d'IA générative distinctes détectées dans une grande entreprise typique, et des violations de politique de données quotidiennes[^3-2].

On peut discuter chaque chiffre. On ne peut pas discuter la direction : ce n'est pas un frémissement, c'est une adoption de masse — plus rapide que celle du cloud, plus rapide que celle du mobile[^3-3]. Et il faut relire cette adoption à la lumière du chapitre 1 : qui sont ces 78 % ? Pas les tire-au-flanc. Apporter son IA demande de l'initiative, du bricolage, l'envie de mieux faire son travail. Ce sont vos détenteurs de capital de contournements — les mêmes qui tenaient déjà l'entreprise à la machine à café — qui viennent de s'équiper. Le Shadow AI n'est pas une pathologie des salariés médiocres ; c'est le prolongement motorisé de la colle humaine, portée par les meilleurs.

## Pourquoi l'interdiction a déjà perdu

La réaction réflexe — bloquer les domaines des services d'IA au niveau du proxy d'entreprise — a été essayée à grande échelle, et son échec est documenté au point d'être devenu un lieu commun des conférences de sécurité. Les voies de contournement sont structurelles, pas anecdotiques : le compte personnel sur le téléphone personnel, hors de portée de tout proxy ; les extensions de navigateur ; et surtout l'IA embarquée — chaque SaaS déjà autorisé dans l'entreprise ajoute, trimestre après trimestre, ses propres fonctions d'IA générative, si bien que "bloquer l'IA" reviendrait à bloquer des outils déjà sous contrat.

Mais l'argument décisif n'est pas technique, il découle du chapitre 1. L'interdiction suppose que l'usage est un caprice qu'on peut éteindre. Or l'usage répond aux deux tiers de travail réel que le SI ne couvre pas. Bloquer l'outil ne supprime pas le besoin ; ça pousse le besoin vers des voies moins visibles. L'interdiction ne réduit pas le Shadow AI — elle le fabrique, exactement comme le logiciel imposé fabriquait la recette de cuisine. Même mécanique, nouvelle génération.

## Les six réponses du marché

Face à ce constat, un marché entier s'est structuré. Si vous êtes DSI ou RSSI, on vous a probablement déjà vendu — ou tenté de vous vendre — l'une des six stratégies suivantes. Elles méritent chacune un examen honnête, car chacune contient quelque chose de juste. Et chacune rate l'essentiel.

**Interdire.** On vient de le voir : essayé, contourné, contre-productif. Plus personne ne le recommande seul — y compris les vendeurs de blocage, reconvertis dans la "visibilité".

**Surveiller.** Le segment le plus actif : des plateformes qui détectent les usages d'IA dans les flux réseau, inventorient les applications, inspectent les prompts. La promesse est la visibilité, et elle a une valeur réelle — on ne gouverne pas ce qu'on ne voit pas. Deux limites. Technique d'abord : l'inspection réseau rate précisément ce qui prolifère — applications natives, comptes personnels, IA embarquée, agents. Juridique ensuite, et massive en droit français : inspecter le contenu que produit un salarié dans le cadre de son activité intellectuelle touche à la surveillance des communications, terrain où la jurisprudence est dense et le contrôle de proportionnalité sévère — le chapitre 14 y reviendra longuement. Philosophiquement surtout : cette stratégie traite le salarié comme une menace. Le chapitre 1 a montré qu'il est plutôt le diagnostiqueur le plus fiable des lacunes du SI.

**Canaliser.** Faire passer les flux d'IA par un point de contrôle — une gateway — qui filtre, anonymise, journalise. Techniquement, c'est la brique la plus intéressante du paysage, et le chapitre 10 montrera qu'elle est largement réutilisable. Mais vendue seule, c'est de la tuyauterie sans doctrine : elle dit comment faire transiter les flux, jamais ce qui a le droit de transiter, vers quoi, pour faire quoi. Le tuyau ne remplace pas l'architecture.

**Fournir l'outil béni.** Donner à tous un Copilot, un ChatGPT Enterprise, un Claude d'entreprise — la réponse majoritaire des grandes organisations, et la plus raisonnable en première intention. Son talon d'Achille est dans les chiffres mêmes : les salariés apportent leur propre IA *aussi* dans les entreprises qui fournissent un outil officiel. Pourquoi ? Le chapitre 2 a donné la réponse : leur besoin n'est pas "de l'IA" en général, c'est la couverture de *leurs* déviations — leurs données, leurs formats, leurs enchaînements. L'outil béni est un générique de plus, excellent sur le nominal, aveugle aux 65 %. On reconduit le problème au lieu de le résoudre.

**Enfermer la production dans une plateforme.** Puisque les salariés construisent des outils, offrons-leur un atelier surveillé : plateformes low-code augmentées d'IA, environnements de "vibe coding gouverné". La gouvernance y est réelle — et le chapitre 11 montrera que ces plateformes ont inventé des mécanismes précieux. Mais l'atelier surveillé reproduit, un cran plus haut, les deux défauts déjà rencontrés : le plafond de contraintes du low-code (le chapitre 4 y revient) et la captivité du chapitre 1 — vos salariés construiront leurs outils dans un runtime propriétaire qu'ils ne pourront pas quitter. On répond à la captivité par une captivité mieux meublée.

**Certifier.** Encadrer le tout par des référentiels : systèmes de management de l'IA, cadres de gestion des risques, préparation réglementaire. Nécessaire — le chapitre 14 montrera même que c'est une opportunité. Mais un référentiel décrit des processus ; il ne dessine pas une architecture. On peut être certifié et n'avoir rien résolu.

## La case vide

Prenez du recul sur les six stratégies. Interdire, surveiller, canaliser : contrôler un flux. Fournir, enfermer : distribuer un produit. Certifier : documenter un processus. Ce n'est pas un hasard si le marché s'arrête là : une enquête menée en 2026 auprès de huit cents dirigeants français[^3-4] montre que seuls 28 % d'entre eux estiment que l'IA impose de revoir l'organisation dans son ensemble — pour la grande majorité, l'IA reste un outil d'optimisation de l'existant, et les six stratégies sont les produits logiques de cette conviction. Fait notable : dans les grandes entreprises, la proportion s'inverse — deux tiers des dirigeants y jugent une refonte globale nécessaire. Ceux qui ont le plus pratiqué ont déjà compris où était le vrai chantier. Aucune — aucune — ne pose la seule question qui découle des trois premiers chapitres : **qu'est-ce que le système d'information lui-même devrait exposer, garantir et interdire pour que l'IA apportée par les salariés produise du spécifique gouverné au lieu du chaos ?**

C'est la case vide du marché, et c'est le programme de ce livre. Non pas une septième défense contre le BYOAI, mais l'étage au-dessus : l'architecture d'accueil. Elle exige de répondre à des questions qu'aucun produit sur étagère ne tranche à votre place : où passe exactement la ligne entre ce qui reste au SI et ce qui appartient au salarié ; comment une IA prouve pour le compte de qui elle agit ; quelles actions doivent rester à jamais hors de sa portée ; comment un outil individuel devient, s'il le mérite, un outil commun ; et qui absorbe la complexité que tout cela engendre.

Chacune de ces questions a une réponse précise. Mais avant de les dérouler, il faut solder un débat économique — car tout ce qui précède repose sur une affirmation qu'un DSI expérimenté a le droit d'accueillir avec scepticisme : que produire du logiciel spécifique serait devenu bon marché. C'est vrai, c'est mesuré, et c'est plus subtil que ce que les vendeurs racontent. Le chapitre suivant sépare ce qui s'est réellement effondré de ce qui n'a pas bougé.

## Notes et sources

[^3-1]: Microsoft & LinkedIn, *Work Trend Index Annual Report* 2024 : 78 % des utilisateurs d'IA au travail apportent leurs propres outils (phénomène « BYOAI »). ~ Formulation et périmètre exacts à revérifier en source primaire avant publication.

[^3-2]: Chiffres rendus volontairement qualitatifs dans le texte car issus de sources éditeurs et de sondages : ~ 82 % des DSI déclarent que les salariés créent applications et agents plus vite que l'IT ne peut les gouverner ; ~ 21 % seulement des salariés ont reçu des consignes IA claires pour leur rôle (Work Trend Index / presse RH-tech) ; télémétrie des éditeurs de sécurité : ~ plusieurs centaines d'applications d'IA distinctes par grande entreprise, violations quotidiennes (LayerX, Cloud Security Alliance, Retool — *State of AI Governance 2026*). Valeurs précises et datées dans la fiche d'état de l'art ; à ne réintroduire chiffrées que re-sourcées vers l'étude primaire.

[^3-3]: ⚠ « Adoption plus rapide que le cloud et le mobile » : affirmation plausible mais non sourcée à ce jour — à étayer par une courbe d'adoption datée, ou à adoucir, avant publication.

[^3-4]: Enquête Kéa × OpinionWay, *AI Readiness des dirigeants français*, 2026 (~ 802 dirigeants) : ~ 28 % estiment que l'IA impose de revoir l'organisation dans son ensemble ; ~ 66 % dans les grandes entreprises. Via *Le Monde Informatique*, 10/07/2026. ⚠ Source primaire (méthodologie, formulations exactes) à lire avant citation.

---

## Notes de rédaction (hors manuscrit)

- ~ **78 % (Work Trend Index 2024, Microsoft + LinkedIn)** : seul chiffre cité nominalement dans le chapitre — vérifier la formulation exacte de l'enquête avant publication (périmètre : "AI users bring their own AI tools to work").
- Les autres chiffres (82 % des DSI, 21 % de consignes, 665 apps, 223 violations/mois) sont volontairement **dé-chiffrés** dans le texte ("la grande majorité", "une minorité", "plusieurs centaines") car sources vendeurs — les valeurs précises restent dans [byoai-shadow-ai-marche](../06-etat-de-lart/byoai-shadow-ai-marche.md) avec marqueurs, à réintroduire seulement si re-sourcées.
- L'affirmation "adoption plus rapide que le cloud/mobile" : ⚠ plausible mais non sourcée ici — vérifier ou adoucir avant publication.
- Les six stratégies : détail et fournisseurs dans [byoai-solutions-existantes](../06-etat-de-lart/byoai-solutions-existantes.md) ; les noms de produits/vendeurs sont absents du chapitre (ils vont en Annexe A) pour tenir la stratégie anti-obsolescence.
- Renvois posés : ch. 4 (plafond low-code, économie), ch. 10 (gateways), ch. 11 (mécanismes des plateformes), ch. 14 (proportionnalité, référentiels). Vérifier que chaque promesse est tenue à la rédaction.
- La "case vide" formule les cinq questions dans l'ordre des chapitres 6, 8, 9, 11, 12 — c'est l'annonce de plan déguisée.
- Grille lecteur : répond à la question RSSI ("pourquoi mon blocage ne marche pas, que vaut ce qu'on me vend") sans hostilité envers les fournisseurs — chaque stratégie a "quelque chose de juste".
- Sources ontologie : [byoai-shadow-ai-marche](../06-etat-de-lart/byoai-shadow-ai-marche.md), [byoai-solutions-existantes](../06-etat-de-lart/byoai-solutions-existantes.md).
