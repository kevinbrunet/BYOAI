# Responsabilité du pilote et diversité des harnais

Deux principes formulés par Kevin (2026-07-11), développés dans [le chapitre 5 — Aucun harnais n'est parfait](../07-manuscrit/chapitre-05.md).

## 1. La responsabilité reste associée à celui qui pilote le harnais

Le harnais automatise l'exécution de la validation, pas le jugement — donc la responsabilité ne se transfère pas à l'outillage. Celui qui pilote le harnais répond de ce qui en sort. Conséquences en chaîne :

- **Cohérence avec la délégation (ch. 7)** : la chaîne `act` remonte toujours à une origine humaine — le pilote. Techniquement, la responsabilité est déjà câblée : chaque action porte le nom de celui pour le compte de qui elle a été faite.
- **Cohérence avec le régime humain-only (ch. 8)** : le rubber-stamping cesse d'être un simple risque résiduel — si la responsabilité est explicitement au pilote, cliquer "OK" sans regarder n'est pas un contournement du système, c'est une faute *du pilote*, traçable comme telle. Le cadre de responsabilité est la réponse organisationnelle au trou que le verrou technique ne peut pas fermer.
- **Cohérence avec le cycle de promotion** : au niveau utilisateur, le pilote répond de son outil (il peut casser demain — c'est son problème) ; la promotion transfère la maintenance ET déplace la responsabilité vers la couche qui accepte l'outil. Responsabilité et maintenance voyagent ensemble — jamais l'une sans l'autre.
- **Cohérence avec l'AI Act (ch. 13)** : la supervision humaine exigée par l'art. 26 suppose un humain identifiable qui supervise. Le pilote du harnais est cet humain — le modèle donne un nom à ce que le règlement exige.

Formulation candidate pour le livre : *le harnais est un outillage, pas un alibi.*

## 2. Aucun harnais n'est magique — la diversité comme défense contre les angles morts

Aucun harnais ne teste ce que son concepteur n'a pas imaginé ; aucune IA ne détecte les erreurs situées dans ses propres angles morts. Un harnais parfait est une contradiction dans les termes — c'est le [happy path](./happy-path-illusion-statistique.md) appliqué à la validation elle-même : le harnais couvre les déviations *prévues*.

La défense n'est pas un meilleur harnais unique — c'est la **diversité** des harnais et des IA :

- Deux IA différentes (modèles, entraînements, prompts différents) ont des angles morts **décorrélés** : l'erreur que l'une laisse passer, l'autre a une chance de la voir. C'est la condition de validité de la sagesse des foules (Condorcet) : l'agrégation n'aide que si les biais sont indépendants — des IA identiques votent identiquement, y compris dans l'erreur.
- Le BYOIA produit cette diversité **par construction** : chaque collaborateur son harnais, ses modèles, sa configuration. Là où l'outil béni unique (stratégie 4 du marché, ch. 3) installe une **monoculture** — un seul angle mort, partagé par toute l'entreprise, invisible par définition — la diversité des harnais décorrèle les défaillances. Une erreur systématique du modèle X frappe les utilisateurs de X, pas l'entreprise entière ; et les utilisateurs de Y la voient passer.
- L'argument retourne l'accusation classique : "la diversité des outils, c'est le chaos" devient "la monoculture des outils, c'est le risque systémique". L'analogie est écologique/agricole — une monoculture est efficace et fragile ; un écosystème divers est redondant et résilient. Même argument que la diversification en finance : on ne diversifie pas parce que chaque actif est meilleur, mais parce que leurs risques sont décorrélés.
- **Prolongement (2026-07-15)** : la métaphore de la selle donne à la diversité son fondement positif (pas de selle idéale → la pluralité est une conséquence de l'ajustement, pas un chaos toléré) et sa réponse organisationnelle (le harnais d'équipe garant de la cohésion) — voir [selle-personnelle-harnais-equipe](./selle-personnelle-harnais-equipe.md).
- **Instrumentation** : la diversité ne détecte les angles morts que si on regarde les désaccords. Le désaccord entre deux harnais/IA sur le même objet est un signal (pas un correcteur) : il indique où chercher — voir [taxonomie des angles morts](./taxonomie-angles-morts-empirique.md) (divergence rétrospective, désaccord inter-modèles comme détecteur) et [l'épidémiologiste](./epidemiologiste-du-backlog.md), qui collecte ces signaux à l'échelle.

## Statut vis-à-vis du cluster multi-agents (hors livre)

Ce concept réintègre dans le livre la **partie applicable** du cluster multi-agents sorti du périmètre : la condition de décorrélation (Condorcet) et le désaccord-comme-détecteur. Le reste du cluster (conseil d'agents, pondération bayésienne, chef-arbitre, Moussaïd) reste hors livre. La littérature 2025-2026 confirme les deux points réintégrés (voir [multi-agents-agregation](../06-etat-de-lart/multi-agents-agregation.md) : le vote majoritaire échoue quand les agents partagent les mêmes biais ; la sycophancie des consensus).

## Place dans le livre (mise à jour 2026-07-12, renumérotation option B)

- Ch. 5 (Aucun harnais n'est parfait) : développement complet de la mécanique — responsabilité au pilote, juge et partie, boucle saturée, Goodhart, tests du même cerveau, dégradation du contexte, décorrélation comme parade, désaccord-détecteur au niveau de la ligne de production (fait, 2026-07-12).
- Ch. 13 (métier augmenté) : la conséquence organisationnelle — monoculture/défense de population, l'argument contre l'outil béni unique, la carte des angles morts à l'échelle (retouché pour renvoyer au ch. 5 sans redite).
- Ch. 16 : prédiction falsifiable n° 3 — les organisations à harnais divers détectent plus d'anomalies que les monocultures (mesurable par le taux de désaccords exploités).
