# Chapitre 11 — Le cycle de promotion

Projetons-nous six mois après le déploiement de l'architecture des chapitres précédents. Le socle expose ses API, les harnais produisent, les verrous tiennent. Et l'entreprise compte maintenant quelques centaines d'outils spécifiques : le tableau de suivi de la gestionnaire RH, le croiseur d'extractions du contrôleur de gestion, les scripts du technicien de maintenance. C'est le succès du modèle — et c'est le cauchemar annoncé de tout DSI qui lit ce livre : des centaines d'outils, qui les connaît, qui les maintient, qui les éteint ? La réponse tient en un mot que l'informatique d'entreprise n'applique jamais à ses outils : un **cycle de vie**. Pas un inventaire, pas un comité — un chemin, avec des étages, des règles de passage, et un sens de circulation dans les deux directions.

Que ce chemin manque partout, les chiffres le disent : l'enquête française du chapitre 3 montre une adoption de l'IA bloquée à l'étage pilote — un tiers des entreprises encore en exploration, une sur six seulement avec des cas d'usage déployés à l'échelle. Le fameux "passage à l'échelle", dont toutes les directions parlent, n'est pas un problème de technologie : c'est un problème de trajet. Il n'existe, dans la plupart des organisations, aucun chemin outillé entre le pilote qui marche et l'outil industrialisé — on saute, ou on reste en bas. Ce chapitre construit le trajet.

## Quatre étages, quatre contrats

Le spécifique n'a pas vocation à rester isolé — ni à être promu d'office. Il naît en bas et monte s'il le mérite :

**L'étage utilisateur.** L'outil appartient à celui qui l'a fait faire. Il peut casser demain — c'est son problème, et c'est un problème minuscule : l'outil se régénère. Personne d'autre ne s'en sert, personne d'autre n'a besoin de le savoir ; tant qu'il respecte la frontière — il ne fait que consommer les API, préparer, projeter —, il n'existe pour personne.

**L'étage équipe.** L'outil a fait ses preuves ; des collègues le veulent. Sa maintenance se **mutualise** : l'équipe le connaît, et l'on fait désormais attention à lui lors des changements internes.

**L'étage service.** L'outil devient un cas pris en compte : celui qui modifie un référentiel ou une API du périmètre doit le considérer.

**L'étage entreprise.** L'outil s'intègre à l'API commune, avec le contrat le plus exigeant : non-régression, rétro-compatibilité, traçabilité pleine.

Voyez ce qui monte avec l'outil : à chaque étage, **la maintenance est transférée** — de l'individu à l'équipe, de l'équipe au service, du service à l'entreprise — et le **contrat de stabilité** se durcit. C'est le premier point que le sceptique doit entendre : le modèle ne demande à personne de maintenir des centaines d'outils. L'immense majorité vit et meurt à l'étage utilisateur, où sa maintenance est : le régénérer. Seul ce qui prouve sa valeur monte, et seul ce qui monte coûte.

Et nommons ce que la promotion achète réellement, car c'est plus subtil qu'un transfert de charge : elle achète une place dans le **périmètre de considération des changements**. Un outil d'étage utilisateur n'existe pas aux yeux de celui qui modifie le SI — s'il casse, il régénère. Un outil d'étage service, si : chaque évolution du périmètre doit le prendre en compte. C'est exactement la définition de la fiabilité du point de vue d'autrui — et c'est pour cela que la promotion coûte.

## L'uniformisation, remise dans le bon sens

Prenez du recul sur ce mécanisme, et vous verrez qu'il inverse vingt ans de doctrine. L'uniformisation classique procède **a priori** : un comité, un recueil de besoins, une spécification de consensus, un déploiement — puis la découverte que l'outil uniforme ne convient vraiment à personne, chapitre 1. Le cycle procède **a posteriori** : on laisse proliférer en bas, on observe, et l'on promeut ce qui a survécu à l'épreuve de l'usage réel. La sélection remplace la conception par comité. Le générique de demain est le spécifique qui a survécu.

Ce qui déclenche la montée n'est pas un jugement — c'est une **mesure**. Chaque outil qui monte d'un étage est instrumenté : qui l'utilise, à quelle fréquence, sur quels cas. Usage convergent — trois équipes se sont fabriqué la même chose, douze tickets tournent autour du même trou — : candidat à la promotion. Usage effondré : candidat à la descente. Le point politique mérite une phrase, car quiconque a vécu une décommission d'application sait qu'elle est un acte de guerre : ici, **on ne retire pas l'outil de quelqu'un — on acte une mesure**. La métrique dépolitise la montée comme la descente.

