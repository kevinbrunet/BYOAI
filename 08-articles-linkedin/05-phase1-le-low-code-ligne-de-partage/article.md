# Le low-code n'a jamais été la bonne ligne de partage

*Phase 1 — Accroche · Article 5/38 · Publication prévue : mardi 15 septembre 2026*

**Dépend de :** rien de spécifique, cet article se lit seul. Prolonge, sous un autre angle, le constat de l'article précédent : les catégories qu'on croyait stables (low-code/code pur, pilote/déploiement) ne tiennent plus.
**Suite :** si l'origine de l'outil ne compte plus, ce qui compte est la ligne de production qui l'entoure. Cette ligne a un nom précis, qu'il est temps de définir. (Article 6 : *Le harnais, enfin défini*)

---

## Gartner a inventé la catégorie "low-code". Elle vient de tracer, elle-même, une toute nouvelle ligne. Et cette ligne n'a plus rien à voir avec le low-code.

### Le bilan que tout le monde connaît déjà

Le low-code promettait de rapprocher la production du besoin métier. Un salarié compétent sur son sujet, pas nécessairement développeur, assemble une application avec des blocs visuels plutôt que d'écrire du code ligne à ligne. Le bilan, plusieurs années après l'essor de la catégorie, revient dans presque tout audit IT sous la même forme : les usages se multiplient, la gouvernance ne suit pas.

