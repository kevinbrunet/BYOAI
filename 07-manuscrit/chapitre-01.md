# Chapitre 1 — Le logiciel qu'on ne peut pas quitter

Faites le test. Fermez les yeux et citez le pire logiciel que vous utilisez régulièrement. Pas le plus laid, pas le plus lent — le pire : celui qui vous fait perdre du temps chaque semaine, celui dont vous connaissez les bugs par leur prénom, celui que vous ouvrez en soupirant.

Vous venez de penser à un logiciel d'entreprise. Un outil de gestion des temps, un CRM, un portail de notes de frais, un ERP. Personne ne répond jamais "Spotify" ou "Google Maps" à cette question. Et ce n'est pas un hasard statistique.

L'explication paresseuse serait que les éditeurs de logiciels d'entreprise sont moins compétents que les autres. C'est faux, et ce n'est pas le sujet. La vraie différence tient en une phrase : un logiciel que vous utilisez dans votre vie personnelle, s'il ne vous convient pas, vous en changez. Un logiciel d'entreprise, vous le subissez. La qualité perçue d'un logiciel n'est pas seulement une propriété du logiciel — c'est une propriété de votre liberté d'en partir.

## Sortie, prise de parole, et la troisième voie

Il existe un cadre classique pour penser cette situation. Dans *Exit, Voice, and Loyalty* (1970), l'économiste Albert Hirschman[^1-1] décrit les deux réactions possibles d'un individu face à une organisation ou un produit qui se dégrade : la sortie — on part, on achète ailleurs — et la prise de parole — on reste et on proteste pour obtenir un changement.

Appliquez ce cadre au poste de travail. La sortie est impossible : l'outil est imposé, l'utiliser conditionne la paie, les congés, la production. La prise de parole existe en théorie — remontées utilisateurs, tickets, enquêtes de satisfaction — mais chacun a appris par l'expérience ce qu'elle pèse : qui, dans une carrière, a vu sa remontée utilisateur modifier un ERP ? Le canal existe ; la boucle de rétroaction, non. L'éditeur vend à la direction des achats, pas à l'utilisateur ; le contrat court sur des années ; la roadmap arbitre entre des milliers de clients. La voix se perd dans des couches que personne ne traverse.

Quand la sortie est impossible et la voix inefficace, Hirschman prévoyait la loyauté résignée. Il manquait à son modèle une troisième voie, que tout salarié connaît sans l'avoir jamais nommée : le contournement. On ne part pas, on ne proteste plus — on s'arrange.

## La colle humaine

Regardez honnêtement le système d'information de n'importe quelle organisation de taille moyenne. Ce n'est pas une cathédrale, c'est un empilement : des logiciels achetés à des années d'écart, à des éditeurs différents, sur des hypothèses différentes, qui s'interconnectent mal ou pas du tout. Entre les briques, il y a des trous. Et ces trous ne sont pas comblés par de l'intégration — l'intégration coûte cher, elle attendra le prochain schéma directeur. Ils sont comblés par de la colle humaine.

La colle humaine, vous la connaissez. C'est la recette de cuisine passée à la machine à café : "quand l'export plante, tu réenregistres en CSV et tu le repasses par l'ancien module." C'est la procédure de dix-sept étapes écrite un jour de bonne volonté dans un wiki que personne ne maintient et que personne ne consulte, ou dans un SharePoint dont plus personne ne connaît l'arborescence. C'est surtout le collègue qui sait — celui qu'on va voir directement, parce que c'est plus rapide et plus fiable que toute la documentation réunie.

Il faut prendre la mesure de ce que cela signifie : le fonctionnement réel de l'entreprise n'est écrit nulle part. La documentation décrit un système théorique ; le système effectif est une tradition orale, transmise de poste en poste, faite de ouï-dire et d'essais-erreurs. Chaque nouvel arrivant refait le même apprentissage : tenter, se tromper, déranger un collègue, noter un truc dans un coin, jusqu'à trouver — non pas la bonne façon de faire, il n'y en a pas — mais une façon qui ne déclenche ni erreur, ni conflit, ni question de la hiérarchie.

C'est ainsi que se fabrique ce qu'on pourrait appeler le happy path d'un poste : le chemin qui ne fait pas de vagues. Il n'a été conçu par personne. Il s'est sédimenté, par évitements successifs, comme un sentier se dessine dans un champ à force de pas. Le chapitre suivant montrera que cette sédimentation n'est pas une anomalie locale mais une nécessité statistique — que le chemin nominal prévu par le logiciel est, mathématiquement, minoritaire dans les usages réels. Retenons pour l'instant le fait : ce que l'organisation appelle "la procédure" et ce que les gens font pour que le travail sorte sont deux choses différentes, et la seconde n'appartient qu'à eux.

## La résistance au changement est un calcul juste

Ce détour éclaire un mystère managérial ancien : pourquoi les salariés résistent-ils au changement d'outil, même quand le nouvel outil est objectivement meilleur ?

Parce qu'ils ont raison.

