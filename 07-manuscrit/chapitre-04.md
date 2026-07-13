# Chapitre 4 — L'économie du code s'est inversée (mais pas là où on croit)

Tout ce qui précède débouche sur une affirmation économique : produire du logiciel spécifique serait devenu bon marché. Un DSI expérimenté a le droit — le devoir — d'accueillir cette phrase avec méfiance. Il a déjà entendu la promesse. Les ateliers de génie logiciel devaient diviser les coûts ; les CASE tools, les générateurs d'applications, le low-code, le no-code : chaque décennie a juré que le développement allait cesser d'être cher, et chaque décennie a laissé les budgets là où ils étaient. Ce chapitre traite l'affirmation comme elle le mérite : avec des données. Elles existent, elles sont récentes, et elles disent quelque chose de plus intéressant que la promesse des vendeurs — quelque chose qui donne raison au scepticisme ET à la thèse.

## Pourquoi on a uniformisé : un calcul, pas une idéologie

Rappelons d'abord ce que l'uniformisation avait de rationnel, car ce livre ne raconte pas l'histoire d'une erreur — il raconte l'histoire d'un compromis dont les termes viennent de changer.

Une entreprise n'a pas besoin d'outils ; elle a besoin de ce que les outils portent : capitaliser la connaissance, garantir des processus et des réglementations, faciliter l'accès à l'information, conserver une mémoire qui survive à la rotation des personnes. Pour porter tout cela, imposer un outil commun avait trois justifications solides : un référentiel partagé évite la fragmentation de l'information ; une stack maîtrisée est une stack auditable ; et surtout, l'économie d'échelle — mutualiser un développement divise son coût par le nombre d'utilisateurs.

Cette troisième justification était la clé de voûte. Le sur-mesure par poste de travail aurait mieux servi chacun — tout le monde l'a toujours su — mais son coût était absurde : des semaines de développeur pour l'outil d'une seule personne. Alors on a acheté du générique, en connaissance de cause, et on a accepté le prix caché que les chapitres 1 et 2 ont décrit : la couverture du seul nominal, et la colle humaine pour le reste. Le générique n'a jamais été un idéal. C'était un compromis économique — le meilleur possible avec les coûts d'alors.

## Ce qui s'est effondré : le coût de production

Premier fait, désormais solidement établi : générer du code neuf coûte une fraction de ce qu'il coûtait. Les essais contrôlés randomisés — la méthodologie des essais cliniques, appliquée au développement — convergent. L'expérience fondatrice (Peng et al., 2023) : des développeurs assignés aléatoirement avec ou sans assistant d'IA sur une tâche de développement neuve terminent 56 % plus vite avec. L'essai terrain mené par GitHub avec Accenture sur des développeurs en poste retrouve le même ordre de grandeur, jusqu'à 55 % ; une banque australienne mesure 42 % sur six semaines. Trois essais, trois contextes, un ordre de grandeur : sur du code **neuf et isolé**, le gain de vitesse est réel, massif, répliqué[^4-1].

Retenez les deux adjectifs — neufs et isolés — ils vont porter tout le chapitre.

## Ce qui ne s'est pas effondré : tout le reste

Car voici la seconde moitié des données, celle que les vendeurs ne mettent pas dans leurs slides.

En 2025, le laboratoire METR a mené l'essai randomisé le plus rigoureux du domaine, avec un dispositif inhabituel : non pas des tâches d'école, mais 246 tâches réelles sur des dépôts de code mûrs — plus d'un million de lignes — confiées à des développeurs open source expérimentés qui connaissaient ces dépôts. Résultat : avec l'IA, ils ont été 19 % **plus lents**. Le second résultat de l'étude vaut le premier : interrogés après coup, ces mêmes développeurs estimaient que l'IA les avait accélérés de 20 %. L'écart entre la productivité ressentie et la productivité mesurée est de quarante points[^4-2]. Ils ne sentaient pas le ralentissement — ce qui éclaire, au passage, la confiance des enquêtes déclaratives.

