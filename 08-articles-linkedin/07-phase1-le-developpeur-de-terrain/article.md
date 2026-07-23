# Le développeur de terrain

*Phase 1 — Accroche · Article 7/38 · Publication prévue : mardi 22 septembre 2026*

**Dépend de :** le harnais, enfin défini (art. 6) — reste à savoir qui le pilote, au quotidien, pour produire ce dont une équipe métier a besoin.
**Suite :** le harnais que le développeur de terrain pilote ne se contente pas de produire. Il peut aussi transmettre, à condition d'être construit pour ça. (Article 8 : *Le harnais comme passage de connaissance*)

---

## Shell visait cinq cents développeurs maison. Ils sont aujourd'hui plus de quatre mille. Le nombre n'est pas ce qu'il y a de plus intéressant. C'est ce qu'ils avaient le droit de construire, et sa limite, qui vient de changer.

### Le réflexe qu'on connaît tous

Depuis que l'IA générative écrit du code, une inquiétude revient dans presque toute conversation sur le sujet : le pipeline junior va-t-il s'effondrer, les développeurs vont-ils tout simplement disparaître ? Une note de la [Direction générale du Trésor](https://www.tresor.economie.gouv.fr/Articles/2026/06/30/l-intelligence-artificielle-quels-effets-sur-l-emploi) publiée fin juin 2026 confirme que l'inquiétude n'est pas fantasmée. L'insertion professionnelle des jeunes ralentit, et l'informatique fait partie, avec la finance, des secteurs les plus exposés aux premières vagues de suppressions de postes attribuées à l'IA.

### Ce que Shell a déjà prouvé, avant l'IA générative

Il y a environ quatre ans, Shell a lancé un programme baptisé DIY, "Do It Yourself", pour donner à des salariés sans expérience de développement les moyens de construire eux-mêmes leurs outils avec Power Platform. L'objectif de départ était de cinq cents développeurs internes. Le résultat dépasse aujourd'hui les quatre mille, documenté à la fois par [Microsoft](https://www.microsoft.com/en/customers/story/1699045592642116808-shell-energy-power-platform-uk) et par [Forrester](https://www.forrester.com/report/case-study-shells-diy-citizen-developer-program/RES178358). Le programme tient sur trois zones de gouvernance. En zone verte, l'application reste entièrement sous la responsabilité de qui l'a créée. En zone orange, un coach dédié encadre le projet. En zone rouge, réservée aux projets les plus risqués, seule l'IT centrale intervient. Un centre d'expertise dédié pilote l'ensemble, avec un vice-président nommé pour ça et l'aval direct du CIO.

### Ce qui change, ce n'est pas le modèle, c'est le plafond

L'article 5 de cette série l'a montré : le low-code échoue par un plafond d'expressivité structurel, pas par degré. Le programme de Shell fonctionne depuis quatre ans, mais il reste, pour l'essentiel, plafonné par ce que des blocs visuels permettent de construire. Ce que l'IA générative de code change n'est pas ce modèle organisationnel, zoné, coaché, gouverné. C'est ce qu'un salarié en zone verte a le droit de construire avec. Le harnais défini dans l'article précédent, tests générés, analyse statique, revue, boucle de correction, est ce qui permet de faire sauter ce plafond sans perdre la gouvernance qui a fait tenir le programme de Shell pendant quatre ans.

### Le développeur de terrain, ni citizen developer, ni DSI centralisée

Cette figure n'est ni le citizen developer du low-code, qui rapproche un salarié métier de la production en le formant à des blocs visuels, ni le développeur d'une DSI centralisée, qui reste à distance du besoin réel et hérite d'un ticket déjà froid. Le développeur de terrain est un professionnel intégré à l'équipe métier, qui pilote un harnais plutôt qu'un éditeur visuel, et qui transforme la recette de cuisine échangée à la machine à café en outil produit le jour même, sous la même logique de zones que Shell applique depuis quatre ans, mais sans le plafond du low-code.

### Ce que ça change concrètement

Le problème du pipeline junior, documenté par le Trésor, reste réel. L'IA automatise en premier les tâches codifiées, celles qu'on confiait justement aux débutants pour qu'ils apprennent. Mais le modèle de Shell suggère une réponse organisationnelle, pas seulement individuelle. Un junior qui pilote un harnais sous supervision, en zone orange, avec un coach dédié, apprend en produisant sur de vrais besoins métier, pas en attendant qu'un senior ait le temps de relire un exercice. Reste à savoir si ce mode de formation produit des seniors aussi solides que l'ancien modèle. C'est une question ouverte, pas encore tranchée par cette série.

---

## Sources & vérification

*(Article produit le 19/07. Recherche menée pour vérifier les deux sources marquées ~ et ⚠ au fichier maître. Le chiffre Shell est confirmé avec précision : l'objectif de départ était bien de 500 développeurs, dépassé aujourd'hui par plus de 4 000, citation directe trouvée via la page Microsoft Customer Stories, structure de gouvernance à trois zones confirmée par Forrester. La note Trésor-Éco n° 391 (30/06/2026) est authentique et consultée directement sur tresor.economie.gouv.fr : elle confirme un ralentissement de l'insertion professionnelle des jeunes et cite l'informatique parmi les secteurs les plus exposés aux premières suppressions de postes attribuées à l'IA. Un chiffre plus précis, trouvé uniquement via une synthèse tierce et non confirmé dans le corps de la note consultée directement, affirmait une contraction spécifique de l'emploi des 15-29 ans dans l'informatique compensant la progression des autres tranches d'âge : ce chiffre n'a pas été repris dans l'article faute de confirmation directe dans le texte source, à vérifier dans le PDF complet de la note avant toute citation plus précise.)*

- Direction générale du Trésor, *L'intelligence artificielle, quels effets sur l'emploi ?*, Trésor-Éco n° 391 (30 juin 2026), M. Chopard, E. Cotet, T. Gantois, E. Villani ✓ (consulté directement) — https://www.tresor.economie.gouv.fr/Articles/2026/06/30/l-intelligence-artificielle-quels-effets-sur-l-emploi
- Contraction spécifique de l'emploi 15-29 ans dans l'informatique compensant la progression des autres tranches d'âge ~ (relayé par une synthèse tierce, non confirmé dans le corps de la note consultée directement, non repris dans le texte publié)
- Shell, programme *DIY* : objectif initial de 500 développeurs internes, plus de 4 000 aujourd'hui, gouvernance à trois zones (verte/orange/rouge), centre d'expertise dédié ✓ — https://www.microsoft.com/en/customers/story/1699045592642116808-shell-energy-power-platform-uk
- Forrester, étude de cas sur le programme DIY de Shell ✓ (titre et existence confirmés, contenu complet non consulté au-delà du résumé) — https://www.forrester.com/report/case-study-shells-diy-citizen-developer-program/RES178358
