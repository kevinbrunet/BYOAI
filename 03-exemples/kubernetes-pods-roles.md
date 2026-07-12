# Exemple — Analogie Kubernetes / pods pour les rôles

## L'analogie

Dans l'[holacratie](../01-concepts/holacratie-parallele.md), un rôle peut être rempli par un humain, un workflow, une IA, ou une combinaison. On peut alors piloter l'allocation des rôles sur des métriques opérationnelles — délai de traitement, nombre de tâches en attente, taux d'escalade, charge instantanée — un peu comme on pilote des pods sur un cluster Kubernetes : un pic de demandes sur un rôle donné, on scale l'exécution IA de ce rôle ; un cas trop ambigu, il remonte vers l'instance humaine du même rôle.

## Limite structurelle de l'analogie — à assumer ou couper

Les pods sont interchangeables parce qu'ils sont censés être strictement équivalents : même image, même comportement, aucune trace d'état entre deux exécutions. Un rôle occupé par un humain vs par une IA n'est **pas** interchangeable au même sens : l'humain apporte du jugement contextuel, une responsabilité légale engageable, une capacité à gérer l'exception non prévue dans la redevabilité écrite.

Si l'analogie est filée jusqu'au bout ("on pilote les rôles comme des pods"), un lecteur qui connaît à la fois l'holacratie et Kubernetes objectera qu'elle efface cette différence.

## Formulation recommandée

Le pilotage ressemble à du scaling de pods pour les rôles à faible variance (support niveau 1, tâches procédurales) ; il ne s'applique pas aux rôles à forte redevabilité de jugement. Le dire explicitement évite qu'on prête à l'auteur l'idée que n'importe quel rôle humain est substituable à volonté.

Voir aussi : [limite de l'analogie Kubernetes](../04-objections/limite-analogie-kubernetes.md).
