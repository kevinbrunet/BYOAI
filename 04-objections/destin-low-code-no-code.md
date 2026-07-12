# Objection — Pourquoi le BYOIA échapperait-il au destin du low-code/no-code ?

## L'objection (la numéro un de tout DSI expérimenté)

Le low-code/no-code et le "citizen developer" promettaient exactement la même chose : le métier produit son outil, l'IT garde la structure. Ils ont largement déçu. Pourquoi cette fois serait différente ?

## La réponse : le plafond de contraintes

Le no-code/low-code repose sur des **contraintes pour simplifier**. Pour dessiner un process dans n8n, on adopte les règles de fonctionnement de l'outil — et ces règles ne sont pas vraies partout. Très vite on se retrouve bloqué, et on doit contourner : le contournement se fait hors de l'outil, dans la douleur, ou pas du tout.

C'est un défaut **structurel**, pas un défaut de maturité : simplifier en contraignant l'espace exprimable garantit qu'une partie des besoins réels sortira de cet espace. Plus le besoin est spécifique — précisément ce qu'on cherche à servir — plus vite on touche le plafond. Le low-code échoue donc en proportion exacte de la spécificité du besoin : il est le pire là où on en avait le plus besoin.

Le BYOIA ne simplifie pas en contraignant : le spécifique est **écrit en code pur**. L'espace exprimable est le langage entier. La complexité n'est pas absorbée par une restriction du problème, elle est absorbée par le générateur (le harnais IA). Il n'y a pas de plafond au-delà duquel il faut "sortir de l'outil" — le code pur *est* déjà dehors.

## Trois différences structurelles supplémentaires

1. **La captivité en moins.** Un flow n8n ou Power Automate vit dans un runtime propriétaire : illisible hors de l'outil, non portable, non versionnable proprement — une nouvelle [captivité logicielle](../01-concepts/captivite-logicielle-happy-path-social.md) qui remplace l'ancienne. Le code pur est inspectable, versionnable dans Git, portable, et surtout **régénérable** : si l'outil de génération disparaît, le code reste.
2. **On ne force plus le métier à programmer.** Le citizen developer devait penser comme un programmeur dans un langage visuel souvent pire que le code. Le BYOIA ne demande pas ça : le métier exprime son besoin en langage naturel, et la production peut être **déléguée à un développeur de terrain, proche des utilisateurs** ([développeur-harnais](../01-concepts/equipe-agile-developpeur-harnais.md)). On casse le silo DSI non pas en transformant le métier en développeur, mais en rapprochant le développeur du métier.
3. **L'économie a réellement changé.** Le low-code déplaçait l'outil de production mais pas l'économie : le temps de spécialiste restait cher, donc on rationnait, donc on re-priorisait, donc on re-uniformisait. L'IA effondre le coût de production lui-même ([argument 1](../02-arguments/01-effondrement-economie-echelle-code.md)) — c'est la condition qui manquait aux promesses précédentes.

## Le résidu honnête de l'objection

Le DSI répliquera : "du code pur produit hors DSI, c'est ingérable en maintenance". La réponse n'est pas de nier, elle est déjà dans l'architecture de la série :

- le spécifique utilisateur est **jetable et régénérable** — on ne maintient pas, on regénère ;
- ce qui mérite de durer entre dans le [cycle de promotion](../01-concepts/cycle-promotion-specifique.md) avec transfert de maintenance et mise au standard ;
- la [fenêtre de complexité](../01-concepts/cycle-promotion-specifique.md) borne explicitement ce que la capacité de maintenance peut tenir.

⚠ Point à ne pas esquiver : le "développeur de terrain" ressemble à ce que le mouvement DevOps/SRE a fait en intégrant l'ops dans les équipes. Analogie porteuse, mais le DSI y verra aussi un risque de re-création de mini-DSI dispersées et incohérentes. La réponse est la frontière structure/interface (la structure reste unique et commune) — mais elle suppose que la [doctrine de la frontière](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) soit tranchée. Cette objection-ci ne tient debout que si la question 14 est résolue.

## Lien avec le reste de la série

- [Générique vs spécifique](../01-concepts/generique-vs-specifique.md) — le low-code était une tentative de servir le spécifique avec un outil générique : la contradiction était interne
- [Frontière structure/interface](../01-concepts/frontiere-structure-interface.md) — ce que l'IT garde, ce que le terrain produit
- [Questions-livre, question 3](../00-meta/questions-livre.md) — cette page y répond
