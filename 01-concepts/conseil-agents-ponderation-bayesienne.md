# Conseil d'agents et pondération bayésienne de réputation

## Le mécanisme proposé

Un conseil d'agents où chaque agent a une voix et donne son degré de confiance. En production, en cas de bug, on regarde qui avait un vote sûr et faux, et on dégrade sa pondération pour l'espace de problème concerné.

C'est sain dans son principe — une forme de pondération bayésienne de réputation par sous-espace de problème — mais quatre failles se révèlent si on les découvre en prod plutôt qu'avant.

## Faille 1 — Confiance ≠ calibration

Rien ne garantit que le score de confiance verbalisé par un agent LLM est calibré, c'est-à-dire que parmi tous les votes où il annonce "95%", il a effectivement raison 95% du temps. ✓ Problème documenté dans la littérature ML : les LLM ont tendance à être systématiquement surconfiants, et cette surconfiance n'est pas uniforme selon le domaine de la question.

Conséquence pratique : dégrader sur la base d'un chiffre de confiance non calibré ne mesure pas "cet agent est mauvais sur ce problème", mais "cet agent verbalise mal son incertitude sur ce problème" — pas la même chose, pas la même correction. Une phase de calibration préalable est nécessaire : sur un échantillon de cas avec vérité terrain connue, est-ce que le taux de succès réel à confiance=90% est bien ~90% ? Sinon, la dégradation se fait sur du bruit.

## Faille 2 — Le problème d'attribution de crédit (credit assignment)

Un incident en production est souvent le produit de plusieurs agents qui ont voté confiants et faux ensemble, parce qu'ils partagent le même angle mort (biais corrélé, pas indépendant — voir [Condorcet](./sagesse-des-foules-condorcet.md)). Dégrader individuellement chaque agent qui avait un vote sûr punit symétriquement des agents dont l'erreur avait une cause commune, sans jamais identifier la cause. Le système devient méfiant envers plusieurs agents à la fois sur la même classe de problème, sans jamais savoir si le vrai problème est "ces agents sont mauvais ici" ou "ces agents tournent sur le même modèle sous-jacent avec le même trou de couverture".

## Faille 3 — Taille d'échantillon : un incident ne doit pas faire osciller le poids

Dégrader sur un seul incident, c'est réagir au bruit statistique. Il faut une mise à jour bayésienne avec un prior, pas une dégradation dure au premier échec — sinon le système sur-réagit à des cas isolés et sous-réagit à des biais systématiques qui s'accumulent lentement sans jamais franchir un seuil de déclenchement individuel. ⚠ Le nombre d'observations nécessaires avant de faire confiance à une dégradation dépend de la tolérance au risque par catégorie — pas de formule générale, c'est un choix de design à calibrer sur les données réelles.

## Faille 4 — Granularité de "l'espace de problème"

Qui définit cet espace ? Trop fin (un cas très spécifique) et on n'accumule jamais assez de données pour qu'un signal émerge. Trop grossier et un vrai signal de blind spot se dilue dans un espace qui contient aussi plein de cas où l'agent est bon. C'est le même problème de taxonomie que dans [taxonomie des angles morts empirique](./taxonomie-angles-morts-empirique.md) — sauf qu'ici il est nécessaire dès la conception du mécanisme de pondération, pas seulement en aval.

## Cadre théorique existant à emprunter plutôt qu'à réinventer

✓ Ce mécanisme ressemble structurellement aux algorithmes de type Multiplicative Weights / Hedge en apprentissage en ligne (Littlestone & Warmuth) — un cadre théorique existant pour gérer "combien dégrader un expert après une erreur, sans sur-réagir ni sous-réagir", avec des garanties de regret prouvées. Voir aussi [architectures de référence pour l'agrégation multi-agents](../03-exemples/architectures-agregation-references.md) (AdaBoost notamment).

## Question de conception non résolue

Le conseil d'agents utilise-t-il le même modèle sous-jacent pour tous les votants, ou des modèles différents ? Si c'est le même modèle avec des prompts différents, la dégradation par agent risque de n'être qu'un théâtre de gouvernance — les votes ne sont pas indépendants au sens de Condorcet, et pondérer différemment des instances du même modèle biaisé ne corrige rien de structurel.
