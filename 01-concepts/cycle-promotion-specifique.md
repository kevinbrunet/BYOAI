# Cycle de promotion du spécifique — de l'outil individuel à l'API d'entreprise

## Le principe

Les outils spécifiques n'ont pas vocation à rester isolés. Quand une pratique mérite d'être partagée ou tracée, on peut l'intégrer dans l'API de l'entreprise. Le cycle :

1. **Spécifique utilisateur** — l'interface personnalisée produite pour un salarié (directement ou via le [développeur-harnais](./equipe-agile-developpeur-harnais.md))
2. **Uniformisation pour l'équipe** — la pratique fait ses preuves, elle est harmonisée à l'échelle de l'équipe
3. **Mise à disposition de l'outil** — l'équipe y accède comme un commun
4. **Escalade potentielle** vers le service, puis l'entreprise — intégration dans l'API d'entreprise, avec la traçabilité qui va avec

À chaque promotion, **la maintenance est transférée** : de l'individu vers l'équipe, de l'équipe vers le service, du service vers l'entreprise.

## Pourquoi c'est un argument fort

- **L'uniformisation redevient a posteriori.** L'ancien modèle uniformisait a priori (comité, spécification, consensus mou avant tout usage). Ici, l'uniformisation est une **sélection par l'usage** : seul ce qui a prouvé sa valeur en conditions réelles est promu. On inverse le sens de la standardisation — elle remonte du terrain au lieu de descendre de l'organigramme.
- **Réponse structurelle à l'objection du coût aval.** [Le déplacement du coût vers l'aval](../04-objections/deplacement-cout-aval.md) suppose que chaque spécifique traîne sa maintenance individuelle indéfiniment. Le cycle de promotion borne ce coût : ce qui est promu voit sa maintenance mutualisée ; ce qui n'est pas promu reste jetable — et un outil jetable généré en un minimum de temps peut être régénéré plutôt que maintenu.
- **La traçabilité arrive au bon moment.** Exiger la traçabilité complète dès le stade individuel tuerait l'expérimentation ; ne jamais l'exiger serait du Shadow IT. Le cycle place l'exigence de traçabilité au moment de l'intégration à l'API d'entreprise — là où elle a un sens de gouvernance.

## Le contrat de stabilité par couche

On part du rapide et jetable vers quelque chose de plus pérenne et testé plus massivement au fur et à mesure. L'usage est maintenu plus activement à mesure qu'il passe les couches. Chaque couche porte un contrat implicite différent :

| Couche | Contrat de stabilité | Comportement en cas de changement interne |
|---|---|---|
| Spécifique utilisateur | Aucun — peut casser demain | Personne ne le protège ; l'utilisateur régénère |
| Équipe | Maintenance mutualisée | On fait attention lors des changements internes |
| Service | Cas pris en compte | Fait partie des cas considérés avant tout changement |
| Entreprise / API | Engagement fort | Non-régression, rétro-compatibilité |

La promotion n'est donc pas qu'un transfert de maintenance : c'est l'entrée dans le **périmètre de considération des changements**. Un spécifique utilisateur n'existe pas aux yeux de celui qui modifie le SI ; un spécifique de service, si.

## Le coût de la considération — et la descente comme opération de premier ordre

Attention : chaque cas pris en compte complexifie le changement et la maintenance. Plus le périmètre de considération grossit, plus chaque évolution interne coûte cher — c'est exactement le mécanisme qui a rigidifié les SI historiques.

Ce qui change avec l'IA : **on peut facilement en enlever**. Le coût de production étant beaucoup plus bas, jeter est facile. La descente (rétrogradation, suppression) devient une opération de premier ordre, aussi légitime que la montée :

- un outil promu qui ne justifie plus son coût de considération redescend ou disparaît ;
- celui qui en a encore besoin le régénère au niveau utilisateur — il ne le perd pas, il perd sa garantie de stabilité ;
- le périmètre de considération reste ainsi élagué en permanence, là où le SI historique ne savait qu'accumuler.

