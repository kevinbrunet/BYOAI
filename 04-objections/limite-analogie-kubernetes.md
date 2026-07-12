# Objection — Limite de l'analogie Kubernetes

## Le problème

Les pods sont interchangeables parce qu'ils sont censés être strictement équivalents (même image, même comportement, aucune trace d'état entre deux exécutions). Un rôle occupé par un humain vs par une IA n'est pas interchangeable au même sens : l'humain apporte du jugement contextuel, une responsabilité légale engageable, une capacité à gérer l'exception non prévue dans la redevabilité écrite.

Si l'analogie ["on pilote les rôles comme des pods"](../03-exemples/kubernetes-pods-roles.md) est filée jusqu'au bout sans nuance, un lecteur qui connaît à la fois l'holacratie et Kubernetes objectera qu'elle efface cette différence.

## Formulation qui tient

Le pilotage ressemble à du scaling de pods pour les rôles à faible variance (support niveau 1, tâches procédurales) ; il ne s'applique pas aux rôles à forte redevabilité de jugement. Le dire explicitement évite qu'on prête à l'auteur l'idée que n'importe quel rôle humain est substituable à volonté.
