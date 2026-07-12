# Approche data-centrique

## Le principe

Séparer la structure (données, règles de gestion, garanties) de l'organe de production/consommation (l'outil quotidien, l'interface).

L'entreprise reste maître de ses données : cohérence, traçabilité, sécurité d'accès, conformité réglementaire. Elle expose cela sous forme d'API. Des logiciels — de plus en plus souvent générés et pilotés par l'IA de chaque collaborateur — consomment et produisent de la donnée à travers cette frontière.

## Ce qui reste au SI, non négociable

- La cohérence des données (référentiels, intégrité, traçabilité)
- Les règles de gestion métier — parce qu'elles portent la conformité réglementaire et la cohérence applicative transverse
- L'exposition contrôlée de tout ça via des API stables

Cette partie ne se négocie pas parce qu'elle porte la responsabilité juridique et la cohérence du système d'information dans son ensemble.

## Ce qui peut redevenir individuel

L'interface. La façon dont chacun consomme ces API dans son travail quotidien. N'importe qui peut construire l'outil qui correspond exactement à sa manière de travailler, l'administrer, le faire évoluer — sans jamais toucher à la couche qui porte la responsabilité.

Le collaborateur ne code plus "son interprétation du processus métier" en dur dans son outil. Il consomme une API qui garantit que le processus métier est correct, et il habille cette garantie comme il veut.

## Généralisation à tous les niveaux

Ça s'applique y compris à l'intérieur de la DSI elle-même : le dépôt Git est commun, la vérification de sécurité, les rôles, les états de tickets, les Definition of Done / Definition of Ready appartiennent à la structure portée par l'entreprise. Comment l'étape est réalisée concrètement — c'est le collaborateur. Voir l'exemple détaillé : [Git, DoD, DoR dans la DSI](../03-exemples/git-dod-dor-dsi.md).

Le principe se généralise à tous les métiers : support, RH, autres fonctions. Chacun interagit avec une plateforme commune portée par l'entreprise, et branche son harnais personnel dessus (Git/Jira/Teams pour le dev, un autre socle pour la RH) — mais le principe de séparation reste identique.

## Lien avec le reste

C'est ce découplage qui rend le [BYOIA](./byoia.md) cohérent, et qui trouve un écho organisationnel dans le [parallèle holacratique](./holacratie-parallele.md).