À l'échelle des dépôts de code mondiaux, la télémétrie confirme et précise. L'analyse de GitClear sur 211 millions de lignes modifiées entre 2020 et 2024 documente une mutation structurelle : le code dupliqué a été multiplié par quatre à huit ; pour la première fois de leur historique de mesure, le copié-collé dépasse le code déplacé ; la part du refactoring — l'entretien du code existant — s'est effondrée de 25 % des lignes modifiées à moins de 10 % ; et le churn, la part du code réécrit dans les deux semaines suivant son écriture, a presque doublé[^4-3]. L'enquête DORA de Google — la plus large du secteur — résume l'effet système en une phrase devenue célèbre : l'IA n'améliore pas une équipe, elle **amplifie** ce qu'elle est déjà. Le débit de livraison monte ; la stabilité se dégrade ; les équipes dotées de tests automatisés solides et de petits lots absorbent le volume, les autres accumulent l'instabilité[^4-4].

Côté sécurité, les tests systématiques de Veracode sur plus de cent modèles donnent la mesure : environ 45 % du code généré contient des vulnérabilités du top OWASP — près de trois fois le taux du code humain[^4-5]. Et la première étude longitudinale du domaine, qui a suivi dans le temps plus de 300 000 commits identifiés comme écrits par IA, montre que 23 % des problèmes qu'ils introduisent sont toujours présents dans la dernière version des dépôts : la dette générée ne se résorbe pas, elle sédimente[^4-6].

## La variable qui sépare les deux mondes

Posez toutes ces études côte à côte et cherchez la variable qui sépare les résultats positifs des négatifs. Ce n'est pas le modèle d'IA, ni le langage, ni le talent des développeurs. C'est, à chaque fois, la même chose : **le code est-il neuf et isolé, ou partagé et durable ?**

Tâche neuve, périmètre clos, personne d'autre n'en dépend : l'IA est spectaculaire. Code mûr, partagé, chargé d'histoire et de dépendances : l'IA ralentit les experts, duplique au lieu de factoriser, introduit des défauts qui survivent. La conclusion tient en deux phrases, et elle est la clef de tout le livre :

**Le coût de production du code s'est effondré. Le coût de validation et de maintenance, lui, n'a pas bougé — et il domine dès que le code est partagé et durable.**

L'économie du logiciel n'a pas disparu ; elle s'est déplacée de la production vers la validation. Voilà pourquoi le scepticisme du DSI est fondé — si l'on traite le code généré comme du code durable ordinaire, l'objection du "coût déplacé vers l'aval" est exacte, les données ci-dessus le prouvent. Et voilà pourquoi la thèse tient quand même : car rien n'oblige à traiter tout le code de la même façon. Si les déviations du chapitre 2 sont couvertes par du code *neuf, isolé et jetable* — régénéré quand le besoin change plutôt que maintenu —, il vit précisément dans le régime où l'IA excelle. Et si tout ce qui est partagé et durable reste soumis au régime de validation complet, le coût aval est payé exactement là où les données montrent qu'il existe. Toute la question devient : où passe la ligne entre les deux ? Ce sera l'objet du chapitre 6. Ce que les données établissent dès maintenant, c'est que cette ligne n'est pas un caprice d'architecte — elle est dessinée par les mesures.

## Pourquoi le low-code n'a pas tenu cette promesse

Un DSI attentif posera l'objection historique : le low-code et le "citizen developer" promettaient déjà tout cela — le métier produit son outil, l'IT garde la structure — et le bilan est notoirement décevant. Les enquêtes du secteur le chiffrent : une part importante des entreprises équipées n'a jamais réussi à y construire une seule de ses applications à forte valeur[^4-7]. L'outil sert pour le périphérique, jamais pour ce qui compte. Pourquoi cette fois serait-elle différente ?

Parce que le low-code échouait pour une raison structurelle qui ne s'applique pas ici. Le low-code simplifie **en contraignant** : pour rendre le développement accessible, il restreint l'espace de ce qui est exprimable — ses briques, ses connecteurs, ses règles de fonctionnement. Or ces règles ne sont pas vraies partout. Dès que le besoin sort de l'espace prévu — et le chapitre 2 a montré que le besoin réel, ce sont précisément les déviations —, on se heurte au plafond, et il faut contourner l'outil, dans la douleur ou pas du tout. Le low-code échoue en proportion exacte de la spécificité du besoin : il est le pire exactement là où on l'attendait le plus. Ajoutez la captivité — un flux construit dans un atelier propriétaire est illisible hors de l'outil, non portable, non versionnable — et le fait que l'économie de fond n'avait pas changé : le temps de spécialiste restait cher, donc rationné, donc re-priorisé, donc re-uniformisé.

