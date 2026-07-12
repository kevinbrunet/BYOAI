# DCB — les décisions comme events

## Le principe

Appliquer une approche DCB (Decision-Centric / event sourcing des décisions) au stockage des décisions elles-mêmes, pas seulement aux données métier : chaque décision est un event avec un début, une fin, un contexte, et l'état courant est une projection des décisions actives.

```
décision = event
stream de décisions = historique complet
état courant = projection des décisions actives
réécriture du passé = rejouer le stream avec une décision modifiée
essai = brancher un stream alternatif sans toucher le principal
rollback = revenir à une projection antérieure
```

## Ce que ça donne concrètement

- **Navigation** : on projette uniquement les décisions actives à un instant T.
- **Impact analysis** : on rejoue le stream en modifiant une décision et on observe la divergence de projection.
- **Essais sans risque** : stream alternatif, comparaison de projections, rollback trivial.
- **Mémoire du passé** : "avant 2000 ça voulait dire ça" devient une projection datée, pas une note perdue dans un wiki.

## Le point non-trivial : réécrire le passé sans casser l'immutabilité

La réécriture du passé en event sourcing pur est normalement un anti-pattern — les events sont immuables. La distinction qui rend ça propre :

```
event immuable   → ce qui s'est passé
décision         → interprétation active d'un event à un instant T
```

On ne réécrit pas l'event — on change la décision qui l'interprète. C'est cette nuance qui rend le rollback propre et qui permet de rejouer/brancher/annuler sans perdre l'historique réel.

## Ce qui reste ouvert

La navigation guidée ("montre-moi uniquement ce dont j'ai besoin") suppose une projection contextuelle intelligente. Qui définit le contexte de la requête — un humain, un agent IA ? Voir [navigation guidée et contexte de projection](../05-questions-ouvertes/navigation-guidee-contexte.md).

## Lien avec le reste de la série

Donne une mécanique concrète à l'axiome "on documente les choix, pas les solutions" : une décision n'est pas un document, c'est un nœud dans un graphe avec des propriétés temporelles (mission, début, fin, dépendances vers d'autres décisions). Changer une décision sans connaître ses dépendances, c'est opérer à l'aveugle.

Voir le backlog d'enrichissement des posts existants et le nouveau post proposé : [backlog des posts](../00-meta/backlog-posts.md).
