# Série LinkedIn — 10 posts, du BYOAI à l'assemblage final

Arc narratif (2026-07-11, accroches durcies) : le phénomène → la réglementation → l'impact sur l'informatique de gestion → les exemples en place → la généralisation → l'assemblage. Chaque post tient seul ; l'ensemble déroule la thèse du livre.

**Mécanique de série** : chaque post se termine par une boucle ouverte vers le suivant (la question que le post pose sans y répondre). Un nom de série affiché dès le post 1 — proposition : **« SI ouvert »** ou simplement **#BYOIA** — pour que suivre la série soit un geste identifiable.

## 1. Vous avez bloqué ChatGPT. Ils ont sorti leur téléphone.

**Accroche :** ~ 78 % des utilisateurs d'IA apportent leurs propres outils au travail. Pas les stagiaires : vos meilleurs éléments. Le Shadow AI n'est pas une fuite dans votre dispositif de sécurité — c'est votre dispositif de sécurité qui le fabrique.
**Contenu :** les chiffres du phénomène, l'échec documenté de l'interdiction (comptes perso, extensions, IA embarquée dans les SaaS déjà autorisés).
**Boucle ouverte :** pourquoi vos salariés les plus sérieux trichent-ils ? Réponse au prochain post — et elle ne va pas vous plaire.
**Source :** [byoai-shadow-ai-marche](../06-etat-de-lart/byoai-shadow-ai-marche.md).

## 2. Le logiciel le plus détesté au monde n'est pas mal codé. Il est obligatoire.

**Accroche :** faites le test : citez le pire logiciel que vous utilisez. C'est un logiciel d'entreprise, à tous les coups. Pas parce que les éditeurs B2B sont nuls — parce que vous ne pouvez pas partir.
**Contenu :** captivité (ni exit, ni voice → contournement), les recettes de cuisine à la machine à café, le happy path qu'on découvre par essais/erreurs, la résistance au changement comme calcul rationnel. Chute : le BYOAI est la recette de cuisine qui a trouvé un moteur. Vos salariés ne trahissent pas votre SI — ils le complètent, comme ils l'ont toujours fait.
**Boucle ouverte :** le marché a flairé le problème. Six familles de solutions. Devinez combien traitent la cause.
**Source :** [captivite-logicielle](../01-concepts/captivite-logicielle-happy-path-social.md) — teste l'ouverture du livre en conditions réelles.

## 3. Six solutions contre le Shadow AI. Zéro s'attaque à la cause.

**Accroche :** j'ai cartographié tout ce que le marché vous vend contre le BYOAI. Interdire, surveiller, canaliser, fournir, enfermer, certifier. Six réponses, des milliards de dollars — et une case vide au milieu.
**Contenu :** le tour des six stratégies avec leur faille chacune (une ligne par stratégie, format qui se partage bien). La case vide : personne ne repense ce que votre SI expose et garantit. On vous équipe contre vos salariés ; personne ne vous équipe pour eux.
**Boucle ouverte :** et pendant que le marché vous vend des pare-feux, les juges, eux, ont commencé à écrire. Prochain post : ce que dit vraiment la jurisprudence.
**Source :** [byoai-solutions-existantes](../06-etat-de-lart/byoai-solutions-existantes.md).

## 4. « On n'a rien déployé » n'est plus une défense. Un juge l'a écrit.

**Accroche :** ~ Nanterre, janvier 2026 : déploiement IA suspendu. ~ Paris, mai 2026 : *mettre à disposition*, c'est déployer. Et non, "c'était juste une expérimentation" ne marche pas non plus — c'est écrit aussi.
**Contenu :** les trois décisions, ce qu'elles impliquent : la consultation CSE n'est pas contournable, même en fournissant "juste des connecteurs". Le retournement : arrêter de chercher l'échappatoire, construire le dossier qui gagne la consultation.
**Boucle ouverte :** et ce n'est que le droit français. L'Europe arrive avec un texte qui contient un piège que presque tout le monde lit de travers.
**Source :** [jurisprudence-cse-ia-2026](../06-etat-de-lart/jurisprudence-cse-ia-2026.md). ⚠ Références à vérifier avant publication.

## 5. Votre assistant IA est légal à 10h. Le même est à haut risque à 15h.

**Accroche :** l'AI Act ne classe pas vos outils. Il classe vos usages. Le matin, votre RH lui fait résumer 40 candidatures : risque minimal. L'après-midi, il lui fait rejeter les 20 derniers du classement : haut risque, logs 6 mois, supervision humaine obligatoire, jusqu'à 7 % du CA mondial.
**Contenu :** la pyramide de risques, l'emploi en annexe III, les obligations du déployeur, le report omnibus à déc. 2027. La lecture stratégique : 17 mois pour construire l'architecture qui rend ces obligations triviales — ou pour les subir.
**Boucle ouverte :** mais comment savoir, concrètement, ce qui doit passer sous contrôle et ce qui peut rester libre ? Il existe un test. Cinq questions. Prochain post.
**Source :** [eu-ai-act](../06-etat-de-lart/eu-ai-act.md).

## 6. Cinq questions décident de tout votre SI. Les voici.