La génération par IA en code pur diffère sur les trois points. L'espace exprimable est le langage de programmation entier — il n'y a pas de plafond au-delà duquel il faudrait "sortir de l'outil", le code pur est déjà dehors. L'artefact produit est du code standard : inspectable, versionnable dans les outils existants, portable, et régénérable même si le générateur disparaît. Et le coût de production a réellement changé — c'était la condition manquante de toutes les promesses précédentes. Méfiez-vous en revanche de l'argument inverse que le marché du low-code sert désormais : "l'IA rend enfin le low-code viable". L'IA qui génère *dans* un atelier contraint hérite du plafond de l'atelier. Le gain de l'IA est maximal en code pur, là où rien ne borne ce qu'elle peut exprimer.

## Les quatre arguments, refondés

On peut maintenant reformuler proprement les quatre arguments économiques du changement de régime, chacun avec sa nuance intégrée — c'est la version qui résiste à un lecteur informé :

L'économie d'échelle sur le code s'effondre — *sur le coût de production*. Mutualiser un développement ne divise plus un coût devenu marginal ; ce qui reste cher est la validation, qui, elle, doit rester mutualisée là où le code est partagé. L'interconnexion cesse d'être le goulot d'étranglement : écrire un connecteur, un adaptateur, une synchronisation est exactement le type de code neuf et isolé où l'IA excelle — la fiabilité de ces synchronisations restant un sujet de validation, pas de production. Nous sommes en phase d'expérimentation, pas de maturité : quand l'essai coûte peu, la stratégie rationnelle est d'essayer beaucoup et de jeter beaucoup — figer des standards maintenant, c'est standardiser l'état de l'art d'une technologie qui a trois ans. Enfin le spécifique redevient supérieur au générique par défaut — non pas partout : là où vivent les déviations, c'est-à-dire, chapitre 2 en main, dans la majorité des situations de travail réelles.

Quatre arguments qui poussent vers la décentralisation. Il en reste un cinquième, qui freine : certaines garanties ne se négocient pas — la cohérence des données, la traçabilité, la conformité. Quatre forces qui poussent, une qui retient : l'équilibre exigera une frontière, et nous y viendrons. Mais ce chapitre laisse d'abord une dette, et elle est en creux dans chacune de ses études : toutes mesurent l'IA-assistant — l'IA génère, l'humain valide, à la main, comme avant. Si le coût de validation domine, la seule stratégie rationnelle est d'industrialiser la validation elle-même. Ce dispositif a un nom — le harnais —, il change l'équation du chapitre entier, et il a ses propres pièges, structurels, documentés. Ce qu'un harnais règle vraiment, et pourquoi aucun n'est parfait : c'est le chapitre suivant.

## Notes et sources

[^4-1]: Gains de vitesse sur code neuf et isolé. ✓ Peng et al., *The Impact of AI on Developer Productivity: Evidence from GitHub Copilot* (arXiv 2302.06590, 2023) : +55,8 % (≈ 56 %), tâche greenfield, bénéfice plus fort pour les moins expérimentés. ✓ GitHub × Accenture (2024) : jusqu'à ~55 %, mesures partiellement déclaratives, co-signé par l'éditeur. ~ ANZ Bank : +42 % sur six semaines (étude interne).

[^4-2]: ✓ METR, *Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity* (arXiv 2507.09089, 2025) : 16 développeurs, 246 tâches réelles sur dépôts mûrs (> 1 M lignes), −19 % de vitesse avec l'IA, alors que la perception post-hoc était de +20 % (écart ≈ 39-40 points). METR qualifie le résultat d'« historique » (outils du début 2025) ; aucun RCT contraire sur code mûr n'a été trouvé.

[^4-3]: ✓ GitClear, *AI Copilot Code Quality* (2025) et *The AI Code Maintainability Gap* (2026) : 211 M de lignes analysées (2020-2024) ; code dupliqué ×4 à ×8 ; copié-collé dépassant le code déplacé pour la première fois ; refactoring de 25 % à moins de 10 % des lignes modifiées ; churn à deux semaines de 3,1 % à 5,7 %.

[^4-4]: ✓ DORA (Google), *State of AI-assisted Software Development 2025* (la plus large enquête du domaine) : débit de livraison en hausse, stabilité en baisse continue ; conclusion textuelle — l'IA « amplifie » ce que l'équipe est déjà.

