# État de l'art — Mesurer la complexité : de quoi outiller la fenêtre (recherche web + littérature, juillet 2026)

Répond au point 8 de [questions-restantes](../00-meta/questions-restantes.md) : la [fenêtre de complexité](../01-concepts/cycle-promotion-specifique.md) a besoin d'une unité. La littérature existe, sur quatre étages.

## Étage 1 — Complexité du code (50 ans de littérature)

- ✓ **Complexité cyclomatique** (McCabe, 1976) : nombre de chemins d'exécution indépendants. Le doyen, toujours utilisé, mais corrélé essentiellement à la taille.
- ✓ **Complexité cognitive** (Campbell/SonarSource, 2018) : pénalise l'imbrication et les ruptures de flux — conçue pour mesurer la difficulté *humaine* de compréhension, pas la difficulté machine.
- ✓ **Maintainability Index** (Oman & Hagemeister, 1992 ; intégré à Visual Studio) : composite volume/complexité/taille.
- **Limite pour la fenêtre** : ces métriques notent un fichier, pas un périmètre de considération. Nécessaires, pas suffisantes.

## Étage 2 — Complexité d'architecture (le coût des dépendances)

- ✓ **Propagation cost** (MacCormack, Baldwin, Rusnak — Harvard Business School) : à partir de la matrice de dépendances (DSM), pourcentage du système potentiellement affecté par un changement en un point. C'est mathématiquement **le "coût de prise en compte" de la fenêtre** : combien de choses bougent quand une chose bouge.
- ✓ **Métriques de couplage** (fan-in/fan-out, instabilité de Martin) : classiques, outillées partout.
- ✓ **Entropie des changements** (Hassan, 2009) : la dispersion des modifications prédit les défauts mieux que la complexité statique.

## Étage 3 — Dette et coût en unités de temps (les méthodes industrielles)

- ✓ **SQALE** : méthode d'évaluation de la dette technique exprimée en **temps de remédiation** (jours-homme) — implémentée dans SonarQube. Donne à la fenêtre une unité monnayable : la dette du périmètre en jours.
- ✓ **ISO/IEC 5055 (CISQ)** : standard de mesure automatisée de la structure du logiciel sur 4 axes dont la maintenabilité — détection avant mise en production des faiblesses structurelles. L'argument d'autorité pour un DSI : la mesure de maintenabilité est un standard ISO, pas une lubie.
- ✓ **Modèle SIG** (Software Improvement Group, adossé à ISO 25010) : notation en étoiles de la maintenabilité, calibrée sur un benchmark de milliers de systèmes.

## Étage 4 — La capacité de l'équipe (l'autre moitié de la fenêtre)

- ✓ **CodeScene / Adam Tornhill ("Your Code as a Crime Scene")** : l'approche la plus proche de la fenêtre. Analyse *comportementale* : croise la complexité du code avec la **fréquence de modification** (hotspots) et les facteurs organisationnels (combien de personnes/équipes touchent le même code). Leur "Code Health" est validé empiriquement contre la vélocité et la densité de défauts (résultats publiés supérieurs à SonarQube). Idée clé transposable : **la complexité qui compte est celle qu'on touche** — un code affreux jamais modifié ne consomme pas de fenêtre.
- ✓ **Team Topologies** (Skelton & Pais) : la **charge cognitive d'équipe** comme contrainte de conception de premier ordre — une équipe a une capacité cognitive finie, les périmètres de responsabilité doivent y tenir. C'est exactement la thèse de la fenêtre, formulée côté organisation, avec un questionnaire d'auto-évaluation existant. Repris par le Thoughtworks Technology Radar.

## Complément (2026-07-11) — "Ownership coverage" et la matière noire du codebase