Et l'adoption reste un choix. C'est le second point que le sceptique doit entendre, car il y verra une contradiction : à quoi bon promouvoir si personne n'est obligé d'utiliser l'outil promu ? Le modèle répond : l'outil promu est une **offre**, jamais une obligation. Le salarié qui préfère forker — faire diverger sa version, ou garder la sienne — le peut, tant qu'il passe par les chemins d'accès autorisés ; ce que l'entreprise contraint, ce ne sont pas les outils, ce sont les accès aux données, chapitres 6 et 9 — et c'est là que vivent la sécurité et la conformité, pas dans l'uniformité des outils. Mais celui qui forke récupère sa liberté *avec* sa maintenance : sa version peut casser demain, personne ne la protège. L'outil promu gagne parce qu'il est **moins cher à posséder** — protégé lors des changements, maintenu par d'autres —, pas parce qu'il est imposé. Toute la littérature du platform engineering converge sur ce point : la plateforme choisie bat la plateforme décrétée. Et le fork cesse d'être une dissidence pour devenir un capteur : si beaucoup forkent le même outil promu de la même façon, ce n'est pas de l'indiscipline — c'est la mesure qui dit que l'outil ne couvre plus le besoin.

## La descente est une opération de premier ordre

Voici maintenant la moitié du cycle dont personne ne parle, et qui est peut-être la contribution la plus importante de ce chapitre.

