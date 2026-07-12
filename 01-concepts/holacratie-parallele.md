# Parallèle avec l'holacratie

> **Statut (2026-07-11) : rétrogradé.** Ce parallèle servait l'esprit (le rôle indépendant de qui l'occupe), pas la thèse. Le label "holacratie" étant controversé, le livre s'appuie sur [Haier / RenDanHeYi](../03-exemples/haier-rendanheyi.md) comme référence organisationnelle — cas industriel documenté plutôt que méthode à marque déposée. Le contenu ci-dessous reste comme matériau ; le pilotage façon Kubernetes et le problème du chef restent utilisés ailleurs.

## Le rapprochement

L'holacratie a formalisé, il y a quinze ans, la séparation que construit tout le reste de la série : le rôle comme unité structurelle, indépendante de qui l'occupe.

L'holacratie part d'un principe rarement formalisé ailleurs : l'entreprise théorique — l'ensemble des rôles, de leurs redevabilités (accountabilities) et de leurs domaines d'autorité — est une structure indépendante des personnes qui l'occupent. Un rôle n'est pas un poste ni une personne. C'est une unité de travail avec un périmètre défini, qui peut être occupée par une personne, partagée entre plusieurs, ou cumulée par une seule qui en tient plusieurs à la fois.

C'est la même séparation que [structure vs interface](./frontiere-structure-interface.md), théorisée au niveau organisationnel avant que l'IA ne la rende opérationnelle au niveau technique.

## Ce qui change avec l'IA

Un rôle qui, dans l'holacratie classique, ne pouvait être rempli que par des humains, peut désormais être rempli par un workflow automatisé, par une IA, ou par une combinaison des deux — sans que la structure de rôles elle-même ait besoin de changer.

Exemple : le rôle "traiter les demandes de niveau 1 du support" reste défini par les mêmes redevabilités, que 90% des instances de ce rôle soient occupées par un agent IA et 10% escaladées à un humain, ou l'inverse.

## Le pilotage façon Kubernetes

On peut optimiser l'allocation des rôles non plus seulement sur des critères de compétence ou de disponibilité humaine, mais sur des métriques opérationnelles : délai de traitement, nombre de tâches en attente, taux d'escalade, charge instantanée. Un pic de demandes sur un rôle donné ? On scale l'exécution IA de ce rôle. Un cas trop ambigu ? Il remonte vers l'instance humaine du même rôle.

Voir l'exemple détaillé et ses limites : [analogie Kubernetes / pods pour les rôles](../03-exemples/kubernetes-pods-roles.md) et [limite de l'analogie Kubernetes](../04-objections/limite-analogie-kubernetes.md).

## Quand un rôle est rempli par plusieurs agents : le problème du chef

Dès qu'un rôle holacratique est rempli par plusieurs instances IA en parallèle (un "conseil d'agents"), la question de l'arbitrage se pose : faut-il un chef, et si oui de quelle nature ? Voir [conseil d'agents et pondération bayésienne](./conseil-agents-ponderation-bayesienne.md), [sagesse des foules et Condorcet](./sagesse-des-foules-condorcet.md) et [architectures de référence pour l'agrégation multi-agents](../03-exemples/architectures-agregation-references.md).
