# Chapitre 12 — La fenêtre de complexité

Le cycle du chapitre précédent a un point de fuite. La montée est mesurée, la descente est légitime — mais qu'est-ce qui *oblige* à descendre ? Si chaque promotion se justifie individuellement, le périmètre de considération grossit indéfiniment, chaque évolution du socle coûte un peu plus cher que la précédente, et l'on se réveille dans dix ans avec le SI rigide que ce livre promettait d'éviter. Il manque une contrainte globale : un budget.

Posons-le d'emblée, car c'est l'idée de ce chapitre : toute organisation a une **fenêtre de complexité** — la quantité maximale de complexité que sa capacité de maintenance peut tenir. Cette fenêtre a toujours existé. Le SI historique en avait une aussi ; simplement, elle n'était déclarée nulle part, personne ne la mesurait, et on ne la découvrait qu'en la crevant : le projet qui s'enlise sans raison apparente, la refonte déclarée impossible, la modification triviale chiffrée à six mois. Chaque DSI a vécu ce moment où l'organisation apprend, brutalement et sans préavis, qu'elle avait un budget de complexité et qu'il est dépassé depuis des années. La proposition n'est donc pas d'inventer une contrainte — c'est de rendre explicite, mesurée et arbitrée une contrainte qui, restée implicite, ne se manifeste que par des catastrophes.

## Un budget, deux leviers

La mécanique tient en trois phrases. Chaque cas pris en compte — chaque outil promu, chaque règle exécutable, chaque intégration garantie — **consomme** de la fenêtre. La fenêtre est **finie** : elle vaut ce que vaut la capacité de maintenance disponible à l'étage considéré — celle d'une équipe pour ses outils d'équipe, celle de l'entreprise pour son socle. Et quand le périmètre dépasse la fenêtre, il n'existe que **deux leviers** : agrandir la fenêtre — renforcer l'équipe — ou réduire le périmètre — rétrograder, élaguer. Il n'y a pas de troisième option. "Tenir en serrant les dents" n'est pas un levier : c'est le nom qu'on donne au dépassement pendant qu'il creuse.

L'ingénierie logicielle a déjà éprouvé cette forme de contrainte, deux fois. Les limites d'encours du kanban : on borne explicitement le travail en cours, non parce que la limite est agréable, mais parce qu'une limite déclarée force l'arbitrage — terminer avant de commencer — là où l'absence de limite laisse tout s'empiler silencieusement. Et les budgets d'erreur du SRE : un service a droit à une quantité chiffrée d'indisponibilité ; tant qu'il est dans son budget, on innove ; budget crevé, tout s'arrête et l'on fiabilise. Dans les deux cas, la vertu n'est pas dans le chiffre exact — elle est dans l'existence d'un seuil explicite qui transforme une dégradation continue et invisible en décision discrète et assumée. La fenêtre de complexité est ce même geste, appliqué à ce que l'organisation garantit[^12-1].

## Mesurer ce qu'un cas consomme

Un budget exige une unité. C'est l'objection qu'un DSI fera dans la minute — "votre fenêtre, elle se mesure en quoi ?" — et elle mérite une réponse précise, car cinquante ans de littérature l'ont préparée.

Première idée, la plus importante : **la complexité qui compte est celle qu'on touche**. Un outil promu au code médiocre mais posé sur un périmètre gelé, que personne ne modifie jamais, ne consomme presque rien — il dort. Le même outil accroché à un référentiel qui change chaque semaine consomme énormément : chaque changement doit le considérer. L'école d'analyse dite comportementale du code a établi ce principe en croisant deux dimensions que les métriques classiques regardaient séparément : la complexité d'un composant et sa **fréquence de modification**. Les zones critiques — les hotspots — sont à l'intersection : complexes ET souvent touchées. C'est là, et presque seulement là, que la maintenance se dépense[^12-2].

Deuxième idée : le coût d'un cas se lit dans les **dépendances**. Des travaux académiques sur les matrices de dépendances ont produit une mesure au nom parlant — le *coût de propagation* : pour un point du système, quel pourcentage du reste est potentiellement affecté quand ce point change. C'est très exactement le "coût de prise en compte" du chapitre 11, rendu calculable : un outil promu couplé à trois API stables a un coût de propagation faible ; un outil tissé dans douze référentiels vivants est un consommateur vorace[^12-3].

