# Équipe agile interne — le développeur-harnais comme organe de production

## Le principe

Le BYOIA n'exige pas que chaque salarié pilote lui-même son équipe IA. Un modèle intermédiaire existe : une vraie équipe agile composée de salariés de l'entreprise, où les salariés métier donnent des tâches à un développeur équipé de son harnais IA, qui produit les interfaces personnalisées pour eux.

Le flux : un salarié a besoin de traiter telle demande spécifiquement pour un client → la demande part vers le développeur → le développeur produit le ticket en un minimum de temps grâce à son harnais.

## Ce que ça change dans le modèle

- Le salarié métier reste **donneur d'ordre** (il exprime le besoin spécifique), pas opérateur d'IA.
- Le développeur devient **l'organe de production des interfaces sur mesure** : son harnais lui permet un débit de production compatible avec du sur-mesure individuel, ce qui était économiquement impossible avant.
- La structure (données, règles de gestion, API, DoD/DoR) reste commune — c'est l'interface produite qui est personnalisée par salarié ou par cas client.

## Ce que ça résout

- **La question de la compétence** : le modèle "chaque salarié pilote son équipe IA" ne concerne qu'une minorité. Le développeur-harnais rend le bénéfice du spécifique accessible à tous les salariés, sans exiger d'eux une compétence de pilotage d'agents. Répond partiellement à la question 19 de [questions-livre](../00-meta/questions-livre.md).
- **Le devenir du développeur** (question 20) : il ne disparaît pas, il change de position — d'exécutant de spécifications génériques à producteur à haut débit d'interfaces spécifiques. Le harnais est son outil de production, pas son remplaçant.
- **La gouvernance** : le point de production reste identifié et outillé (un développeur, un harnais, un pipeline), ce qui est plus traçable qu'une prolifération d'agents individuels.

## Tension à trancher (ne pas l'esquiver dans le livre)

Ce modèle est-il encore du BYOIA ? Le salarié n'apporte pas *son* IA — c'est le développeur qui apporte la sienne. Deux lectures possibles :

1. **Variante du BYOIA** : le "Your" désigne l'équipe, pas l'individu. Le harnais est apporté par celui qui produit.
2. **Modèle distinct et complémentaire** : un continuum de délégation — à un extrême le salarié autonome avec sa propre équipe IA, à l'autre le salarié qui passe par le développeur-harnais. Le livre gagnerait à nommer ce continuum plutôt qu'à tout appeler BYOIA.

Non tranché. À articuler avec la [doctrine frontière SI/interface](../05-questions-ouvertes/doctrine-frontiere-si-interface.md).

## Lien avec le reste de la série

- [BYOIA](./byoia.md) — le modèle général dont ceci est une déclinaison (ou un voisin, selon la tension ci-dessus)
- [Git, DoD, DoR dans la DSI](../03-exemples/git-dod-dor-dsi.md) — même mécanique : structure commune, réalisation individuelle
- [Effondrement de l'économie d'échelle](../02-arguments/01-effondrement-economie-echelle-code.md) — c'est ce qui rend le sur-mesure par ticket économiquement viable
- [Frontière structure/interface](./frontiere-structure-interface.md) — la personnalisation ne porte que sur la couche interface