Repéré par Kevin sur LinkedIn (post d'Elias Waly Ba, Senior Software Engineer @ OpenFn) :

- **"Matière noire du codebase"** : la part du code maîtrisée par aucun humain de l'organisation. Elle a toujours existé (le script du dev parti, le module legacy contourné) mais grandissait lentement — chaque ligne avait été tapée, donc comprise, au moins une fois par une personne. Avec l'IA, du code compile, passe les tests, tourne en prod sans avoir "jamais traversé un cerveau humain" — la matière noire grandit "de quelques pourcents par sprint".
- **"Ownership coverage"** : pour chaque module, existe-t-il au moins une personne capable de l'expliquer, le modifier en confiance, le débugger sous pression. À suivre avec la même attention que le test coverage — "95 % de test coverage et 40 % d'ownership coverage, ce n'est pas un actif, c'est une dette qui ne dit pas encore son nom".
- Convergence frappante avec le ch. 4 : *"le goulot d'étranglement n'est plus l'écriture, c'est le jugement"* — formulation quasi identique à la thèse production/validation.

**Lecture pour le livre (retournement de l'objection)** : la matière noire n'est dangereuse que dans le périmètre de considération (l'incident à 3h du matin suppose qu'on doive débugger, pas régénérer). La métrique doit donc être lue **par étage** : ownership coverage ~100 % exigé dans le socle — la promotion EST un transfert d'ownership, le modèle mental voyage avec la maintenance — et ~0 % assumé à l'étage utilisateur, où l'on régénère au lieu de débugger. Un ownership coverage indifférencié à 40 % est une dette ; 100 % sur le socle / 0 % assumé sur le jetable est une architecture. À intégrer aux enrichissements des ch. 4 et 11 (métrique de capacité complémentaire de la charge cognitive).

## Proposition d'opérationnalisation pour le livre

La fenêtre de complexité d'une couche (équipe, service, entreprise) peut se mesurer avec trois nombres, tous outillables aujourd'hui :

1. **Consommation d'un cas promu** = son coût de prise en compte : propagation cost (étage 2) pondérée par la fréquence de changement du périmètre qu'il touche (hotspots, étage 4). Un cas isolé et stable consomme presque rien ; un cas couplé à du code chaud consomme beaucoup.
2. **Taille de la fenêtre** = capacité de remédiation disponible : jours-homme de maintenance soutenables par l'équipe (étage 3, unité SQALE), bornée par l'auto-évaluation de charge cognitive (étage 4).
3. **Signal de dépassement** : dette de remédiation du périmètre qui croît plus vite que la capacité, ou charge cognitive auto-évaluée qui décroche — déclencheur des deux leviers (agrandir l'équipe / élaguer).

**Formulation pour le livre** : la fenêtre n'est pas une image — c'est la rencontre de deux littératures établies : la propagation cost (Harvard) pour ce que coûte un cas, la charge cognitive d'équipe (Team Topologies) pour ce que tient une équipe. Le BYOIA n'invente que le lien : en faire le régulateur du cycle de promotion.

## Sources

- [CodeScene — What is Code Health](https://codescene.com/blog/measure-code-health-of-your-codebase) et [Wikipedia — CodeScene](https://en.wikipedia.org/wiki/CodeScene)
- [Tech Lead Journal — Adam Tornhill, Your Code as a Crime Scene](https://techleadjournal.dev/episodes/241/)
- [IT Revolution — Team Cognitive Load](https://itrevolution.com/articles/cognitive-load/)
- [Thoughtworks Radar — Team cognitive load](https://www.thoughtworks.com/en-us/radar/techniques/team-cognitive-load)
- [CISQ — ISO 5055](https://www.it-cisq.org/standards/code-quality-standards/)
- ✓ Références pré-2025 de mémoire (à vérifier au moment de citer précisément) : McCabe 1976 ; Campbell 2018 (Cognitive Complexity, SonarSource) ; Oman & Hagemeister 1992 ; MacCormack, Rusnak & Baldwin (Harvard, DSM/propagation cost) ; Hassan 2009 (entropie des changements) ; méthode SQALE (Letouzey) ; modèle SIG/ISO 25010.
