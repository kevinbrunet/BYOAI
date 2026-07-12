# Architectures de référence pour l'agrégation multi-agents ("faut-il un chef ?")

Quatre corpus qui traitent frontalement la question du chef dans les systèmes distribués/multi-agents, avec niveau de certitude par référence.

## 1. Mixture of Experts — le chef comme fonction de gating apprise

✓ L'architecture Mixture of Experts (Jacobs, Jordan, Nowlan, Hinton, 1991) : au lieu d'un vote à poids fixe ou d'un chef désigné statiquement, un réseau de gating apprend dynamiquement quel expert consulter selon l'input. Le "chef" n'est pas un agent parmi les autres, c'est une fonction séparée, elle-même entraînée sur le signal d'erreur.

Ça répond à la question de granularité (voir [conseil d'agents](../01-concepts/conseil-agents-ponderation-bayesienne.md)) : le gating network apprend la partition de l'espace des problèmes plutôt qu'on la définisse à la main. ⚠ Contrepartie : le gating network hérite lui aussi des angles morts de son propre entraînement — pas de sortie complète de la récursion "qui garde le gardien".

## 2. Boosting (AdaBoost) — le chef comme méta-algorithme, pas comme agent

✓ AdaBoost (Freund & Schapire, 1997) formalise littéralement le mécanisme de dégradation pondérée : à chaque round, les exemples mal classés voient leur poids augmenter, et chaque classifieur faible reçoit un poids dans le vote final proportionnel à sa performance globale — par une règle de mise à jour prouvée mathématiquement (borne de generalization error connue), pas par intervention manuelle après incident.

Réponse à "a-t-on besoin d'un chef" : dans ce cadre, pas de chef-agent, mais un chef-mécanisme — un orchestrateur sans opinion propre sur le problème, seulement une fonction d'agrégation. Le taux d'apprentissage (learning rate) du boosting est le paramètre qui contrôle combien un échec dégrade le poids, avec des garanties théoriques sur la vitesse de convergence — réponse directe au risque de sur-réaction à un seul incident.

## 3. Byzantine Fault Tolerance — le chef comme point de défaillance unique

✓ La littérature sur la tolérance aux pannes byzantines (Lamport, Shostak, Pease, 1982) part du problème inverse : un système avec un chef unique est un point de défaillance unique — si le chef est compromis ou biaisé, tout le système hérite du biais sans recours. Les protocoles BFT (PBFT, etc.) répondent par des seuils de quorum (⚠ seuil exact du type 2f+1 à vérifier selon la variante précise du protocole avant citation) plutôt que par une hiérarchie.

Point clé : si un conseil d'agents tourne sur le même modèle sous-jacent pour tous les votants, un chef élu parmi eux hérite structurellement du même biais que les votants — BFT indique que la robustesse vient de la diversité des sources de défaillance, pas de la structure de vote elle-même.

## 4. Liquid Democracy / vote délégatif — chef dynamique et révocable

~ Courant popularisé en science politique computationnelle (⚠ références académiques précises non vérifiées, à confirmer) : chaque agent peut déléguer son vote à un autre agent jugé plus compétent sur ce sujet précis, révocable à tout moment. Structurellement proche d'un chef contextuel et temporaire, réévalué en continu — répond au problème de granularité sans figer une hiérarchie a priori.

## Le fil qui relie ces quatre cadres

Aucun ne répond "oui" ou "non" à "faut-il un chef" — tous convergent vers : le chef doit être une fonction d'agrégation apprise et corrigée par le signal réel, jamais un agent-pair simplement promu. Dès que le chef est un agent parmi les votants (même avec un vote pondéré plus fort), le problème de corrélation de biais revient — le chef n'échappe pas à ses propres angles morts ; il doit être structurellement différent des votants pour apporter un signal indépendant.

## Question de conception restée ouverte

Cherche-t-on un chef qui arbitre les désaccords (résout le conflit), ou un chef qui détecte qu'il y a désaccord et route vers un humain ? Deux architectures très différentes. Voir [chef-arbitre vs chef-détecteur](../05-questions-ouvertes/chef-arbitre-vs-detecteur.md).

## Complément narratif : le livre de Moussaïd

Voir [Mehdi Moussaïd — "A-t-on besoin d'un chef ?"](./moussaid-a-t-on-besoin-dun-chef.md) pour un cadrage en trois régimes selon la topologie du problème (réponse vérifiable + erreurs indépendantes / réponse vérifiable + erreurs corrélées / pas de réponse vérifiable).