C'est l'asymétrie centrale : avant, ajouter un cas était coûteux et le retirer impensable (quelqu'un en dépendait, personne ne savait le refaire). Maintenant, ajouter est facile et retirer aussi — parce que refaire est trivial. La rigidification n'est plus une fatalité, c'est un choix de gouvernance.

## Le pilotage : métriques d'utilisation et fenêtre de complexité

Deux instruments pilotent le cycle :

**Les métriques d'utilisation.** Chaque outil promu est instrumenté : qui l'utilise, à quelle fréquence, sur quels cas. C'est la métrique qui déclenche la montée (usage convergent constaté → candidat à la promotion) et qui légitime la descente (usage effondré → rétrogradation). Elle dépolitise le retrait : on n'enlève pas l'outil de quelqu'un, on acte une mesure. La traçabilité exigée au moment de l'intégration à l'API sert donc à deux choses : la conformité, et le pilotage du cycle lui-même.

**La fenêtre de complexité.** C'est la complexité maximale tenable par la capacité de maintenance disponible, à chaque couche. Chaque cas pris en compte consomme de la fenêtre ; la fenêtre est finie. Quand le périmètre de considération dépasse la fenêtre, deux leviers et seulement deux :

1. **augmenter l'équipe** (agrandir la fenêtre) ;
2. **réduire le périmètre** (rétrograder ou jeter les cas dont les métriques d'utilisation ne justifient plus le coût de considération).

L'analogie la plus proche est la limite de WIP en kanban ou le budget d'erreur en SRE : une contrainte explicite et chiffrée qui force l'arbitrage au lieu de laisser la complexité s'accumuler silencieusement. Le SI historique n'avait pas de fenêtre de complexité déclarée — elle existait quand même, mais on ne la découvrait qu'en la crevant (projets enlisés, refontes impossibles). Ici elle devient un objet de gouvernance de premier ordre : visible, mesurée, arbitrée.

⚠ Reste à définir comment on *mesure* la complexité consommée par un cas (nombre de dépendances ? coût de non-régression ? temps de prise en compte lors d'un changement ?) — sans unité de mesure, la fenêtre reste une image.

## Ce que ça implique (à développer)

- **Critères de promotion** : partiellement tranché par les métriques d'utilisation (usage convergent → montée, usage effondré → descente). Reste à fixer les seuils, et à décider si l'usage suffit seul (un outil très utilisé mais risqué doit-il monter ?).
- **Qui décide** : recoupe directement l'[arbitrage règle de gestion vs interface](../04-objections/arbitrage-regle-gestion-vs-interface.md) et la question 18 de [questions-livre](../00-meta/questions-livre.md) — le cycle donne le *processus*, il reste à nommer l'*arbitre*.
- **Le refactoring de promotion** : un outil individuel généré vite n'est pas au standard d'une API d'entreprise. La promotion implique un coût de mise au standard (sécurité, tests, documentation) — c'est le prix du transfert de maintenance, à assumer explicitement.
- **Le droit de fork — TRANCHÉ (2026-07-11)** : le fork est libre par défaut. L'outil promu est une *offre*, jamais une obligation en soi : le salarié n'est pas obligé de l'utiliser s'il trouve un chemin alternatif **autorisé**. Ce qui est obligatoire n'est pas l'outil, c'est le passage par le SI — et c'est **le SI qui restreint ou non le nombre de façons d'interagir avec les données**, au niveau de l'API, pas au niveau de l'outil. Deux régimes :
  - **Latitude par défaut** : plusieurs chemins d'accès autorisés, fork et divergence libres. L'outil promu gagne par adoption volontaire (convergent avec le constat platform engineering : l'adoption choisie bat l'adoption décrétée), pas par décret — le consensus mou par le bas est évité par construction.
  - **Restriction ciblée** : pour les endpoints humain-only et les processus réglementaires, le SI resserre les chemins (une seule commande, typage humain, traçabilité imposée). La contrainte est portée par la [frontière](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) et la [délégation typée](./delegation-agents-jwt-mtls.md), pas par l'uniformisation des outils.

  Conséquence élégante : la liberté se régule à la couche accès (combien de chemins vers la donnée), jamais à la couche outil (lequel utiliser). L'uniformisation des outils reste une pure économie d'efforts ; la sécurité et la conformité vivent ailleurs.

  **L'incitation à adopter (à dire explicitement dans le livre)** : si le fork est libre, pourquoi utiliser l'outil promu ? Parce que la promotion porte le contrat de stabilité et le transfert de maintenance. Celui qui adopte l'outil promu est protégé lors des changements internes et ne maintient rien ; celui qui forke récupère sa liberté ET sa maintenance — sa version peut casser demain, personne ne la protège, à lui de la régénérer. Il n'y a donc ni obligation ni contradiction : l'outil promu gagne parce qu'il est *moins cher à posséder*, pas parce qu'il est imposé. Le fork n'est pas un acte de rébellion, c'est un choix économique local — et si beaucoup forkent la même chose, c'est un signal des métriques : l'outil promu ne couvre plus le besoin, il faut le faire évoluer ou promouvoir le fork.

## Lien avec le reste de la série

- [Équipe agile interne — développeur-harnais](./equipe-agile-developpeur-harnais.md) — l'organe de production en amont du cycle
- [Frontière structure/interface](./frontiere-structure-interface.md) — la promotion est le mécanisme par lequel une interface peut franchir la frontière et devenir structure
- [Approche data-centrique](./approche-datacentrique.md) — l'API d'entreprise comme point d'intégration final
- [Générique vs spécifique](./generique-vs-specifique.md) — le cycle réconcilie les deux : le générique de demain est le spécifique qui a survécu
- [DCB — décisions comme events](./dcb-decisions-comme-events.md) — chaque promotion est une décision datée, avec mission, début, fin : candidate naturelle au stream de décisions
