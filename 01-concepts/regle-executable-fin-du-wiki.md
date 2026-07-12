# La règle exécutable — à l'ère de l'IA, le wiki d'entreprise est fini

## Le principe (formulation de Kevin, 2026-07-11)

À l'ère de l'IA, le wiki d'entreprise, c'est fini. **Si tu as une règle, automatise son contrôle, et donne la raison au moment où celle-ci s'active.**

## Décomposition

Trois affirmations dans cette phrase, chacune porteuse :

1. **Une règle dont le contrôle n'est pas automatisé n'existe pas.** Elle est un vœu déposé dans un document. Le chapitre 1 l'a montré : la procédure écrite dans le wiki n'est pas consultée, le fonctionnement réel est une tradition orale. Tant que la règle vit dans un texte et son application dans la bonne volonté, les deux divergent — c'est même la définition de la colle humaine.
2. **Le contrôle porte sa propre explication.** Quand la règle s'active (refus, blocage, demande de validation), elle délivre sa raison — à ce moment-là, dans ce contexte-là. La documentation n'est plus un lieu où l'on va chercher (et où l'on ne va jamais) ; c'est un message qui vient au moment exact où il est utile. Le wiki inversé : just-in-time au lieu de just-in-case.
3. **L'IA change les deux bouts de l'équation.** Avant, automatiser un contrôle coûtait cher (développer le check, le maintenir) et formuler une explication contextuelle coûtait plus cher encore — donc on écrivait un wiki, compromis économique par défaut. Maintenant, générer le contrôle est bon marché (c'est du code spécifique — précisément ce dont le coût s'effondre) et générer l'explication contextualisée est le cœur de métier d'un LLM. Le compromis wiki n'a plus de raison d'être.

## La jonction avec le reste de la série

- **Le wiki mort du chapitre 1** : c'est là que les recettes de cuisine allaient mourir. La règle exécutable est son remplacement structurel — non pas un meilleur wiki, mais la suppression du besoin de wiki pour tout ce qui est règle.
- **La doctrine ([frontière fiduciaire](../05-questions-ouvertes/doctrine-frontiere-si-interface.md))** : une règle auditable vit dans le SI — et vivre dans le SI, ça veut dire exactement ceci : contrôle automatisé + raison délivrée à l'activation + trace. Le critère 3 du test gagne sa définition opérationnelle.
- **DCB / décisions comme events ([dcb](./dcb-decisions-comme-events.md))** : la raison délivrée à l'activation n'est pas un texte figé — elle pointe vers la **décision source** (l'event qui a créé la règle, sa mission, son début, sa fin). "Refusé parce que la décision D-2024-17, prise pour telle raison, active jusqu'à telle échéance, l'exige." La règle exécutable est la projection opérationnelle du stream de décisions ; le message d'erreur devient navigable jusqu'au pourquoi.
- **[Conformité par design](./conformite-par-design.md) et [API humain-only](./delegation-agents-jwt-mtls.md)** : le régime "humain uniquement" est un cas particulier de règle exécutable — le refus technique qui s'explique ("cette action requiert un humain authentifié : décision de conformité AI Act art. 26").
- **Les précédents existent côté DSI** : ✓ policy-as-code (OPA/Rego, admission controllers Kubernetes), linters, hooks Git, DoD/DoR outillés ([git-dod-dor-dsi](../03-exemples/git-dod-dor-dsi.md)) — le monde du développement a déjà basculé : plus personne ne documente une convention de code dans un wiki, on écrit un linter. La thèse ici : ce basculement s'étend à toutes les règles de gestion de l'entreprise, parce que l'IA en effondre le coût.

## Ce que ça change pour le salarié et son IA

Double bénéfice, symétrique :

- **Pour l'humain** : il n'a plus à connaître la règle à l'avance — il la découvre au moment où elle le concerne, avec sa raison. L'apprentissage par essais-erreurs du chapitre 1 cesse d'être une errance : chaque erreur enseigne, immédiatement et avec contexte.
- **Pour l'IA du salarié** : un agent ne lit pas le wiki non plus — mais un refus d'API motivé, structuré, avec la raison en clair, est exactement ce qu'un agent sait exploiter pour corriger sa trajectoire. La règle exécutable est la seule documentation que les deux lecteurs du SI — l'humain et l'agent — consomment effectivement.

## L'économie de contexte : la productivité des deux lecteurs

Ajout (2026-07-11). Pousser la règle au fur et à mesure ne change pas seulement *où* vit la règle — ça change la quantité de contexte que chaque acteur doit porter, et donc sa productivité.

**Pour l'humain** : l'alternative au just-in-time, c'est le chargement à l'avance — formations, procédures à lire, habilitations à mémoriser — c'est-à-dire de la charge cognitive dépensée sur des règles qui ne serviront peut-être jamais, ou plus. En ne délivrant la règle qu'au moment où elle s'active, on aligne le coût d'apprentissage sur l'usage réel : on n'apprend que ce que son travail rencontre effectivement. C'est le principe UX de la *progressive disclosure*, appliqué à la norme d'entreprise. Et c'est la même économie que la [fenêtre de complexité](./cycle-promotion-specifique.md) côté organisation : la capacité cognitive est finie, la dépenser en règles dormantes est un gaspillage mesurable.

**Pour l'IA** : l'argument devient littéral — le contexte d'un agent est une fenêtre en tokens, finie et coûteuse. L'approche naïve consiste à charger toutes les politiques de l'entreprise dans le prompt système de chaque agent : contexte saturé, instructions diluées, coût par requête gonflé, et désynchronisation garantie le jour où une politique change. L'approche règle-exécutable inverse le flux : l'agent travaille avec un contexte minimal, tente l'action, et reçoit — seulement si nécessaire — un refus motivé, structuré, actionnable. La règle n'est jamais dupliquée dans les prompts ; elle vit en un seul endroit (l'API) et se distribue à la demande. Un agent qui reçoit "refusé : cette action requiert une validation humaine (décision D-2024-17)" corrige sa trajectoire en une itération, sans avoir jamais eu besoin de connaître les mille autres règles qui ne le concernaient pas.

**La symétrie est le point** : humain et agent deviennent plus productifs par le même mécanisme — moins de contexte à porter, plus de pertinence au moment utile. C'est un argument d'architecture rare, qui sert les deux lecteurs du SI à la fois ; il mérite d'être nommé dans le livre (proposition : *l'économie de contexte*).

## Place dans le livre

Chapitre 6 (la structure : tout passe par l'API) — la règle exécutable est ce que "règle de gestion côté SI" veut dire concrètement. Écho au chapitre 1 (le wiki mort) à faire explicitement : le lecteur doit reconnaître l'enterrement de ce qu'on lui a montré au début.

## Vigilance

- ⚠ Ne pas promettre la fin de TOUTE documentation : ce qui meurt, c'est le wiki *normatif* (les règles). La documentation de contexte (pourquoi le système existe, architecture, décisions) vit dans le stream de décisions — autre mécanique, même esprit.
- Le risque bureaucratique inverse : automatiser des contrôles sur des règles mortes ou absurdes les rend infranchissables au lieu d'ignorables. La règle exécutable exige le cycle de vie des décisions (début, fin, révision) — sinon on bétonne l'absurde. C'est le pendant du "réécrire le passé" de DCB.
