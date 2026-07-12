# Accès conversationnel aux services

## Le principe

L'IA transforme aussi la manière dont on accède à un service, pas seulement la manière dont on le produit. Jusqu'ici, on a parlé du collaborateur qui construit son propre outil pour consommer les API de l'entreprise ([BYOIA](./byoia.md)). Il y a un autre sens à cette histoire : l'IA peut devenir l'interface d'accès à un service pour ceux qui ne le consomment pas au quotidien.

## La charge de traduction

Un service interne (support, RH, DSI...) repose sur trois choses : un processus formalisé, des rôles qui le composent, et une charge implicite pour l'utilisateur externe de savoir à qui s'adresser et comment formuler sa demande pour qu'elle rentre dans le processus.

Cette charge de traduction — transformer "j'ai un problème avec mon accès VPN" en ticket correctement routé, catégorisé, assigné — a toujours été soit portée par l'utilisateur (mal, avec de la friction), soit par un premier niveau humain dédié à cette traduction (efficace, mais coûteux).

## Ce que l'IA change

L'IA peut absorber cette charge de traduction. Elle fait le lien entre une demande formulée en langage naturel et le processus interne réel qui doit la traiter — avec ses rôles, ses collaborateurs, ses étapes. Le service devient conversationnel sans cesser d'être structuré derrière : l'utilisateur parle normalement, l'IA route vers la bonne structure.

## Exemple de référence : Claude Tag

Voir [exemple Claude Tag / Slack](../03-exemples/claude-tag-slack.md) pour le détail du produit et la nuance importante : Claude Tag illustre l'accès conversationnel côté entreprise (agent partagé configuré par l'entreprise), pas le BYOIA (IA personnelle du collaborateur). Les deux logiques sont complémentaires : l'une gère l'accès entrant, l'autre la production sortante.

## Lien avec les garanties

Ce mécanisme illustre en pratique l'[argument 5 (garanties non négociables)](../02-arguments/05-garanties-non-negociables.md) : la conversation est libre côté utilisateur, l'accès aux données et aux outils reste gouverné côté structure.
