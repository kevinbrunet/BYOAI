# La préférence révélée : la porte qui se ferme

*Phase 1 — Accroche · Article 1/36 · Publication prévue : mardi 1er septembre 2026*

**Dépend de :** rien, ouverture de la série. Se lit seul.
**Suite :** cette clôture du débat productivité a un enjeu plus grand que la méthode scientifique, elle redessine déjà la carte du pouvoir économique entre entreprises. (Article 2 : *Quand un outil décuple votre capacité, il concentre le marché*)

---

## METR a mesuré un ralentissement de 19 % chez les développeurs assistés par IA. Sa tentative de remesurer cet effet en 2026 a buté sur un problème qu'aucune étude de productivité n'avait rencontré avant.

### L'étude originale (2025) : un ralentissement, pas une accélération

En 2025, METR (Model Evaluation & Threat Research) publie une étude qui va devenir la référence la plus citée du débat sur l'IA et la productivité des développeurs. Le protocole est simple sur le papier : des développeurs open source expérimentés, qui connaissent leurs dépôts depuis des années, chronométrés sur des tâches réelles réparties au hasard entre une condition avec IA et une condition sans IA, rémunérés 150 dollars de l'heure pour participer.

Le résultat surprend tout le monde, y compris les chercheurs. L'usage de l'IA fait durer les tâches 19 % plus longtemps, avec un intervalle de confiance qui va de +2 % à +39 %. C'est un ralentissement, pas un gain. Et avant même de découvrir leur propre chronométrage, ces mêmes développeurs pensaient avoir été environ 20 % plus rapides grâce à l'IA, soit un écart d'une quarantaine de points entre ce qu'ils ressentaient et ce qui s'était réellement passé.

### Comment ce chiffre a été reçu

Le −19 % devient rapidement un point de repère incontournable. On le cite en conférence, dans des notes de cadrage IT, dans des articles qui alertent sur un emballement mal maîtrisé de l'IA en entreprise. Le message qu'on en retient presque partout, c'est que sur du code mûr et partagé, l'IA peut activement nuire à ceux qui l'utilisent sans qu'ils s'en rendent compte, et que les enquêtes déclaratives sur la productivité ne valent pas grand-chose face à une mesure directe.

C'est un point de départ raisonnable. C'est aussi, comme la suite le montre, une lecture qui s'arrête un peu tôt.

### La suite : une deuxième étude, deux résultats très différents

Le 24 février 2026, METR publie une note technique, *We are Changing our Developer Productivity Experiment Design*, qui rend compte d'une deuxième étude lancée dès août 2025 pour suivre l'évolution de cet effet. L'échantillon s'élargit à 57 développeurs : 10 déjà présents dans l'étude 2025, plus 47 nouveaux recrutés sur des dépôts plus divers, répartis sur 143 dépôts pour plus de 800 tâches. Il y a une différence méthodologique notable : cette fois, la rémunération n'est plus que de 50 dollars de l'heure, contre 150 dans l'étude originale.

Les résultats se scindent en deux, selon qui est mesuré. Sur les 10 développeurs revenus de l'étude 2025, le ralentissement mesuré est de −18 %, avec un intervalle de confiance de −38 % à +9 %, ce qui reste très proche du chiffre original. Sur les 47 nouveaux développeurs en revanche, le ralentissement tombe à seulement −4 %, avec un intervalle de confiance de −15 % à +9 %.

Ce deuxième chiffre mérite qu'on s'y arrête, parce qu'il est plus ambigu qu'il n'y paraît. Un intervalle de confiance de −15 % à +9 % ne veut pas dire que l'effet est faible. Il veut dire que l'effet réel pourrait tout aussi bien être un ralentissement presque aussi sévère que l'original, ou au contraire une véritable accélération. Le −4 % n'est pas une mesure précise qui viendrait remplacer le −19 %. C'est le centre d'un nuage d'incertitude si large qu'il est statistiquement indiscernable de zéro, et tout aussi indiscernable d'un vrai ralentissement que d'une vraie accélération.

### Pourquoi la mesure se brouille

METR identifie elle-même la cause de ce brouillage, et ce n'est pas un problème d'échantillon trop petit. C'est un problème de comportement des participants, une fois dans l'étude.

Il y a d'abord un biais sur le choix des tâches. Interrogés, entre 30 % et 50 % des développeurs déclarent avoir volontairement écarté certaines tâches de l'expérience, précisément celles où ils anticipaient le plus grand bénéfice de l'IA, pour ne pas risquer de tomber sur ce type de tâche dans la condition sans IA tirée au sort. L'un des participants résume le mécanisme sans détour : il évite de soumettre les tickets qu'il sait pouvoir boucler avec l'IA en deux heures, contre vingt heures sans, parce que ce serait trop douloureux si le tirage au sort tombait du mauvais côté.

Il y a ensuite un biais sur les développeurs eux-mêmes. Une part croissante d'entre eux ne voulait tout simplement plus faire une partie de leur travail sans IA, même rémunérés pour l'expérience. METR attribue ce comportement surtout à des attentes de plus en plus fortes vis-à-vis de l'IA, tout en reconnaissant que le tarif réduit, 50 dollars contre 150 dans l'étude originale, y a probablement aussi contribué.

