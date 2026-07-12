# L'épidémiologiste du backlog

## La métaphore médicale filée

À l'hôpital, plusieurs métiers coexistent et se complètent, chacun à une échelle de temps différente :

- **L'urgentiste** traite le patient devant lui — le présent, un cas.
- **L'interniste** cherche la cause profonde en analysant l'ensemble de l'historique médical d'un patient — le passé, un cas.
- **L'épidémiologiste** observe des milliers de cas pour comprendre les schémas récurrents et améliorer le système — le passé, à grande échelle.

Ces approches ne s'opposent pas, elles se complètent.

## Le constat sur les organisations IT

Dans beaucoup d'organisations IT, on trouve des urgentistes (le backlog, le présent), parfois des internistes (l'analyse ponctuelle d'un incident), rarement des épidémiologistes (l'analyse systématique des patterns sur l'ensemble de l'historique). Pourtant, c'est souvent là que se trouvent les plus grands leviers de transformation.

Le backlog regarde le présent. L'historique regarde le passé. Aucun des deux ne regarde le futur — donc c'est économe et fiable, contrairement à la prédiction. Voir [le paradoxe de l'armoire à fibre optique](./paradoxe-armoire-fibre-optique.md) pour un exemple concret de ce que l'absence de cette fonction produit.

## La question opérationnelle qui en découle

Y a-t-il, dans une équipe, des personnes qui s'occupent spécifiquement d'analyser l'historique — des "épidémiologistes du backlog" ? C'est un rôle distinct de la résolution de tickets et de l'analyse d'incident ponctuelle : il porte sur la détection de patterns récurrents à travers l'ensemble du stream de décisions/incidents passés.

## Réserve du conférencier (Frédéric Leguédois)

Interpellé sur ce prolongement de sa conférence "Éloge de la simplicité", l'auteur a confirmé que la direction était juste mais hors du format (45 minutes) — signe que le sujet est reconnu comme pertinent mais pas encore développé publiquement par lui.

## La jonction BYOIA : plus les tickets vont vite, plus l'épidémiologiste devient vital (ajout 2026-07-11)

Le [développeur-harnais](./equipe-agile-developpeur-harnais.md) est un urgentiste surpuissant : la demande arrive, le ticket est produit en un minimum de temps. C'est le bénéfice — et c'est le risque. Une organisation qui résout de plus en plus vite sans comprendre de mieux en mieux traite les symptômes à un débit record : elle peut régénérer indéfiniment le même outil pour le même problème sans jamais voir que c'est le même problème. Le post déjà publié le disait : "réagir vite, c'est bien ; comprendre, c'est encore mieux" — le BYOIA aggrave l'écart si la fonction épidémiologiste n'existe pas.

Concrètement, l'épidémiologiste du backlog devient **l'opérateur du [cycle de promotion](./cycle-promotion-specifique.md)** :

- **Détection de convergence (la montée)** : c'est lui qui voit que douze tickets, six outils spécifiques et trois forks récents tournent autour du même trou dans le SI — le signal "usage convergent → candidat à la promotion" n'est pas automatique, il faut quelqu'un qui regarde le stream à l'échelle de la population.
- **Détection d'extinction (la descente)** : usage effondré, forks divergents, tickets récurrents sur un outil promu — les signaux d'élagage sont aussi des patterns d'historique.
- **Alimentation de la taxonomie des angles morts** : chaque pattern récurrent détecté est un angle mort documenté empiriquement — la fonction capitalise au lieu de découvrir incident par incident.

Et la question ouverte (rôle humain ou agent ?) reçoit un début de réponse par l'architecture même : le stream de décisions/events et les métriques d'utilisation rendent l'épidémiologie *bon marché* — un agent peut balayer l'historique en continu et lever des hypothèses de patterns ; le jugement de promotion (ce pattern mérite-t-il une réponse structurelle ?) reste un arbitrage humain. Agent-détecteur, humain-arbitre — écho direct à [chef-arbitre vs chef-détecteur](../05-questions-ouvertes/chef-arbitre-vs-detecteur.md).

## Lien avec le reste de la série

Ce rôle d'épidémiologiste du backlog est une fonction organisationnelle concrète pour exploiter le [stream de décisions DCB](./dcb-decisions-comme-events.md) : sans quelqu'un (humain ou agent IA) qui interroge systématiquement les projections passées à la recherche de patterns, le mécanisme de rejeu/rollback de DCB reste un outil sans opérateur. Voir aussi [taxonomie des angles morts construite empiriquement](./taxonomie-angles-morts-empirique.md) — la fonction épidémiologiste est précisément celle qui pourrait construire cette taxonomie dans la durée, plutôt que de la découvrir incident par incident sans capitalisation.

Question ouverte pour la série : ce rôle peut-il être occupé par un agent IA de façon crédible (voir [parallèle holacratique](./holacratie-parallele.md) — un rôle peut être rempli par un humain, un workflow ou une IA), ou nécessite-t-il un jugement humain difficile à déléguer ?
