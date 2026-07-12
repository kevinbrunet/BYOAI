# Taxonomie des angles morts — construite empiriquement, pas définie a priori

## Le problème d'épistémologie

On ne peut pas définir a priori la taxonomie des angles morts d'un modèle, parce que la connaître supposerait déjà les avoir cartographiés. On ne peut pas écrire une règle de détection "si catégorie X alors bascule hétérogène" pour un X qu'on n'a pas encore observé — ce n'est pas seulement un problème d'ingénierie, c'est un problème d'épistémologie.

## Ce que ça change concrètement

Le mécanisme de déclenchement ne peut pas être une taxonomie de risques figée à l'avance. Il doit être un signal de surprise a posteriori — quelque chose qui détecte, après coup, que la réalité a divergé de ce que le modèle homogène prédisait avec confiance.

### Deux familles de signaux exploitables

1. **Divergence rétrospective** : logger les cas où l'agent primaire a validé avec haute confiance, et comparer après coup au résultat réel (incident en prod, bug remonté, non-conformité détectée en revue humaine). Chaque divergence haute-confiance/résultat-réel-faux est une instance d'angle mort découverte — la classe se construit empiriquement, ticket après ticket, ce n'est pas une définition figée.
2. **Désaccord inter-modèles comme détecteur, pas comme correcteur** : faire tourner systématiquement (ou en échantillonnage) un second modèle en parallèle sur un sous-ensemble ; le désaccord lui-même devient le signal d'alerte — pas la réponse du second modèle qui prime, mais l'écart qui déclenche une revue humaine ou un troisième arbitre. On n'utilise plus l'hétérogénéité pour corriger, on l'utilise pour détecter où chercher.

## La conséquence dure à avaler

Le coût du second point de vue n'est pas seulement le coût du tour supplémentaire — c'est le coût de construction progressive d'une taxonomie d'erreurs qu'on ne peut financer que par l'expérience réelle en production ou en test. Il n'y a pas de raccourci théorique qui dispense d'observer réellement où le système se plante. La courbe coût/complexité n'est donc pas calculable en amont — elle s'écrit rétrospectivement, à mesure que la taxonomie des angles morts s'enrichit.

Conséquence pratique : loguer systématiquement les désaccords inter-agents (même sans basculer en mode hétérogène par défaut) comme matière première pour affiner, au fil du temps, quelles catégories de cas méritent structurellement un second avis. C'est un détecteur qui apprend, pas une règle qu'on écrit une fois.

## Point de convergence possible avec les exigences de traçabilité réglementaire

⚠ Question ouverte, non vérifiée : ce mécanisme de logging des divergences ne recoupe-t-il pas exactement le type de traçabilité qu'une norme comme IEC 62304 pourrait déjà demander de justifier pour un dispositif logiciel réglementé — auquel cas la contrainte réglementaire et le besoin architectural convergeraient, plutôt que d'être deux couches séparées ? Formulation exacte des exigences à vérifier directement dans le texte normatif avant toute affirmation.

## Lien avec le reste

Ce principe s'applique directement au [conseil d'agents et pondération bayésienne](./conseil-agents-ponderation-bayesienne.md) : la granularité de "l'espace de problème" sur lequel on dégrade un agent est exactement ce problème de taxonomie, mais nécessaire dès la conception du mécanisme de pondération, pas seulement en aval.
