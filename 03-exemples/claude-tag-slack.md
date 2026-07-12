# Exemple — Claude Tag / Slack

## Le fait (vérifié par recherche web dans la conversation source)

✓ Anthropic a lancé Claude Tag le 23 juin 2026 : un produit qui ajoute Claude à Slack comme coéquipier IA persistant et partagé, en beta pour les clients Claude Enterprise et Team.

*Note de vérification : cette date/ce statut proviennent d'une recherche web faite dans la conversation source (Build Fast with AI, Anthropic). Marqueur ✓ hérité de cette vérification — à re-confirmer si le post est publié longtemps après, les produits Anthropic évoluant vite.*

## Le mécanisme

N'importe qui dans le canal peut taguer @Claude et lui déléguer une tâche pendant qu'il se concentre sur autre chose. Claude agit sous l'identité de l'organisation dans le canal plutôt que sous les permissions personnelles de l'utilisateur qui le tague — un basculement d'un modèle "identité personnelle" à un modèle "identité de service, scopée par canal".

Ce basculement est précisément le découplage [structure/interface](../01-concepts/frontiere-structure-interface.md), transposé à l'accès plutôt qu'à la production.

## Ce que ça illustre

- [Accès conversationnel aux services](../01-concepts/acces-conversationnel.md) : un service devient conversationnel sans cesser d'être structuré derrière.
- [Argument 5 (garanties non négociables)](../02-arguments/05-garanties-non-negociables.md) en pratique : ✓ l'usage est facturé à l'organisation, les administrateurs choisissent quels canaux/outils/données chaque instance de Claude peut atteindre, et une instance configurée pour la vente ne transmet pas ses mémoires à une instance configurée pour l'ingénierie. La conversation est libre côté utilisateur ; l'accès aux données et aux outils reste gouverné côté structure.

## Point de vigilance — ne pas confondre avec le BYOIA

Claude Tag est un exemple d'accès conversationnel à un service, **pas** un exemple de [BYOIA](../01-concepts/byoia.md) au sens défini dans cette série. Dans Claude Tag, c'est l'entreprise qui possède et configure l'agent partagé du canal — ce n'est pas le collaborateur qui apporte son IA personnelle pour consommer les API de l'entreprise.

Les deux logiques sont complémentaires (l'une gère l'accès entrant, l'autre la production sortante), mais il faut une transition explicite dans le texte pour ne pas créer de confusion conceptuelle chez un lecteur qui connaît le produit : *"Ce n'est pas du BYOIA à proprement parler — c'est l'entreprise qui pose l'agent — mais ça illustre le même principe de séparation structure/interface, appliqué à l'accès plutôt qu'à la production."*

## Sources (issues de la conversation d'origine)

- https://www.anthropic.com/news/introducing-claude-tag
- https://www.buildfastwithai.com/blogs/anthropic-claude-tag-slack-review