**Accroche :** partagé ? réglementaire ? auditable ? traçable ? changement d'état ? Un seul oui → ça appartient au SI. Cinq non → ça appartient au salarié. C'est tout. Vous pouvez trier l'intégralité de votre informatique de gestion avec ça, lundi matin.
**Contenu :** le test appliqué au cas RH (préparer = libre, acter = SI), la compression ("si quelqu'un d'autre doit pouvoir s'y fier, c'est le SI"), et le précédent qui prouve que c'est tenable : le mandat Bezos de 2002 — tout par l'API, zéro porte dérobée, licenciement à la clé. Sous-produit : AWS.
**Boucle ouverte :** ce test a un talon d'Achille — que se passe-t-il quand c'est l'IA elle-même qui appelle l'API ? Il manque un verrou. Le prochain post est celui que les architectes sécurité vont s'envoyer entre eux.
**Sources :** [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md), [amazon-mandat-api](../03-exemples/amazon-mandat-api.md).

## 7. Il faut des API interdites à l'IA. Oui, interdites.

**Accroche :** tout le monde se demande ce que l'IA a le droit de lire. Mauvaise question. La bonne : qu'a-t-elle le droit d'ACTER ? Rejeter un candidat, valider un licenciement, notifier un client — il y a des endpoints où la réponse doit être : jamais. Même avec une délégation parfaitement valide.
**Contenu :** typage humain/agent dans la chaîne de délégation, trois régimes par endpoint, "l'IA prépare, l'humain acte" rendu exécutoire par l'API — plus un slogan de gouvernance, un refus technique. Bonus : la supervision humaine de l'AI Act devient prouvable par les logs. Limites assumées : rubber-stamping, prouver l'humain (un agent sait cliquer).
**Boucle ouverte :** "OK sur le papier. Qui a fait tourner un truc pareil en vrai, à grande échelle ?" Réponse : une major pétrolière, un éditeur de Redmond, et un fabricant de frigos chinois. Vraiment.
**Source :** [delegation-agents-jwt-mtls](../01-concepts/delegation-agents-jwt-mtls.md) + [backlog](./backlog-posts.md).

## 8. Shell laisse 4 000 salariés fabriquer leurs outils. Leur DSI dort très bien.

**Accroche :** pendant que vos comités débattent d'autoriser Copilot, Shell a industrialisé le bricolage : trois zones (libre / accompagné / interdit), des coaches développeurs au milieu des équipes métier. Microsoft a fait pareil en interne. Haier l'a fait avec l'organisation entière.
**Contenu :** Shell DIY, les environnements par étages de Microsoft (et la leçon du default environment qui pourrit — un bac à sable sans ménage devient une décharge), Haier en preuve organisationnelle. Puis le retournement : ces méthodes marchent MAIS enferment dans une plateforme et ne savent pas jeter. L'IA en code pur lève exactement ces deux limites.
**Boucle ouverte :** reste LA question que tout DSI pose : "et la maintenance de ces centaines de petits outils ?" Le prochain post renverse 20 ans de doctrine dessus.
**Sources :** [methodologies-grandes-entreprises](../06-etat-de-lart/methodologies-grandes-entreprises.md), [haier-rendanheyi](../03-exemples/haier-rendanheyi.md).

## 9. Arrêtez de standardiser vos outils. Laissez les survivants monter.

**Accroche :** on uniformise depuis 20 ans a priori : comités, spécifications, consensus mou — puis plus personne n'utilise l'outil. Inversez : laissez proliférer en bas, mesurez l'usage, promouvez ce qui survit. Le générique de demain, c'est le spécifique qui a fait ses preuves.
**Contenu :** le cycle de promotion (utilisateur → équipe → service → entreprise), la maintenance transférée à chaque étage, les métriques qui dépolitisent la montée ET la descente, la fenêtre de complexité (deux leviers seulement : agrandir l'équipe ou élaguer). L'asymétrie nouvelle : jeter est enfin bon marché — la rigidification n'est plus une fatalité, c'est un choix.
**Boucle ouverte :** phénomène, droit, frontière, verrou, preuves, méthode. Il ne reste qu'à assembler. Dernier post de la série — et une annonce.
**Source :** [cycle-promotion-specifique](../01-concepts/cycle-promotion-specifique.md).

## 10. Le BYOAI est ce qui vous arrive. Le BYOIA est ce que vous en faites.

**Accroche :** deux lettres inversées, deux mondes. BYOAI : vos salariés apportent leur IA, vous subissez. BYOIA : votre SI est architecturé pour l'accueillir — API typées humain/agent, frontière en cinq questions, cycle de promotion, conformité CSE et AI Act fabriquée par construction, pas déclarée.
**Contenu :** l'assemblage en une image (le schéma complet — le visuel le plus partageable de la série), la filiation assumée (le versant organisationnel du malleable software de Litt/Ink & Switch), et l'annonce du livre. CTA explicite : "le livre développe chaque brique — abonnez-vous / lien".
**Sources :** [byoia](../01-concepts/byoia.md), [positionnement-malleable-software](../01-concepts/positionnement-malleable-software.md).

## Notes de série

- **Règle marketing constante** : une affirmation contre-intuitive dans la première ligne (avant le "voir plus"), des phrases courtes, une chute, une boucle ouverte. Jamais d'accroche descriptive ("état de l'art de…" est un titre de rapport, pas de post).
- Les posts 4, 5 et 7 portent des références réglementaires/jurisprudentielles : vérification (Légifrance, texte consolidé) avant publication — règle ✓/~/⚠.
- Le post 2 teste l'ouverture du livre en conditions réelles ; mesurer sa performance avant de figer le chapitre 1.
- Cadence : 1/semaine, 10 semaines — atterrissage dans la fenêtre AI Act et avant les budgets 2027.