[^4-5]: ✓ Veracode, *2025 GenAI Code Security Report* (100+ modèles, 4 langages) : ~ 45 % du code généré porte une vulnérabilité du OWASP Top 10 ; ×2,74 vs code humain (« près de trois fois ») ; Java le pire (~72 %). ~ Corroboré par Apiiro (Fortune 50).

[^4-6]: ✓ *Debt Behind the AI Boom* (arXiv 2603.28592) : 302 600 commits identifiés comme écrits par IA, 6 299 dépôts, 5 assistants suivis dans le temps ; 22,7 % des problèmes introduits toujours présents à la dernière révision (« 23 % ») ; type dominant, le *code smell*, invisible en revue.

[^4-7]: ~ « Une part importante des entreprises équipées n'a construit aucune application à forte valeur » : chiffre source rendu qualitatif (≈ 31 %, sondage éditeur, à décoter). Voir la fiche *bilan low-code / citizen developer*. ⚠ Estimations circulantes type « coûts ×4 en année 2 » écartées (blogs vendeurs, méthodologie non publiée).

---

## Notes de rédaction (hors manuscrit)

- Chiffres et statuts, tous détaillés dans [meta-analyse-cout-aval](../06-etat-de-lart/meta-analyse-cout-aval.md) :
  - ✓ Peng et al. 2023 (arXiv 2302.06590) : 55,8 %, arrondi à 56 %. RCT laboratoire.
  - ✓ GitHub × Accenture : "jusqu'à 55 %" — co-écrit vendeur, formulé prudemment. ~ ANZ : 42 %.
  - ✓ METR 2025 (arXiv 2507.09089) : −19 %, perception +20 %. Mention "labellisé historique par METR" omise dans le corps — à mettre en note finale du livre.
  - ✓ GitClear : 211 M lignes, duplication ×4-8, refactoring 25 %→<10 %, churn 3,1→5,7 % (rendu "presque doublé").
  - ✓ DORA 2025 : throughput ↑, stabilité ↓, "amplificateur".
  - ✓ Veracode : ~45 %, ×2,74 (rendu "près de trois fois").
  - ✓ Étude longitudinale arXiv 2603.28592 : 302,6 k commits, 22,7 % (rendu 23 %).
  - ~ "Une part importante des entreprises n'a construit aucune app à forte valeur" : le chiffre source (31 %) est dé-chiffré car sondage vendeur — voir [bilan-low-code](../06-etat-de-lart/bilan-low-code-citizen-developer.md).
- Le mot "citizen developer" apparaît une seule fois, comme étiquette historique — conformément à la décision vocabulaire (terme chargé d'échec).
- L'objection "déplacement du coût vers l'aval" est traitée *dans* le chapitre (section "la variable") plutôt qu'en annexe : décision assumée, c'est l'objection centrale.
- Le régime "jetable/régénéré" est affirmé comme conception, pas comme fait mesuré — la formulation "rien n'oblige à traiter tout le code de la même façon" prépare le ch. 16 (prédiction falsifiable) sans anticiper dessus. Vérifier la cohérence à la rédaction du ch. 16.
- **Restructuration (décision Kevin, 2026-07-12, option B)** : la section "Ce que le harnais change à l'équation" (ajoutée le 2026-07-11) a MIGRÉ au ch. 5 "Aucun harnais n'est parfait", où elle est développée en chapitre complet (anatomie + pièges + décorrélation). Le ch. 4 redevient un pur chapitre de données ; sa chute passe la main au harnais (ch. 5), qui passe la main à la frontière (ch. 6).
- Grille lecteur : DSI (coût réel, scepticisme légitimé puis retourné). Le chapitre donne raison au sceptique avant de le déplacer — même mécanique d'empathie que les ch. 1-2.
- Sources ontologie : [meta-analyse-cout-aval](../06-etat-de-lart/meta-analyse-cout-aval.md), [frontiere-structure-interface](../01-concepts/frontiere-structure-interface.md), [generique-vs-specifique](../01-concepts/generique-vs-specifique.md), [02-arguments 1-4](../02-arguments/), [deplacement-cout-aval](../04-objections/deplacement-cout-aval.md), [destin-low-code](../04-objections/destin-low-code-no-code.md), [bilan-low-code](../06-etat-de-lart/bilan-low-code-citizen-developer.md).
