# Deux catégories de skills — SI et personnelles

## Le principe

Les skills (au sens des capacités packagées qu'un harnais IA peut invoquer) se divisent en deux catégories, qui ne vivent pas au même endroit ni sous la même gouvernance — application directe de la [frontière structure/interface](./frontiere-structure-interface.md) à la brique la plus concrète du harnais.

## Catégorie 1 — les skills SI

Propres à l'entreprise, au processus et/ou au tool utilisé. Elles doivent être **communes** et bénéficier d'un **système de droits** : hébergées et administrées par le SI, au même titre que les tools et le workflow décrits dans [CI/CD, un processus comme un autre](../03-exemples/cicd-processus-comme-un-autre.md).

Exemple direct : une skill « ouvrir une PR conforme au DoD » n'a de sens que si elle encode une règle partagée (voir [Git, DoD, DoR dans la DSI](../03-exemples/git-dod-dor-dsi.md)) — si chacun la réécrit à sa façon, la règle cesse d'être vérifiable, donc cesse d'être une règle. Le critère 1 de la [doctrine frontière SI/interface](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) s'applique telle quelle : dès qu'une skill encode quelque chose de partagé (auditable, à tracer, changeant un état du domaine), elle bascule côté SI.

Le système de droits associé est le même mécanisme que celui déjà posé pour l'accès aux tools : délégation d'identité, intersection de permissions sur toute la chaîne, durée de vie courte associée à la tâche — voir [délégation d'identité pour agents](./delegation-agents-jwt-mtls.md). Une skill SI n'est pas un fichier qu'on copie librement d'un poste à l'autre ; c'est une capacité gouvernée, au même régime qu'un accès API.

## Catégorie 2 — les skills personnelles

Propres à la philosophie de travail de la personne. Elles lui **restent attachées** : elles ne sont pas hébergées par le SI, elles s'ajoutent librement à l'usage de son IA personnelle. C'est la couche interface au sens strict — personne d'autre n'a besoin de s'y fier, donc rien n'oblige à la centraliser, à la gouverner par des droits, ni à la faire administrer par un tiers.

Exemple : une manière personnelle de structurer ses prompts, une checklist de relecture propre à son style, un raccourci de formulation — ça relève du même statut que « présentation, priorisation personnelle, projections, brouillons » dans la doctrine : libre, spécifique, non partagé.

## Le test pour trancher

Le même test des cinq questions que pour la frontière générale s'applique à une skill donnée : si un collègue, un auditeur ou un processus doit pouvoir s'y fier, elle est SI ; sinon elle reste personnelle. Une skill peut migrer d'une catégorie à l'autre — c'est exactement le mécanisme déjà nommé pour l'interface en général : voir [cycle de promotion du spécifique](./cycle-promotion-specifique.md). Une skill personnelle qui s'avère utile à toute une équipe est un candidat naturel à la promotion vers le SI, avec le changement de gouvernance que ça implique (droits, audit, maintenance par un rôle plutôt que par un individu).

## Où ça s'insère

- [BYOIA](./byoia.md) — les skills personnelles sont un composant du harnais que chaque collaborateur apporte.
- [CI/CD, un processus comme un autre](../03-exemples/cicd-processus-comme-un-autre.md) — les skills SI y sont illustrées comme brique du triptyque tools/workflow/métriques.
- [Frontière structure/interface](./frontiere-structure-interface.md) — cette distinction est une instance de plus du principe général, appliquée au grain le plus fin (la skill individuelle) plutôt qu'au processus entier.
