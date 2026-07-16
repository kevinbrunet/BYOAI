# Exemple — La CI/CD n'échappe pas à la règle

## Le principe

La CI/CD n'est pas un cas à part : c'est un processus d'entreprise comme un autre, et la [doctrine frontière SI/interface](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) s'y applique telle quelle. Elle sert ici de cas d'école pour vérifier le triptyque **SI / rôle / interface** sur un terrain que tout développeur connaît par cœur — dans la continuité directe de [Git, DoD, DoR dans la DSI](./git-dod-dor-dsi.md), qu'elle approfondit.

## Ce qui est SI

Trois couches distinctes, toutes du côté SI :

1. **Les tools** — GitHub/GitLab, les agents de build, etc. Le SI est responsable de ces technologies, qu'il expose via des interfaces standardisées (CLI, serveur MCP, API REST). Le tool ne fait qu'exposer une capacité ; il n'incarne pas le processus.
2. **Le workflow** — le flux production sur une branche → PR vers `develop` → review → tests unitaires obligatoires, etc. Ce workflow n'est pas une propriété de l'outil : c'est un accord d'équipe qui *naît au-dessus* des outils. GitHub/GitLab rendent ce flux possible, ils ne le définissent pas.
3. **Les métriques de suivi** — le workflow produit des indicateurs (délai de review, taux d'échec des tests, taux d'escalade) qui permettent de l'adapter aux cas rencontrés. Boucle de rétroaction du même ordre que la [taxonomie des angles morts construite empiriquement](../01-concepts/taxonomie-angles-morts-empirique.md).

## Ce qui est rôle

Le workflow — comme les rôles qu'il fait exister (produire du code, review une PR, etc.) — est **administré par un rôle**, au sens de la [séparation rôle/personne de l'holacratie](../01-concepts/holacratie-parallele.md) : le rôle définit le périmètre et la redevabilité, indépendamment de qui l'occupe.

Chaque rôle est rempli par une personne qui **porte la responsabilité du rôle**. Cette personne délègue ensuite à son harnais tout ou partie de la tâche — elle reste garante de la production, quelle que soit la part que son IA a exécutée. C'est la même mécanique que le [développeur-harnais](../01-concepts/equipe-agile-developpeur-harnais.md) : le harnais est l'outil de production, pas le titulaire du rôle.

Conséquence pour la conception du processus : il doit être **désigné pour mitiger le risque d'un mauvais code ou d'une mauvaise PR de la même manière**, qu'elle soit produite par un humain ou par une machine. Le workflow ne traite pas différemment un commit humain et un commit généré — les mêmes garde-fous (review obligatoire, tests, DoD) s'appliquent aux deux. C'est la même logique que « [le critère porte sur l'artefact, pas sur l'auteur](../04-objections/frontiere-si-ia-genere-code.md) », appliquée ici à la sécurité du pipeline plutôt qu'à la frontière SI/interface elle-même.

## Ce qui est interface

Chaque rôle est libre d'utiliser le harnais qu'il entend, du moment qu'il respecte les règles établies et utilise les tools pour communiquer avec le SI. La personne reste garante de la production et libre de designer l'outil qu'elle veut pour remplir sa tâche — c'est la définition même de l'interface dans la doctrine : personne d'autre n'a besoin de s'y fier, donc c'est libre.

## Le triptyque récapitulé

| | Contenu | Qui porte |
|---|---|---|
| Tools | GitHub/GitLab, agents de build, exposés via CLI/MCP/API REST | SI |
| Workflow | branche → PR → review → tests obligatoires | SI (design et maintenance : un rôle) |
| Métriques | délai, taux d'échec, taux d'escalade | SI |
| Harnais | l'outil personnel de chaque rôle pour exécuter sa part | Interface, libre |

## La sécurité d'utilisation

Quatre mécanismes, qui recoupent l'architecture déjà posée pour le BYOIA plutôt que d'en inventer une nouvelle :

- **Enrôlement du périphérique** — le device qui porte le harnais est enrôlé (MDM/mTLS), condition d'entrée déjà posée dans l'[architecture BYOIA](../01-concepts/byoia.md).
- **Proxy de filtrage** — un proxy qui filtre les IA frontière autorisées (allowlist de modèles) et filtre/anonymise les données envoyées. Voir [gateways de sécurisation LLM](./gateways-securisation-llm.md) pour le comparatif des solutions existantes.
- **Droits délégués à durée de vie courte** — les droits délégués à l'agent, consommés par les tools, ont une durée de vie courte, associée à la tâche, et validée par l'humain. C'est un raffinement du mécanisme de [délégation d'identité JWT/mTLS](../01-concepts/delegation-agents-jwt-mtls.md) : ⚠ la contrainte de durée de vie courte et de lien explicite à la tâche est un principe cohérent avec l'architecture d'attenuation déjà documentée (dérivation d'un token attenuable avant chaque appel), mais elle n'a pas été vérifiée comme implémentée telle quelle dans une plateforme CI/CD réelle — à valider avant de la présenter comme acquise dans le livre.
- **API humain-only** — certaines API ne sont exécutables que par un humain, pour rester conforme aux besoins réglementaires (AI Act, normes ISO, etc.). C'est exactement le troisième régime déjà décrit dans la [délégation d'identité](../01-concepts/delegation-agents-jwt-mtls.md) (section « la nature de l'appelant ») : humain uniquement, même avec une chaîne de délégation valide.

## Généralisation

Ce principe s'applique à tout processus de l'entreprise, pas seulement à la CI/CD — c'est la même généralisation déjà notée dans [Git, DoD, DoR dans la DSI](./git-dod-dor-dsi.md#généralisation) : structure commune portée par le SI, harnais individuel portée par la personne qui tient le rôle. La CI/CD n'est qu'un cas particulier, choisi parce qu'il est familier à tout développeur — pas parce qu'il est spécial.

## Où ça s'insère dans le livre

Prolonge [Git, DoD, DoR dans la DSI](./git-dod-dor-dsi.md), qui reste l'exemple d'entrée (le plus lisible, le plus court). Celui-ci peut servir de développement pour un lecteur technique qui veut voir le mécanisme jusqu'au bout — rôle, délégation, sécurité, métriques.