Chaque recette de cuisine, chaque contournement, chaque "je connais quelqu'un au service comptable qui peut débloquer ça" représente un capital. Un capital invisible — il n'apparaît dans aucun bilan de compétences, aucune fiche de poste — mais un capital réel, acquis lentement, à un coût personnel non négligeable. Changer d'outil détruit ce capital d'un coup. Et le coût de sa reconstitution — un nouveau cycle de tâtonnements, d'erreurs, de dérangements — retombe intégralement sur le salarié, sans jamais figurer dans le business case du projet. Le ROI de la migration compte les licences, les jours-homme d'intégration, la formation officielle de deux demi-journées. Il ne compte jamais les six mois pendant lesquels quarante personnes retrouveront, à tâtons, comment faire sortir le travail.

Ce que le management appelle "résistance au changement" est, vu du poste de travail, une évaluation correcte d'un coût que l'organisation refuse de voir. Les salariés ne défendent pas l'ancien outil — personne n'aime l'ancien outil, on vient de voir pourquoi. Ils défendent leur capital de contournements. Nuance décisive : elle signifie que la résistance ne vise pas le changement, mais la destruction non compensée.

## La recette de cuisine vient de trouver un moteur

Tout ce qui précède décrit un état ancien et stable. Des décennies de logiciel d'entreprise ont produit des décennies de colle humaine, et l'équilibre — inconfortable mais tenable — s'était installé : le SI théorique pour l'audit, la tradition orale pour le travail réel.

Ce qui vient de changer, c'est qu'un salarié n'a plus besoin de se contenter de *noter* sa recette de cuisine. Il peut désormais la donner à exécuter. L'assistant IA générative qu'il utilise — le plus souvent le sien, sur son compte personnel, hors de toute validation — sait lire le fichier mal formé, refaire l'export planté, remplir le formulaire à sa place, croiser les deux extractions que le SI n'a jamais su joindre. La recette de cuisine, artefact oral et fragile, devient un outil qui tourne.

Il faut voir ce moment pour ce qu'il est. Ce n'est pas l'irruption d'une technologie exotique dans un monde sain ; c'est la rencontre d'une technologie nouvelle avec un besoin vieux de quarante ans, massif, documenté à chaque machine à café. Les chiffres d'adoption sauvage de l'IA en entreprise — nous les verrons au chapitre 3 — ne mesurent pas une mode. Ils mesurent la pression accumulée de tous ces contournements qui attendaient un moteur.

Et c'est ici que ce livre choisit son camp, ou plutôt refuse le choix qu'on lui propose. Le réflexe institutionnel face à ce phénomène est défensif : bloquer, surveiller, encadrer — traiter le salarié qui s'outille comme un risque ambulant. Le réflexe inverse, libertaire, serait de laisser faire — et de découvrir dans deux ans un archipel d'outils non testés, non tracés, accrochés aux données de l'entreprise. Ce livre soutient que l'alternative est fausse. Le salarié qui contourne a raison sur le diagnostic : le logiciel imposé ne couvre pas son travail réel. La DSI qui s'inquiète a raison sur l'exigence : certaines garanties — la cohérence des données, la traçabilité, la conformité — ne sont pas négociables. Toute la suite de ce livre consiste à donner à ces deux raisons une architecture commune, au lieu de les laisser s'affronter.

Mais avant l'architecture, il faut finir le diagnostic. Car si le logiciel d'entreprise déçoit si uniformément, ce n'est pas seulement parce qu'on ne peut pas le quitter. C'est parce qu'il repose sur une erreur de probabilités que tout le monde commet — et qu'elle est réparable.

## Notes et sources

[^1-1]: Albert O. Hirschman, *Exit, Voice, and Loyalty: Responses to Decline in Firms, Organizations, and States*, Harvard University Press, 1970 (trad. fr. *Défection et prise de parole*, Fayard, 1995). ✓ Ouvrage et thèse *exit/voice*. La « troisième voie » — le contournement — est une extension propre à ce livre, pas une thèse de Hirschman. ~ Référence exacte de l'édition française à confirmer aux notes finales.

---

## Notes de rédaction (hors manuscrit)

- ✓ Hirschman, *Exit, Voice, and Loyalty*, Harvard University Press, 1970 — référence exacte à vérifier en édition française (« Défection et prise de parole », Fayard) au moment des notes finales.
- Le "contournement" comme troisième voie est notre extension du cadre, pas une thèse de Hirschman — formulé comme tel dans le texte ("il manquait à son modèle").
- Les chiffres BYOAI sont volontairement absents de ce chapitre (renvoi ch. 3) pour garder l'ouverture sans données à défendre.
- La promesse "erreur de probabilités réparable" en clôture est le pont vers le ch. 2 (happy path).
- Grille lecteur : le chapitre répond à la question DSI ("pourquoi mes utilisateurs détestent-ils mon SI alors qu'il fonctionne ?") et prépare l'empathie plutôt que la culpabilisation — aucun reproche à la DSI dans ce chapitre, le "coupable" est structurel (captivité + achat/usage dissociés).
- Source ontologie : [captivite-logicielle-happy-path-social](../01-concepts/captivite-logicielle-happy-path-social.md).