La consommation d'un cas promu se formule alors simplement : ce qu'il touche, pondéré par la fréquence à laquelle ce qu'il touche change. Deux données que l'outillage moderne — dépôts de code, journaux d'API, la gateway du chapitre 10 — produit déjà sans effort supplémentaire.

## Mesurer ce que l'organisation tient

L'autre moitié du budget est la taille de la fenêtre — et elle a deux planchers, un technique et un humain.

Le plancher technique s'exprime en temps : les méthodes industrielles d'évaluation de la dette convertissent l'état d'un périmètre en **jours de remédiation** — combien de jours-homme pour ramener le code au standard. L'unité est parlante, budgétable, et normalisée : la mesure automatisée de la maintenabilité fait l'objet d'un standard ISO[^12-4], ce qui n'est pas un détail rhétorique — le jour où la fenêtre de complexité arrive en comité d'architecture, "c'est une lubie de consultant" ne survit pas à "c'est une grandeur normalisée ISO". La capacité, en face, est connue de tout gestionnaire : les jours-homme de maintenance que l'équipe peut réellement consacrer, une fois retranché le reste.

Le plancher humain est moins familier et plus dur : la **charge cognitive d'équipe**. Une équipe a une capacité cognitive finie — la quantité de choses qu'elle peut comprendre, garder en tête et faire évoluer sans se dégrader. Le courant d'organisation qui a popularisé cette notion en a fait un principe de conception : on dimensionne les périmètres de responsabilité pour qu'ils tiennent dans la capacité cognitive de l'équipe, et non l'inverse[^12-5] — avec des questionnaires d'auto-évaluation simples pour la sonder ("dans quelle mesure votre équipe comprend-elle, teste-t-elle, fait-elle évoluer sereinement ce dont elle a la charge ?"). Le point décisif : le plancher humain peut être crevé alors que le plancher technique tient. Une dette de remédiation stable mais une équipe qui déclare ne plus comprendre son périmètre est une fenêtre dépassée — les incidents suivront, avec quelques trimestres de retard.

## Le tableau de bord et le geste

Assemblons. La fenêtre de complexité d'un étage se pilote avec trois nombres, tous productibles avec l'outillage existant : la **consommation** du périmètre — la somme des coûts de considération, propagation pondérée par la fréquence de changement ; la **capacité** — jours de remédiation soutenables, bornés par la charge cognitive déclarée ; et le **signal** — la dérive de l'un vers l'autre : dette qui croît plus vite que la capacité, ou auto-évaluation qui décroche.

Que ce dispositif soit rare, l'enquête française déjà croisée deux fois le confirme : un dirigeant sur dix seulement déclare disposer d'un pilotage avancé de ses projets d'IA — tableaux de bord, intégration aux modèles financiers — et moins d'un tiers a évalué les bénéfices obtenus[^12-6]. La fenêtre n'est pas une exigence de plus posée sur les équipes : c'est le dispositif manquant que tout le monde cherche, construit à partir de données que l'architecture produit déjà.

Quand le signal passe au rouge, le geste est celui du chapitre 11, mais il cesse d'être facultatif : agrandir ou élaguer. Et les métriques d'usage désignent les candidats à l'élagage sans débat de comité : les cas à forte consommation et faible usage — l'outil tissé partout que plus grand monde n'utilise — sont, littéralement, le gras du périmètre. La fenêtre transforme la question la plus politique de l'informatique d'entreprise — "peut-on enfin supprimer ceci ?" — en une lecture de tableau : ceci consomme tant, sert si peu, et le budget est crevé.

Restons honnête sur les limites, car un lecteur outillé les verra. Il n'existe pas d'unité standard de "la complexité" — le coût de propagation, les jours de remédiation, la charge déclarée sont des **approximations**, chacune discutable, et leurs valeurs absolues se comparent mal d'une organisation à l'autre. Mais l'objection manque la cible : le SI historique n'a pas été rigidifié par un défaut de précision de ses mesures — il l'a été par l'absence totale de mesure et de seuil. Un budget imparfait, déclaré et suivi en tendance, bat sans appel un budget parfait qui n'existe pas. La fenêtre n'a pas besoin d'être juste au point près ; elle a besoin d'exister, d'être visible, et que quelqu'un ait le mandat d'agir quand elle se ferme.

