# Exemple — Git, DoD, DoR dans la DSI

## Le cas

Le principe de séparation structure/interface s'applique y compris à l'intérieur de la DSI elle-même.

- **Structure (commune, portée par l'entreprise)** : le dépôt Git, la vérification de sécurité, les rôles, les états des tickets, les Definition of Done (DoD), les Definition of Ready (DoR).
- **Interface (individuelle, portée par le collaborateur)** : comment l'étape est concrètement réalisée.

## Pourquoi c'est le meilleur exemple de la série

C'est concret, vérifiable, et ça ancre immédiatement l'abstraction "structure vs organe de production" dans quelque chose que n'importe quel développeur reconnaît directement. Recommandation éditoriale : le mettre en premier dans le texte final, pas en illustration finale — inverser l'ordre théorie-puis-exemple rend la lecture plus dense, cet exemple devrait porter l'abstraction dès le départ.

## Où le BYOIA s'insère

C'est précisément là que le [BYOIA](../01-concepts/byoia.md) s'insère : il connecte les API de l'entreprise (Git, Jira, Teams) à l'équipe IA personnelle du collaborateur pour produire le travail demandé, et renvoie les données nécessaires au suivi via ces mêmes API vers la partie commune.

## Généralisation

Le principe se généralise à tous les métiers, pas seulement à la DSI : support, RH, autres fonctions. Chacun interagit avec une plateforme commune portée par l'entreprise, et branche son harnais personnel dessus — pour la RH, ce sera un autre socle que Git/Jira/Teams, mais le principe de séparation reste identique.
