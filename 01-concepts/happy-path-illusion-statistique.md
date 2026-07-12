# Le happy path n'existe pas — l'illusion statistique du 20/80

## L'intuition commune, et pourquoi elle est fausse

La croyance répandue : 80% des utilisateurs empruntent le chemin nominal, les 20% restants tombent dans des cas limites. On teste donc surtout le happy path, et on gère les exceptions "à la marge". C'est une erreur de probabilités, pas un raccourci acceptable.

## Le calcul

Un parcours utilisateur avec 10 étapes, où la probabilité de rester dans le chemin nominal est de 90% à chaque étape : la probabilité de traverser tout le parcours sans déviation est 0,9¹⁰ ≈ 35%.

Autrement dit : dans deux sessions sur trois, quelque chose sort du nominal — pas à cause d'un bug, pas à cause d'un utilisateur atypique, juste parce que la réalité est diverse. Allonger le parcours, ajouter des intégrations, introduire de la latence, des droits différenciés, des données manquantes : la probabilité de rester dans le happy path s'effondre encore plus vite.

**Ce qu'on appelle "cas limite" est, statistiquement, la majorité des sessions réelles.**

## La conséquence inconfortable

Ce qu'on teste en priorité : le flux nominal complet, fonctionnel, avec des données propres. Ce qui arrive en production : des sessions incomplètes, des états intermédiaires, des transitions que personne n'a prévues.

Le mode dégradé n'est pas une option, c'est le régime de fonctionnement par défaut. Tester le happy path, c'est tester ce qui arrive le moins. Ce n'est pas qu'il ne faut pas le tester — c'est qu'il ne faut pas s'y arrêter : la robustesse d'un système se mesure à ce qu'il fait quand les conditions ne sont pas réunies (timeout partiel, donnée absente, droit révoqué en cours de session, action répétée par erreur).

Ces scénarios ne sont pas des edge cases. Ce sont des cas nominaux que personne n'a voulu nommer ainsi. Redéfinir ce qui est "normal" en test, c'est changer ce qu'on considère comme acceptable en production.

## Lien avec le reste de la série

Ce même constat structure déjà deux fichiers antérieurs sans que le lien explicite ait été posé :

- [Sagesse des foules et Condorcet](./sagesse-des-foules-condorcet.md) : "la boucle homogène optimise la trajectoire la plus probable (le happy path), elle ne cartographie pas les edge cases hors de sa distribution d'entraînement" — l'argument statistique ici en donne la mesure chiffrée.
- [Taxonomie des angles morts construite empiriquement](./taxonomie-angles-morts-empirique.md) : si les cas limites sont statistiquement majoritaires, la taxonomie des angles morts n'est pas un raffinement marginal, c'est la cartographie du régime de fonctionnement principal du système.
- [Le paradoxe de l'armoire à fibre optique](./paradoxe-armoire-fibre-optique.md) illustre concrètement ce que produit un système optimisé pour le chemin nominal quand la réalité (dégradations locales successives) en dévie.

## Place dans le livre — TRANCHÉ (2026-07-11)

Le happy path entre dans le livre comme **justification stratégique du problème de toute application d'entreprise**, et il porte une chaîne argumentative complète :

1. **Le problème stratégique** : une application générique est, par construction, l'implémentation du chemin nominal — le consensus des cas communs. Or le nominal ne couvre que ~35 % des sessions réelles : l'application générique est donc structurellement inadaptée à la majorité de ce qui se passe. Ce n'est pas un défaut d'exécution des DSI, c'est une propriété mathématique du générique.
2. **La jonction avec la captivité** : les deux tiers de sessions hors nominal, c'est précisément ce que comblent les [recettes de cuisine](./captivite-logicielle-happy-path-social.md) — la colle humaine est la gestion manuelle des déviations que le générique ne couvre pas. Les deux ouvertures du livre (constat vécu + constat statistique) sont les deux faces du même fait.
3. **Ce que le spécifique résout** : l'interface spécifique couvre les déviations *de ce poste-là* — elle attaque directement les 65 % que le générique abandonne.
4. **La limite qui milite pour le métier augmenté** : le spécifique écrit par un néophyte reproduit le problème un cran plus bas — il code SON happy path, sans tests, sans architecture (la [méta-analyse](../06-etat-de-lart/meta-analyse-cout-aval.md) chiffre exactement ça : ~45 % de code vulnérable, dette survivante). D'où le [métier augmenté / développeur-harnais](./equipe-agile-developpeur-harnais.md) : le professionnel apporte ce que le néophyte n'a pas — la culture du test et de l'architecture, c'est-à-dire la couverture des déviations — et le [cycle de promotion](./cycle-promotion-specifique.md) impose cette exigence au moment où l'outil se partage.

En une phrase : le happy path justifie pourquoi le générique échoue, pourquoi le spécifique est nécessaire, ET pourquoi le spécifique ne peut pas être naïf — c'est le pivot entre le problème et la méthode.

## Statut éditorial

Post 1 de la série ("Post 1 — Le happy path n'existe pas"), déjà rédigé. Audience visée : product owners, tech leads. Voir [backlog des posts](../00-meta/backlog-posts.md).