Autrement dit, le protocole n'a pas failli parce que des développeurs auraient refusé d'y participer contre rémunération. Il a failli une fois les développeurs dans l'étude, au moment de choisir tâche par tâche ce qu'ils acceptaient d'y exposer.

### Ce que METR en conclut, et ce qu'elle n'affirme pas

Il faut être précis sur ce point : METR ne rétracte pas son étude de 2025. Le chiffre de −19 % reste la mesure valide de ce que l'équipe a observé sur son échantillon initial. Ce qu'elle documente en 2026, c'est que sa propre tentative de suivre l'évolution de cet effet s'est heurtée à un biais structurel, et que ce biais grandit avec l'adoption elle-même : plus l'IA devient utile aux yeux des développeurs, plus ils évitent de s'en priver, y compris dans le cadre d'une étude à laquelle ils ont librement accepté de participer.

METR formule d'ailleurs sa propre conclusion avec prudence. L'équipe juge probable que l'effet réel de l'IA en 2026 soit plus favorable qu'en 2025, mais elle admet que ses données, à cause de ce biais, n'apportent qu'une preuve faible de l'ampleur de cette amélioration.

### La préférence révélée

C'est ce comportement, pas un sondage, pas une déclaration, qui constitue la vraie donnée nouvelle de cette histoire. En économie comportementale, on appelle ça une préférence révélée : ce que les gens font sous contrainte réelle est un signal plus dur que ce qu'ils déclarent. Un développeur qui affirme dans une enquête que l'IA l'aide beaucoup peut se tromper, l'écart de 40 points de l'étude 2025 le montre bien. Un développeur qui, une fois payé pour participer à une étude rigoureuse, écarte discrètement ses tâches les plus favorables à l'IA plutôt que de risquer de les faire sans elle, ne se trompe pas de la même façon. Il révèle par son comportement quelque chose qu'aucun sondage ne peut capter aussi nettement.

Cela ferme une question et en laisse une autre grande ouverte. La question de l'adoption est close : à ce niveau de sélection, on ne peut plus sérieusement débattre de si les développeurs veulent travailler avec l'IA sur ce qui compte pour eux. La question de la validation, elle, devient plus difficile à trancher, précisément parce que l'essai contrôlé randomisé, l'outil de référence pour mesurer un effet causal, perd en fiabilité à mesure que la population volontaire pour la condition sans IA cesse d'être représentative de l'ensemble des développeurs et de l'ensemble des tâches.

### Ce que ça change concrètement

Pour toute organisation qui a cité le −19 % de METR comme argument de prudence, ce livre y compris dans sa première version, la bonne réaction n'est ni d'abandonner le chiffre ni de continuer à le citer sans nuance. C'est de comprendre ce qu'il mesure vraiment aujourd'hui : un effet réel, sur un échantillon donné, à un instant donné d'une adoption encore jeune, et un biais de sélection qui, lui, ne fait que grandir. Un signe que cette adoption devient irréversible plus vite que la méthode scientifique ne peut la mesurer.

La porte qui se ferme n'est pas celle du débat sur la productivité. C'est celle du retour en arrière.

---

## Sources & vérification

*(Article repris en profondeur le 17/07. La première version enchaînait plusieurs corrections partielles qui avaient fini par brouiller l'argument. Cette version reprend l'ensemble depuis la source primaire en une seule fois, et corrige aussi le style, trop marqué "IA" dans les versions précédentes.)*

- METR, *Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity* (arXiv 2507.09089, données fév.-juin 2025) : résultat −19 % (IC +2 %/+39 %), étude rémunérée 150 $/h ✓
- Écart de perception (~20 % de gain ressenti contre −19 % mesuré, environ 40 points d'écart) : repris de l'étude 2025, cohérent avec la note de bas de page déjà vérifiée du chapitre 4 du manuscrit ✓
- METR, *We are Changing our Developer Productivity Experiment Design* (24/02/2026) : deuxième étude (août 2025 et suivants), 57 développeurs (10 revenus de l'étude 2025 + 47 nouveaux), 143 dépôts, 800+ tâches, rémunérée 50 $/h contre 150 $/h dans l'étude originale ✓
- Résultats de la deuxième étude, cités textuellement sur metr.org : développeurs revenus −18 % (IC −38 %/+9 %) ; nouveaux développeurs −4 % (IC −15 %/+9 %, statistiquement indiscernable de zéro) ✓
- Biais de sélection documentés par METR : 30-50 % des développeurs déclarent avoir écarté certaines tâches de l'étude pour ne pas risquer la condition sans IA sur les tâches à fort bénéfice IA anticipé ; part croissante de développeurs réticents à faire une partie de leur travail sans IA du tout. METR attribue ce comportement surtout à la hausse des attentes vis-à-vis de l'IA, avec un effet additionnel probable du tarif réduit ✓
- METR ne rétracte pas l'étude 2025 ; elle qualifie ses propres données 2025-2026 de preuve faible ("weak evidence") de l'ampleur de l'amélioration, tout en jugeant probable un effet réel plus favorable qu'en 2025 ✓
- Cadre théorique de la préférence révélée : terminologie standard d'économie comportementale, rapprochement propre à cette série et non une formulation de METR elle-même. À signaler comme tel si repris tel quel ~
