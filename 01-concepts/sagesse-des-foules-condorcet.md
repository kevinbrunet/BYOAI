# Sagesse des foules et théorème de Condorcet — deux régimes, pas un

## La condition de validité qu'on oublie

L'analogie "sagesse des foules" appliquée à plusieurs agents IA a une condition de validité précise. ✓ Le théorème du jury de Condorcet exige que chaque votant soit meilleur que le hasard et que les erreurs soient indépendantes. Deux modèles biaisés dans la même direction ne votent pas indépendamment — ils confirment le même angle mort avec plus d'assurance. C'est le piège central à éviter dans toute architecture multi-agents.

## Régime homogène (même modèle, même prompt, n tours)

La probabilité de succès P(n) plafonne à une asymptote A < 1, où A dépend du taux de biais systématique du modèle sur la classe de problème donnée. Passé un certain n*, la courbe est quasi plate : on paie du coût pour un gain de probabilité négligeable, parce qu'on ne fait que retirer la même carte dans le même paquet biaisé.

**Signal pour détecter le plateau, sans instrumentation a priori** : si les sorties successives d'un même agent bouclé n fois convergent vers une réponse quasi identique (peu de variance inter-tours), c'est le signe que le modèle a épuisé sa diversité interne — plus de tours ne fait qu'échantillonner le même mode de sa distribution. À l'inverse, si les tours continuent à produire des corrections substantiellement différentes, l'asymptote n'est pas encore atteinte et un tour de plus reste rentable.

⚠ Aucune valeur empirique générale pour "combien de tours avant plateau" — ça dépend de la température d'échantillonnage, de la taille du modèle, du type de tâche. Mesurable sur un pipeline donné (variance de sortie tour à tour), pas déductible théoriquement.

## Régime hétérogène (second modèle/prompt/perspective, biais décorrélé)

Si les erreurs des deux points de vue sont statistiquement indépendantes, la probabilité d'erreur combinée devient (1−p₁)(1−p₂) au lieu de (1−p)² — un saut discret dans la courbe, pas une continuation de la même pente. C'est un changement de régime, pas juste "un tour de plus".

## Le vrai test de nécessité d'un second point de vue

La question n'est pas "ai-je fait assez de tours" mais : est-ce que l'erreur recherchée est dans la classe des erreurs que ce modèle peut voir ? Un modèle ne peut pas s'auto-corriger sur un angle mort qui est un biais de son propre entraînement — par définition, il ne le voit pas comme une erreur. La boucle homogène optimise la trajectoire la plus probable (le happy path), elle ne cartographie pas les edge cases hors de sa distribution d'entraînement — voir [le happy path n'existe pas](./happy-path-illusion-statistique.md) pour la mesure statistique de ce phénomène.

Conséquence contre-intuitive : un second point de vue n'est pas utile quand la probabilité d'erreur est haute, il est utile quand la classe d'erreur suspectée est structurelle au modèle — indépendamment d'où on est sur la courbe. Un modèle avec p=0,95 peut avoir besoin d'un second avis bien avant un modèle avec p=0,6, si son erreur résiduelle de 5% est concentrée exactement sur la catégorie de risque qui compte (~ logique de pondération sévérité × occurrence proche de l'esprit d'une analyse de risque FMEA/ISO 14971, formulation exacte à vérifier directement dans le texte normatif plutôt qu'à citer de mémoire).

## Conséquence architecturale

Le critère de déclenchement d'un second modèle ne devrait pas être un seuil de score de confiance global, mais une détection de catégorie de risque : basculer en mode hétérogène quand la classe d'erreur suspectée est un angle mort structurel connu, plutôt que de simplement boucler plus longtemps sur l'agent primaire.

Mais voir [taxonomie des angles morts construite empiriquement](./taxonomie-angles-morts-empirique.md) : cette détection par catégorie a priori se heurte à un problème d'épistémologie plus profond.