Une [enquête KPMG](https://kpmg.com/be/en/insights/technology/transforming-business-value-creation-with-citizen-development.html) menée auprès de 715 entreprises en Europe, au Moyen-Orient et en Afrique le documente précisément. 73 % des organisations qui prévoient d'adopter le low-code, et 65 % de celles qui l'utilisent déjà, n'ont toujours pas défini de règles de gouvernance pour l'encadrer. 43 % citent la complexité d'implémentation et de maintenance comme premier obstacle. Le citizen developer devait libérer le métier de sa dépendance à l'IT. Dans les faits, une bonne partie de ce qu'il produit finit orpheline, ou revient un jour sur le bureau d'un développeur qui n'a jamais été consulté sur l'architecture d'origine.

### Le chiffre que tout le monde cite

Gartner a lancé, dès 2021, la prévision la plus reprise du secteur : entre 70 et 75 % des nouvelles applications d'entreprise seraient construites en low-code d'ici 2025-2026, contre moins de 25 % en 2020. Ce chiffre a été répété, arrondi différemment selon les relais, décliné dans pratiquement tous les rapports sectoriels depuis. Il est devenu un totem, la preuve que le low-code avait gagné, indépendamment de ce que révélaient les audits de terrain sur son usage réel.

### Ce que Gartner vient de changer, en silence

Ce qui a bougé en 2026 n'est pas ce chiffre. C'est la définition même de ce qu'il mesure. Le dernier Magic Quadrant pour les plateformes low-code d'entreprise ajoute un nouveau critère d'évaluation, la "capacité IA native", qui pèse à lui seul environ 35 % de la notation. [Gartner définit désormais](https://www.gartner.com/reviews/market/enterprise-low-code-application-platform) une plateforme low-code d'entreprise comme un outil combinant développement piloté par modèles, IA générative et catalogues de composants préconstruits, sur l'ensemble de la pile technologique de l'application. L'IA générative n'est plus une option qu'on coche en marge. Elle fait partie de la définition du produit.

### La vraie ligne que Gartner trace

Et c'est là que la catégorie se retourne contre elle-même. Dans une note intitulée [*Why AI Won't Replace the Need for Low-Code Application Platforms*](https://www.gartner.com/en/documents/7033498), Gartner recommande explicitement aux responsables ingénierie de distinguer une plateforme low-code du "vibe coding", la production de code purement par IA générative, sans les mêmes garde-fous. Cette différence ne porte ni sur le langage, ni sur la part de code écrite à la main, ni sur l'outil d'origine. Elle porte sur la gouvernance : contrôles d'accès, journaux d'audit, cadres de validation qui s'étendent au contenu généré par l'IA. Le vibe coding, dit Gartner, doit rester cantonné à des usages encadrés et supervisés par un développeur, prototypage, code répétitif, outils internes non critiques. Un module low-code produit à 90 % par une IA, mais gouverné, ne relève pas de la même catégorie de risque qu'un script produit en trois minutes par un agent sans aucune revue, même si les deux se ressemblent ligne à ligne.

### Ce que ça change concrètement

L'organisme qui a inventé la catégorie "low-code" vient, de fait, d'admettre que cette catégorie n'a jamais été la bonne ligne de partage. Ce n'était pas outil visuel contre code écrit, ni low-code contre IA générative. C'était, depuis le début, gouverné contre non gouverné, prouvé contre non prouvé. Un script généré par IA sans traçabilité et un module low-code déployé sans piste d'audit appartiennent à la même catégorie de risque, quel que soit l'outil qui les a produits. Un module produit par IA, testé, tracé, revu, appartient à une tout autre catégorie, quand bien même il ressemblerait, ligne à ligne, à n'importe quel autre code.

Le bon critère n'a donc jamais été l'outil de fabrication. C'est le degré de rigueur atteint et prouvé autour de ce qui est produit, sur une échelle qui n'a pas encore de nom précis dans cette série. Elle en aura un très bientôt.

---

## Sources & vérification

*(Article produit le 19/07. Recherche menée pour vérifier la statistique Gartner esquissée au fichier maître, marquée ~ à l'origine. Correction de fond : le fichier maître affirmait que "le marché a dissous statistiquement la frontière entre low-code et code généré par IA" et que "Gartner range désormais le développement assisté par IA dans ses stats low-code/no-code". Cette formulation précise n'a pas pu être vérifiée : aucune source trouvée ne confirme que l'IA générative pure est comptée dans le chiffre "70-75 % des nouvelles applications". En revanche, la recherche a mis au jour un fait mieux sourcé et plus fort pour l'argument du livre : le Magic Quadrant 2026 de Gartner pour les LCAP ajoute un critère "capacité IA native" pesant ~35 % de la notation, et Gartner distingue explicitement les plateformes low-code gouvernées du "vibe coding" non gouverné, sur un critère de gouvernance et non d'origine de l'outil. L'article a été réécrit autour de ce fait, qui sert directement la thèse "le bon critère n'est pas l'outil, c'est la rigueur prouvée" sans avoir besoin de la statistique non vérifiable. Toutes les sources Gartner ci-dessous proviennent de synthèses secondaires cohérentes entre elles (Gartner Peer Insights, blogs spécialisés citant les documents Gartner), pas d'une lecture directe des rapports Gartner primaires, qui sont payants. À revérifier contre le texte primaire avant publication si l'accès est possible.)*

- KPMG, enquête auprès de 715 entreprises EMEA sur le citizen development : 73 % des futurs adoptants et 65 % des utilisateurs actuels sans règles de gouvernance définies, 43 % citent la complexité d'implémentation/maintenance comme premier obstacle ✓ (lu directement sur la page KPMG) — https://kpmg.com/be/en/insights/technology/transforming-business-value-creation-with-citizen-development.html
- Gartner, prévision originale du Magic Quadrant 2021 pour les Enterprise Low-Code Application Platforms : 70-75 % des nouvelles applications d'entreprise en low-code/no-code d'ici 2025-2026, contre moins de 25 % en 2020 ~ (chiffre et année varient selon les relais secondaires consultés, pas de lecture directe du Magic Quadrant primaire)
- Gartner, Magic Quadrant 2026 pour les Enterprise LCAP : nouveau critère d'évaluation "capacité IA native" pesant environ 35 % de la notation ~ (relayé de façon cohérente par plusieurs synthèses spécialisées, non vérifié contre le rapport primaire payant) — https://www.gartner.com/reviews/market/enterprise-low-code-application-platform
- Gartner, définition des Enterprise LCAP incluant développement piloté par modèles, IA générative et catalogues de composants préconstruits ~ (même réserve) — https://www.gartner.com/reviews/market/enterprise-low-code-application-platform
- Gartner, *Why AI Won't Replace the Need for Low-Code Application Platforms* : distinction explicite entre LCAP gouvernées (contrôles d'accès, audit, validation) et "vibe coding" à cantonner aux usages supervisés, prototypage, outils non critiques ~ (relayé par plusieurs synthèses cohérentes entre elles, document Gartner primaire payant non consulté directement) — https://www.gartner.com/en/documents/7033498