## Quelqu'un

"Que quelqu'un ait le mandat" — voilà le mot qui manque à toute cette quatrième partie, et il est temps de le regarder en face. Des métriques d'usage, un cycle, une fenêtre : rien de tout cela ne décide. Quelqu'un lit les tendances, repère les convergences, propose les promotions, assume les élagages. Quelqu'un pilote les harnais, et répond de ce qu'ils produisent. Quelqu'un, face à des centaines d'outils qui naissent et meurent, cherche les motifs — le même problème résolu douze fois, le même trou dans le socle contourné par trois équipes. Ce ne sont pas les mêmes "quelqu'un", et aucun des trois n'existe dans l'organigramme d'aujourd'hui. Le chapitre suivant les dessine — et répond à la question que tout ce livre repousse depuis le chapitre 2 : que deviennent les développeurs, et les métiers, dans une entreprise qui fonctionne ainsi ?

## Notes et sources

[^12-1]: ✓ Précédents de contrainte explicite : limites d'encours (*WIP limits*) du kanban ; budgets d'erreur (*error budgets*) du SRE (Google). Dans les deux cas, un seuil déclaré force l'arbitrage qu'une dégradation continue laisse invisible.

[^12-2]: ✓ Analyse comportementale du code et *hotspots* (complexité × fréquence de modification) : CodeScene / Adam Tornhill. Nom en Annexe A.

[^12-3]: *Coût de propagation* (*propagation cost*) via matrices de dépendances (*Design Structure Matrix*) : ~ MacCormack, Baldwin & Rusnak — référence exacte à revérifier avant publication.

[^12-4]: ✓ Mesure normalisée de la maintenabilité : ISO/IEC 5055 (qualité du code source, mesure automatisée). ✓ Méthode d'évaluation de la dette en jours de remédiation : SQALE. Noms en Annexe A.

[^12-5]: ✓ Charge cognitive d'équipe comme critère de dimensionnement des périmètres : *Team Topologies* (Matthew Skelton & Manuel Pais). Nom en Annexe A.

[^12-6]: Enquête Kéa × OpinionWay 2026 (voir ch. 3) : ~ 10 % des dirigeants déclarent un pilotage avancé de leurs projets d'IA ; ~ moins d'un tiers ont évalué les bénéfices. ⚠ Source primaire à revérifier.

---

## Notes de rédaction (hors manuscrit)

- Sources : [cycle-promotion-specifique — pilotage](../01-concepts/cycle-promotion-specifique.md), [mesure-complexite-fenetre](../06-etat-de-lart/mesure-complexite-fenetre.md). L'opérationnalisation en trois nombres (consommation/capacité/signal) reprend la proposition du fichier état de l'art.
- Anonymisation des références dans le corps (noms → Annexe A) : "l'école d'analyse comportementale du code" = CodeScene/Tornhill (hotspots ✓) ; "travaux académiques sur les matrices de dépendances" = MacCormack/Baldwin/Rusnak, propagation cost (✓ de mémoire, à re-vérifier la référence exacte) ; "méthodes industrielles d'évaluation de la dette" = SQALE (✓) ; "standard ISO" = ISO/IEC 5055 (✓) ; "le courant d'organisation" = Team Topologies, Skelton & Pais (✓).
- L'argument "grandeur normalisée ISO ne survit pas à lubie de consultant" : arme rhétorique pour le lecteur en comité — volontairement explicite.
- La section limites ("budget imparfait déclaré bat budget parfait implicite") désamorce l'objection de l'unité — c'est la réponse actée au point 8 des [questions-restantes](../00-meta/questions-restantes.md) ; les seuils précis restent ouverts (dit en creux : "suivi en tendance").
- Formules candidates : "tenir en serrant les dents n'est pas un levier — c'est le nom qu'on donne au dépassement pendant qu'il creuse" ; "la complexité qui compte est celle qu'on touche" ; "le gras du périmètre" ; "elle n'a pas besoin d'être juste, elle a besoin d'exister".
- La chute introduit les trois rôles du ch. 13 sans les nommer (l'arbitre, le pilote, l'épidémiologiste) — vérifier que le ch. 13 les nomme dans cet ordre.
- Grille lecteur : CTO ("comment je pilote, avec quels nombres ?") — livrable : le tableau de bord à trois nombres.
