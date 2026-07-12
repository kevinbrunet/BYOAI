# Questions pour enrichir et consolider — passage au livre

Généré le 2026-07-11. Objectif : transformer l'ontologie actuelle (posts/chapitres) en livre. Les questions marquées 🔴 sont bloquantes pour la crédibilité de la thèse ; les 🟡 structurantes ; les 🟢 éditoriales.

## A. Thèse et positionnement

1. 🔴 Quelle est la thèse en une phrase **falsifiable** ? "L'économie d'échelle sur le code s'effondre" — quelle observation te ferait dire que c'est faux ? Un livre qui ne peut pas être contredit est un manifeste, pas une démonstration.
2. 🔴 Le livre s'adresse à qui, pour lui faire décider quoi ? Le contenu actuel oscille entre plaidoyer économique (DSI/COMEX) et manuel d'architecture (architectes/tech leads). Deux lecteurs, deux livres.
3. ✅ **Répondu (2026-07-11)** : voir [destin du low-code/no-code](../04-objections/destin-low-code-no-code.md) — plafond de contraintes structurel du low-code vs code pur sans plafond, captivité du runtime propriétaire vs code régénérable, délégation au développeur de terrain plutôt que métier-programmeur, et changement réel de l'économie. Résidu : la réponse dépend de la doctrine frontière (Q14).
4. 🟡 Le cluster multi-agents (Condorcet, conseil d'agents, Moussaïd, chef-arbitre) appartient-il à ce livre ? Son lien avec la thèse BYOIA n'est explicité nulle part. C'est potentiellement un second livre caché dans le premier.
5. 🟡 "BYOIA" vs "BYOAI" déjà présent dans la littérature anglophone : néologisme assumé, francisation revendiquée, ou alignement sur le terme existant ?

## B. Preuves et terrain

6. 🔴 Quel matériau terrain existe-t-il ? Un déploiement réel, un pilote, une mission, des interviews ? Le livre n'a actuellement **aucun cas vécu** — que des mécanismes et des analogies. C'est sa plus grande faiblesse.
7. 🔴 L'objection "déplacement du coût vers l'aval" (validation, maintenance, dette) est identifiée mais non tranchée. As-tu des données — même partielles — sur le coût réel de maintenance d'outils générés par IA ? Sans ça, l'argument 1 reste une pétition de principe.
8. 🟡 Dans [chiffres et références manquantes](../05-questions-ouvertes/chiffres-references-manquantes.md) : lesquels sont prioritaires pour le livre, et lesquels peut-on abandonner ?
9. 🟡 Quels sont les contre-exemples assumés — les cas où le générique **reste** supérieur (paie, comptabilité réglementée, ERP core) ? Les nommer renforcerait la thèse au lieu de l'affaiblir.
10. ✅ **Tranché (2026-07-11)** : l'ouverture du livre est le constat de [captivité logicielle](../01-concepts/captivite-logicielle-happy-path-social.md) — pire logiciel = logiciel imposé, recettes de cuisine, happy path sédimenté, résistance rationnelle au changement. Reste optionnel : y adjoindre un échec documenté de Shadow IT + LLM.

## C. Juridique et conformité

11. 🔴 L'argument juridique initial est invalidé ; "conformité par design" est le repositionnement. Mais que reste-t-il de la proposition de valeur si un DPO ou un juriste social dit non ? Le livre a besoin d'un chapitre "comment mener la consultation CSE pour un BYOIA", pas seulement du constat qu'elle est obligatoire.
12. 🔴 Le distinguo filtrage URL / inspection de contenu repose sur une extrapolation marquée ⚠. Prévois-tu une relecture par un avocat en droit social avant publication ? Un livre engage plus qu'un post.
13. 🟡 Périmètre géographique : droit français uniquement ? L'AI Act et le RGPD sont-ils traités, ou explicitement hors périmètre ?

## D. Technique et architecture

14. ✅ **Tranché (2026-07-11)** : le test des cinq questions (partagé ? réglementaire ? auditable ? traçable ? changement d'état ?) — un seul oui → SI, cinq non → interface. Compression : "si quelqu'un d'autre doit pouvoir s'y fier, c'est le SI". Voir [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md). Reste ouvert : l'imposition (gouvernance vs contrainte technique).
15. 🟡 Fiabilité des synchronisations écrites par l'IA : deux options identifiées, aucune retenue. Laquelle ?
16. 🟡 Le livre propose-t-il une architecture de référence nommée et schématisée (facade MCP + gateway + délégation act + traçabilité), ou reste-t-il au niveau des principes ? Entre les deux, le lecteur technique décroche.
17. 🟡 Les outils cités (Bifrost, Kagenti, Presidio…) datent de recherches de mai 2026. Quelle stratégie d'obsolescence — annexe datée, site compagnon, ou principes sans noms de produits ?

## E. Organisation et humain

18. 🔴 Qui arbitre concrètement "règle de gestion vs interface" dans une organisation réelle ? Un rôle, un processus, un comité ? L'objection existe, la réponse organisationnelle n'existe pas.
19. 🟡 Le BYOIA suppose des collaborateurs capables de piloter une "équipe IA personnelle". Quelle proportion des salariés en est réellement capable aujourd'hui, et que fait-on des autres ? Risque de livre pour les 10% déjà convaincus.
20. 🟡 Que devient le développeur d'application dans ce modèle ? Le livre doit-il adresser frontalement la question de l'emploi, ou l'esquiver est-il assumé ?
21. 🟢 Holacratie : parallèle illustratif ou fondement théorique ? Accoler une théorie organisationnelle controversée à la thèse est un risque — préciser le statut du parallèle.

## F. Éditorial

22. 🔴 Les 6 dossiers de l'ontologie ne sont pas un plan de livre. Quel est l'arc narratif — problème → thèse → preuves → objections → méthode ? Un plan chapitré est le prochain livrable logique.
23. 🟡 Posts LinkedIn → chapitres : réécriture complète ou compilation enrichie ? Le ton calibré LinkedIn (court, percutant) ne tient pas 200 pages.
24. 🟡 Le post 1 "happy path" est dit fondateur mais son lien avec BYOIA est ténu. Chapitre d'ouverture, chapitre de méthode, ou hors livre ?
25. 🟢 Titre de travail, langue, canal (éditeur vs auto-édition), longueur cible ?
26. 🟢 Que fait le lecteur en refermant le livre ? Sans méthode actionnable (checklist, canvas, feuille de route 90 jours), c'est un essai ; avec, c'est un ouvrage de référence. Lequel vises-tu ?