Chaque cas pris en compte complexifie le changement. Plus le périmètre de considération grossit, plus chaque évolution coûte — c'est très exactement le mécanisme qui a rigidifié les SI historiques : on savait ajouter, on ne savait pas retirer. Retirer était impensable, pour deux raisons devenues fausses : quelqu'un en dépendait (et n'avait aucune alternative), et personne ne saurait le refaire (le savoir avait disparu avec le développeur). L'IA a cassé les deux : celui qui dépend d'un outil rétrogradé peut le régénérer à l'étage utilisateur — il ne perd pas l'outil, il perd sa *garantie de stabilité*, ce qui est très différent — et refaire est devenu trivial par définition. Jeter est redevenu bon marché.

D'où le principe : la **descente** — rétrogradation, extinction — est une opération aussi légitime et aussi outillée que la montée. Un outil promu dont les métriques ne justifient plus le coût de considération redescend ; le périmètre reste élagué en permanence. Et le même principe s'applique à ce que le chapitre 7 a laissé en suspens : les règles exécutables aussi ont un cycle de vie. Une règle automatisée dont la décision source est morte ne devient pas un garde-fou — elle devient un mur absurde et infranchissable, pire que le wiki qu'elle remplaçait, car on pouvait au moins ignorer le wiki. Automatiser une règle sans lui donner une fin de vie, c'est bétonner l'absurde. Le stream de décisions — chaque décision a une mission, un début, une **fin** — est ce qui l'empêche.

L'asymétrie historique se retourne donc complètement : avant, ajouter un cas était coûteux et le retirer impensable ; maintenant, ajouter est facile et retirer aussi. **La rigidification n'est plus une fatalité — c'est un choix de gouvernance.** Une organisation qui se rigidifie désormais a choisi de ne pas élaguer.

## Le prix de la montée, sans le cacher

Un outil d'étage utilisateur, généré vite, n'est pas au standard d'une API d'entreprise, et la promotion n'est pas un tampon : c'est un chantier de **mise au standard** — revue, tests, sécurité, documentation. Les données disponibles sur le code généré en entreprise donnent l'ordre de grandeur du péage : des cycles de revue sensiblement allongés et un effort de test multiplié par rapport au code écrit à la main. C'est le prix du transfert de maintenance, et il faut le budgéter — c'est aussi, on l'aura compris, le harnais du chapitre 5 qui l'allège : un outil né sous harnais arrive à la promotion avec ses tests. Ce péage a une vertu cachée : il est le vrai filtre du cycle. Beaucoup d'outils très utilisés ne franchiront jamais la promotion parce que leur valeur ne paie pas leur mise au standard — et c'est la bonne réponse : ils resteront d'excellents outils d'équipe, sous contrat d'équipe.

## Ceux qui l'ont déjà fait — et les deux choses qui leur manquent

Ce cycle n'est pas une spéculation : l'industrie logicielle en a déjà construit tous les morceaux, séparément.

La méthode officielle de Microsoft pour gouverner sa plateforme low-code recommande une stratégie d'**environnements par étages** — bac à sable personnel, développement, test, production — avec des exigences croissantes et des pipelines pour franchir les étages : un cycle de promotion institutionnalisé, déployé dans des milliers d'organisations. Elle offre aussi, à son corps défendant, la meilleure preuve *négative* du chapitre : l'environnement par défaut, ce bac à sable que tout le monde peut utiliser et que personne ne peut supprimer, est documenté comme la première source de chaos de tout l'écosystème — des dizaines d'environnements non gérés découverts au premier audit. Un étage du bas sans chemin de promotion ni élagage ne reste pas un bac à sable : il devient une décharge. C'est précisément la descente qui manquait.

Le platform engineering a construit la mécanique de l'offre : les **golden paths** — des chemins outillés et documentés pour construire au standard de l'organisation, qu'on emprunte parce qu'ils sont le chemin le plus facile, pas parce qu'ils sont obligatoires. L'outil emblématique du domaine est lui-même un cas de promotion réussie : né outil interne chez un streamer suédois, ouvert, devenu standard de fait d'une industrie entière. Et le mouvement InnerSource applique depuis des années les pratiques open source à l'intérieur des entreprises : contribution inter-équipes, transfert de propriété, mutualisation — le modèle social du transfert de maintenance existe et a une communauté.

Deux choses, et deux seulement, manquent à tous ces précédents. Ils enferment la production dans une plateforme — le cycle y gouverne des artefacts propriétaires, avec le plafond et la captivité du chapitre 4 ; ici, le cycle gouverne du code pur et des API ouvertes. Et aucun ne documente la descente — toute la littérature parle de faire monter, jamais d'élaguer ; on vient de voir ce qu'il en coûte. Le cycle de ce chapitre est leur synthèse, plus les deux pièces manquantes.

## Ce qui manque encore au cycle

Un cycle, des contrats, des mesures, un sens de l'élagage. Restent deux questions sans lesquelles tout ceci demeure un beau dessin. Combien l'organisation peut-elle *tenir* de cas pris en compte — existe-t-il un budget, une jauge, un signal d'alerte ? C'est le chapitre 12. Et qui *fait* tout cela — qui observe les usages convergents, qui arbitre les promotions, qui pilote les harnais, et que deviennent les développeurs dans une entreprise qui fonctionne ainsi ? C'est le chapitre 13.

---

## Notes de rédaction (hors manuscrit)

- Source principale : [cycle-promotion-specifique](../01-concepts/cycle-promotion-specifique.md) — tout y est repris : étages, contrats, périmètre de considération, uniformisation a posteriori, métriques, fork/incitation, descente, asymétrie.
- La promesse du ch. 7 ("bétonner l'absurde") est tenue ici, comme prévu — les règles exécutables ont un cycle de vie via le stream de décisions.
- ~ Le péage de mise au standard : "cycles de revue sensiblement allongés, effort de test multiplié" — chiffres Apiiro (revue ×2, fixes post-merge ×3) dé-chiffrés car source vendeur ; valeurs dans [meta-analyse-cout-aval](../06-etat-de-lart/meta-analyse-cout-aval.md).
- Précédents : [methodologies-grandes-entreprises](../06-etat-de-lart/methodologies-grandes-entreprises.md) (Microsoft anonymisé en "méthode officielle… plateforme low-code" ; ~ "40-60 environnements" rendu par "des dizaines"), [innersource-golden-paths](../06-etat-de-lart/innersource-golden-paths.md) (Spotify/Backstage anonymisé en "streamer suédois" — noms en Annexe A).
- Formules candidates : "le générique de demain est le spécifique qui a survécu" ; "on ne retire pas l'outil de quelqu'un — on acte une mesure" ; "il ne perd pas l'outil, il perd sa garantie de stabilité" ; "la rigidification n'est plus une fatalité — c'est un choix de gouvernance" ; "un bac à sable sans élagage devient une décharge" ; "automatiser une règle sans fin de vie, c'est bétonner l'absurde".
- Le "vrai filtre du cycle" (des outils très utilisés qui ne montent jamais car la mise au standard ne se paie pas) est un ajout de rédaction — cohérent avec le modèle, à valider par Kevin.
- Grille lecteur : DSI ("comment ça ne devient pas le chaos ?") — réponse structurée en trois temps : presque rien ne monte, ce qui monte paie, ce qui ne sert plus descend.
- Sources ontologie : cycle-promotion-specifique, methodologies-grandes-entreprises, innersource-golden-paths, regle-executable-fin-du-wiki (cycle de vie), dcb-decisions-comme-events (mission/début/fin).
