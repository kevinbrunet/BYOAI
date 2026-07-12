# Chapitre 2 — Le happy path n'existe pas

Le chapitre précédent a montré pourquoi le logiciel d'entreprise est détesté : on ne peut pas le quitter. Mais la captivité n'explique pas tout. Un prisonnier peut être bien logé. Si le logiciel imposé couvrait correctement le travail réel, la colle humaine — les recettes de cuisine, le collègue qui sait — n'aurait pas besoin d'exister. Or elle existe partout, dans toutes les organisations, autour de tous les outils. Ce chapitre explique pourquoi : le logiciel de gestion repose sur une erreur de probabilités. Pas une erreur de tel éditeur ou de tel projet — une erreur que tout le monde commet, qui tient en une phrase, et qui se répare.

## L'intuition 20/80

Demandez à une équipe projet comment elle conçoit un parcours utilisateur. La réponse, presque toujours, s'appuie sur une intuition jamais interrogée : 80 % des utilisateurs suivent le chemin nominal — le happy path, celui où tout se passe bien — et les 20 % restants tombent dans des cas particuliers qu'on traitera "à la marge". On conçoit donc pour le nominal, on teste le nominal, on budgète le nominal. Les exceptions auront des tickets.

Cette intuition paraît raisonnable. Elle est fausse, et pas d'un peu — fausse dans des proportions qui changent la nature du problème.

## Le calcul qui change tout

Prenez un parcours de dix étapes : saisir une demande, joindre une pièce, obtenir une validation, générer un document, notifier un tiers... rien d'exotique, c'est la granularité ordinaire d'un processus de gestion. Accordez à chaque étape une fiabilité généreuse : 90 % de chances que tout se passe nominalement — la donnée est là, le droit est ouvert, le service répond, l'utilisateur ne s'est pas trompé.

La probabilité de traverser les dix étapes sans quitter le chemin nominal est de 0,9 puissance 10 : environ 35 %.

Relisez ce chiffre. Avec des hypothèses favorables — 90 % de fiabilité à chaque pas, aucune malveillance, aucun cas tordu — **près de deux sessions sur trois sortent du happy path**. Pas à cause d'un bug. Pas à cause d'un utilisateur incompétent. Par simple arithmétique de la diversité réelle : une donnée manquante ici, un droit révoqué là, un timeout, une pièce au mauvais format, une validation qui expire. Allongez le parcours, ajoutez des intégrations, des profils de droits différenciés — la probabilité s'effondre encore.

Ce qu'on appelle "cas limite" est, statistiquement, la majorité des sessions réelles. Le nominal n'est pas la norme dont les exceptions s'écartent ; c'est le cas particulier le plus confortable. L'intuition 20/80 inverse exactement la réalité : c'est du 35/65, et le 65 est du mauvais côté.

## Ce que le générique implémente vraiment

Voici maintenant le pas décisif du raisonnement. Qu'est-ce qu'un logiciel de gestion générique, conçu pour des milliers d'organisations ou pour tous les services d'une même entreprise ? C'est, par construction, l'implémentation du consensus — c'est-à-dire des cas communs, c'est-à-dire du chemin nominal. Le générique ne peut pas faire autrement : chaque déviation est spécifique à un contexte (cette donnée-là manque souvent dans ce service-là, ce fournisseur-là envoie ce format-là), et le générique existe précisément pour ignorer les contextes. Couvrir les déviations de chacun, c'est cesser d'être générique.

Assemblons les deux faits. Le générique implémente le nominal ; le nominal couvre un tiers des sessions réelles. Conclusion : **l'application d'entreprise générique est structurellement inadaptée à la majorité de ce qui se passe réellement** — non par incompétence des DSI ni des éditeurs, mais par propriété mathématique. On peut changer d'éditeur, refondre, migrer : tant qu'on achète du générique, on achète une couverture du tiers nominal. C'est pourquoi chaque refonte reproduit la déception de la précédente — on remplace un tiers par un autre tiers, mieux décoré.

Et les deux tiers restants ? Le chapitre 1 a déjà répondu : ils sont pris en charge par la colle humaine. La recette de cuisine n'est pas une bizarrerie folklorique — c'est le système de gestion des déviations de l'entreprise, non financé, non documenté, non testé, mais parfaitement réel. La procédure officielle traite le nominal ; la machine à café traite la production.

## L'armoire à fibre optique

Une image, pour fixer ce que produit un système piloté par le nominal quand la réalité dévie. Dans les armoires de brassage des opérateurs de fibre optique, tout fonctionne parfaitement sur le papier : les tickets de raccordement sont traités un par un, rationnellement, par ordre de priorité. Et pourtant certaines armoires sont un chaos de câbles inextricable, où les pannes se multiplient sans cause apparente.

