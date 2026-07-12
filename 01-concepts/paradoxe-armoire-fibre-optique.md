# Le paradoxe de l'armoire à fibre optique

## Le constat

Sur le papier, tout fonctionne parfaitement : les tickets sont traités un par un, rationnellement, par ordre de priorité. Pourtant, dans certaines armoires de brassage fibre, c'est un chaos absolu.

Plus de place visible ? Un technicien débranche temporairement un voisin pour raccorder un nouveau client et résoudre son ticket. Le lendemain, un autre technicien fait la même chose pour résoudre le sien. Puis un troisième. On entre alors dans une boucle de panne infinie.

## Le diagnostic

Le problème n'est pas la compétence des intervenants. Le problème est que le système récompense la résolution du symptôme, pas la compréhension de la cause. Chaque intervention est individuellement rationnelle et localement correcte — c'est la somme de décisions locales sans mémoire partagée qui produit le chaos global.

## Ce que ça implique

Anticiper le futur (plans détaillés à cinq ans, prédiction) est souvent une illusion coûteuse. Tirer les leçons du passé, en revanche, est une discipline praticable : le passé ne prédit rien, il explique — il révèle les structures, les dépendances et les boucles que l'urgence du présent rend invisibles.

## Lien direct avec le reste de la série

Ce paradoxe est une illustration concrète du problème que [DCB — les décisions comme events](./dcb-decisions-comme-events.md) cherche à résoudre : sans stream de décisions traçable (qui a débranché quoi, quand, pourquoi), chaque technicien opère à l'aveugle sur les dépendances laissées par les décisions précédentes. Voir aussi [l'épidémiologiste du backlog](./epidemiologiste-du-backlog.md) pour la fonction organisationnelle qui manque pour détecter ce genre de boucle avant qu'elle ne devienne chronique.

## Source

Post LinkedIn de Kevin, en réaction à la conférence "Éloge de la simplicité" de Frédéric Leguédois — voir [backlog des posts](../00-meta/backlog-posts.md) pour le contexte de publication.