Le mécanisme : un technicien arrive, ticket en main. Plus de port disponible ? Il débranche "temporairement" un client voisin pour raccorder le sien — son ticket est résolu, il repart. Le lendemain, un autre technicien fait de même pour résoudre le sien. Puis un troisième. Chaque intervention est individuellement rationnelle, localement correcte, conforme au processus. La somme est une boucle de panne infinie.

Le problème n'est pas la compétence des techniciens — pas plus que celle des utilisateurs de nos logiciels. Le problème est que le système récompense la résolution du symptôme dans le cadre nominal (le ticket est fermé) et ne voit pas les déviations qu'il engendre (le voisin débranché). Un système conçu pour le happy path ne devient pas simplement incomplet face aux déviations : il les fabrique, silencieusement, en aval. Retenez cette armoire — elle reviendra quand nous parlerons de mémoire des décisions et de la fonction qui manque pour détecter ces boucles.

## Redéfinir le normal

La première conséquence est une question de test, et elle mérite d'être dite aux équipes : tester le happy path, c'est tester ce qui arrive le moins. Une session incomplète, une donnée absente, un droit révoqué en cours de route, une action répétée par erreur — ce ne sont pas des edge cases, ce sont des cas nominaux que personne n'a voulu nommer ainsi. La robustesse d'un système se mesure à ce qu'il fait quand les conditions ne sont pas réunies, puisque "les conditions ne sont pas réunies" est le régime majoritaire.

Mais la conséquence qui porte ce livre est plus profonde. Si les déviations sont majoritaires et si elles sont, par nature, spécifiques à chaque contexte — ce service, ce poste, ce client, cette donnée — alors la couverture des déviations ne peut pas venir d'un surcroît de générique. Elle ne peut venir que du spécifique : des outils qui épousent le travail réel d'un poste donné, déviations comprises. Ce qui condamnait le spécifique jusqu'ici n'était pas son inutilité — c'était son coût. Un développement sur mesure par poste de travail était économiquement absurde ; alors on a uniformisé, et la machine à café a absorbé la différence.

C'est exactement ce coût qui vient de s'effondrer, et le chapitre 4 mesurera précisément ce qui s'est effondré — et ce qui ne s'est pas effondré, car il y a un piège, et il est sérieux. Disons-le dès maintenant pour ne pas être accusé de vendre du rêve : donner un générateur de code à chaque salarié et le laisser couvrir ses déviations tout seul, c'est lui faire coder *son* happy path à lui — sans tests, sans architecture, sans mémoire. Le problème ne disparaît pas, il se fragmente en mille exemplaires. La façon d'éviter ça est une affaire d'architecture et de rôles, et c'est le cœur des chapitres suivants.

Avant cela, il reste un fait à établir. Ce mouvement vers le spécifique n'est pas une hypothèse d'école dont on débattrait tranquillement : il a déjà commencé, sans autorisation, à grande échelle, dans vos murs. C'est l'objet du chapitre 3.

---

## Notes de rédaction (hors manuscrit)

- Le calcul 0,9¹⁰ ≈ 34,87 % : arrondi à 35 % dans le texte, hypothèses explicitées (10 étapes, 90 % par étape) pour que le lecteur puisse refaire le calcul — c'est voulu : la falsifiabilité commence ici.
- L'armoire à fibre : issue de la réaction à la conférence "Éloge de la simplicité" (Frédéric Leguédois) — créditer la conférence en note finale du livre ; le post LinkedIn d'origine est déjà publié. Teaser volontaire vers DCB/épidémiologiste (ch. 7 et 13) : "retenez cette armoire".
- La chaîne complète happy path → générique=nominal → colle humaine = gestion des 65 % → spécifique nécessaire → spécifique naïf insuffisant est celle actée dans [happy-path — place dans le livre](../01-concepts/happy-path-illusion-statistique.md).
- Le piège du spécifique naïf est annoncé (une phrase dure : "coder son happy path à lui") mais non développé — renvoi ch. 4 (données) et ch. 13 (rôles). Vérifier à la rédaction du ch. 13 que la promesse est tenue.
- Aucune référence chiffrée externe dans ce chapitre (le seul nombre est un calcul interne) — cohérent avec la règle : les chiffres sourcés arrivent au ch. 3 (adoption) et ch. 4 (méta-analyse).
- Grille lecteur : répond à la question DSI/CTO "pourquoi chaque refonte reproduit-elle le problème ?" — la réponse exonère le lecteur (propriété mathématique, pas incompétence), même mécanique d'empathie que le ch. 1.
- Sources ontologie : [happy-path-illusion-statistique](../01-concepts/happy-path-illusion-statistique.md), [paradoxe-armoire-fibre-optique](../01-concepts/paradoxe-armoire-fibre-optique.md).
