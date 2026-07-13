# Chapitre 6 — La frontière fiduciaire

Commençons par un endroit où la frontière que cherche ce chapitre existe déjà, fonctionne depuis des années, et ne choque personne : une équipe de développement.

Regardez comment travaille une DSI moderne. Le dépôt Git est commun. Les règles de sécurité sont communes. Les rôles, les états des tickets, les Definition of Ready et Definition of Done — ce qui définit qu'un travail peut commencer et qu'un travail est terminé — sont communs. Et à l'intérieur de ce cadre, la façon dont chaque développeur réalise concrètement son étape est son affaire : son éditeur, ses scripts, ses raccourcis, sa façon de déboguer, et depuis peu son assistant d'IA. Personne n'impose l'éditeur ; personne ne négocie la DoD. La structure est commune, la réalisation est individuelle, et chacun sait spontanément de quel côté chaque chose se range.

Ce que propose ce livre tient en une phrase : généraliser ce partage à toute l'entreprise. Le support, la RH, la finance, chacun interagissant avec un socle commun — les données, les règles, les états — et branchant dessus sa façon de produire, y compris son équipe d'IA personnelle. Les chapitres 4 et 5 ont établi que c'est devenu économiquement possible — et à quelles conditions d'outillage. Reste la question qui fâche : dans une DSI, la répartition est intuitive parce que des décennies de pratique l'ont réglée. Ailleurs, qui dit ce qui est "structure" et ce qui est "réalisation" ? Il nous faut un critère — pas une philosophie, un test. Quelque chose qu'un architecte peut appliquer un lundi matin à n'importe quel artefact, et qui donne la même réponse quel que soit l'architecte.

## Le test des cinq questions

Le voici. Face à n'importe quel artefact — une donnée, une règle, un document, un traitement — posez cinq questions :

**La donnée est-elle partagée ?** Si un autre poste, un autre rôle, un service, l'entreprise entière s'appuie dessus — dès que deux personnes s'appuient sur la même chose —, son formalisme passe par le SI.

**Le document est-il réglementaire ?** S'il existe parce qu'une obligation externe l'exige, il vit dans le SI.

**La règle est-elle auditable ?** Si un auditeur, un commissaire aux comptes, une autorité peut un jour demander à la voir appliquée, elle vit dans le SI.

**Y a-t-il besoin de traçabilité ?** Si "qui a fait quoi, quand" devra pouvoir être répondu, ça passe par le SI.

**Y a-t-il changement d'état ?** Si l'action modifie l'état du domaine partagé — un statut qui bascule, une validation, une notification qui engage —, elle passe par le SI.

**Un seul "oui" suffit : c'est le SI. Cinq "non" : c'est l'interface**, et elle appartient au collaborateur — présentation, priorisation, projections, brouillons, assistance, ergonomie, tout ce qui l'aide à travailler sans engager personne d'autre.

Une précision d'emblée sur la cinquième question, car elle est la plus puissante et pourrait tout avaler : "changement d'état" signifie changement d'état **du domaine partagé**. Trier ses propres dossiers, annoter sa propre vue, mettre en cache une projection — c'est de l'état local, ça ne compte pas. Les lecteurs familiers de l'architecture logicielle reconnaîtront un découpage connu : les écritures — les commandes qui font muter le domaine — passent par le socle commun ; les lectures — les projections, les vues, les agrégations que chacun se construit — sont libres. La séparation commande/requête, appliquée à l'organisation entière[^6-2].

## Le dénominateur commun : la confiance d'autrui

Regardez maintenant ce que les cinq questions ont en commun. Partagé : quelqu'un d'autre s'appuie dessus. Réglementaire : une autorité s'appuie dessus. Auditable : un contrôleur s'appuie dessus. Traçable : le futur s'appuie dessus. Changement d'état : tout le monde s'appuiera dessus. Cinq déclinaisons d'un seul critère :

**Si quelqu'un d'autre que toi doit pouvoir s'y fier, c'est le SI. Si personne d'autre n'a besoin de s'y fier, c'est ton interface.**

C'est pourquoi ce livre appelle cette ligne la frontière **fiduciaire** — du latin *fiducia*, la confiance. La frontière ne sépare pas le technique du fonctionnel, ni le back du front, ni même le complexe du simple. Elle sépare ce qui engage la confiance d'autrui de ce qui n'engage que soi. Et elle éclaire d'un coup le chapitre 1 : la recette de cuisine passée à la machine à café était une violation permanente de cette frontière — de la connaissance partagée entre postes, dont d'autres dépendaient, qui ne passait par aucun formalisme commun. La doctrine ne crée pas une contrainte nouvelle ; elle formalise ce qui aurait toujours dû l'être, et que l'uniformisation économique avait rendu impossible à formaliser proprement.

## Le test à l'épreuve : le dossier RH

Prenons le cas le plus délicat, celui qui décide de la crédibilité du critère. Une gestionnaire RH construit — ou fait construire, on y reviendra — son harnais d'IA pour accélérer le traitement des dossiers. Où s'arrête son droit ?

Déroulez le test. Lire les quarante dossiers en attente, les résumer, les prioriser selon sa propre logique, préparer des projets de réponse, agréger une vue "dossiers sensibles" que le SI n'a jamais proposée : rien de partagé, rien de réglementaire en soi, rien d'audité, pas de trace exigée, aucun état du domaine modifié. Cinq non — **interface**. Son IA peut faire tout cela, à sa façon, sans demander la permission de personne.

Changer le statut d'un dossier, valider une décision, notifier le salarié concerné : l'état partagé bascule, la traçabilité est exigée, l'auditabilité probable, le réglementaire pas loin. **SI** — l'action passe par l'API commune, avec tout ce que cela impliquera de contrôles aux chapitres suivants.

Le test coupe le cas en deux, proprement, et la coupe a du sens : **l'IA peut tout préparer, elle ne peut rien acter hors du socle commun.** Préparer relève de la liberté individuelle ; acter engage la confiance des autres. Cette maxime — préparer librement, acter par le SI — reviendra au chapitre 9, où elle cessera d'être une règle de gouvernance pour devenir une propriété technique qu'une API refuse ou accepte.

Au passage, une objection tombe d'elle-même : "votre frontière tient-elle si l'IA génère du code des deux côtés ?" Oui — parce que le critère ne porte pas sur *qui* écrit le code, mais sur *ce que l'artefact touche*. Que le connecteur côté SI ait été écrit par un développeur, généré par une IA sous validation, ou les deux, il touche du partagé : régime complet. Que l'outil de projection ait été écrit à la main ou généré en une heure : il ne touche rien de fiduciaire, régime libre. L'auteur du code est indifférent à la frontière ; c'est la destination qui gouverne. Et le chapitre 4 a montré que c'est exactement la ligne que dessinent les données de qualité.

## Le précédent : quatre lignes de Bezos

Un critère aussi tranchant appelle la question : est-ce tenable à grande échelle, dans une vraie organisation, avec de vrais legacy ? Il existe un précédent, et pas un petit.

Vers 2002, Jeff Bezos impose par mémo interne à toutes les équipes d'Amazon un ensemble de règles restées célèbres : toutes les équipes exposent leurs données et leurs fonctionnalités uniquement à travers des interfaces de service ; les équipes ne communiquent entre elles qu'à travers ces interfaces ; aucune autre forme de communication n'est tolérée — pas de lecture directe de la base d'une autre équipe, pas de mémoire partagée, **pas de porte dérobée** ; la technologie utilisée est indifférente ; et chaque interface, sans exception, doit être conçue pour pouvoir un jour être exposée à l'extérieur. Le mémo se conclut, selon le témoignage qui nous l'a transmis, par : quiconque ne s'y plie pas sera licencié[^6-1].

Reconnaissez la structure : c'est la frontière fiduciaire, version 2002, appliquée à des équipes plutôt qu'à des salariés et leurs IA. Interdire les portes dérobées, c'est dire que tout changement d'état passe par le socle. Concevoir chaque interface comme exposable, c'est traiter chaque frontière interne comme fiduciaire — comme si un tiers devait pouvoir s'y fier, car un jour un tiers s'y fiera. Ce qu'il advint mérite d'être médité : la transformation prit des années, elle fut douloureuse — les témoignages décrivent l'apprentissage brutal du distribué, des quotas, du monitoring —, et son sous-produit fut AWS : l'infrastructure interne, conçue dès le départ comme un produit, en devint un, et le plus rentable de l'entreprise. Le mandat visait la dette d'intégration ; il a créé une option sur un futur que personne n'avait anticipé.

La leçon pour un DSI est double, et honnête. D'abord : le prérequis du modèle proposé ici — un socle intégralement accessible par API, sans contournement toléré — est atteignable ; la plus grande entreprise du monde l'a fait, à une échelle et avec un legacy qui relativisent tous les nôtres. Ensuite : ce n'est pas gratuit. Une DSI qui part de loin doit budgéter ce chantier comme Amazon l'a subi — en années, pas en trimestres. La bonne nouvelle est que chaque brique posée rend service immédiatement, IA ou pas : c'est le même chantier que l'urbanisation par API que la plupart des DSI ont déjà entamée. Le modèle de ce livre n'exige pas un SI parfait ; il exige que la direction du chantier soit la bonne.

## Une frontière n'existe que gardée

Résumons la deuxième partie du livre. L'économie a changé : production effondrée, validation intacte — deux régimes de code. La validation s'industrialise dans le harnais, mais aucun harnais ne se suffit — le chapitre 5 a montré pourquoi ce qui engage autrui ne peut pas reposer sur l'outillage d'une seule personne. La frontière fiduciaire dit lequel des deux régimes s'applique à quoi : ce à quoi d'autres doivent se fier relève du socle et du régime complet ; le reste appartient à chacun. Le test tient en cinq questions, il résout les cas difficiles, il a un précédent industriel.

Il a aussi, en l'état, une faiblesse que le lecteur attentif aura vue : c'est une doctrine. Un document de plus, dirait le chapitre 1 — et on sait ce que deviennent les documents. Une frontière n'existe que si quelque chose la garde. Comment un socle commun sait-il *qui* l'appelle — l'humain, ou son IA ? Comment sait-il *pour le compte de qui* agit un agent, au bout d'une chaîne de délégations ? Et comment refuse-t-il, techniquement, qu'une IA acte ce que seul un humain doit acter ? C'est la troisième partie de ce livre : faire descendre la frontière dans l'infrastructure, jusqu'à ce qu'elle cesse d'être une règle qu'on respecte pour devenir une propriété qu'on constate.

## Notes et sources

[^6-1]: Mandat API d'Amazon (~ 2002). ~ Aucune source primaire publique : l'épisode est connu par le témoignage de Steve Yegge, *Stevey's Google Platforms Rant* (2011), ancien ingénieur d'Amazon. Les six règles et la clause finale (« quiconque ne s'y plie pas sera licencié ») sont paraphrasées d'après ce récit, non citées d'un document original — le texte l'assume. ✓ La naissance d'AWS comme sous-produit de l'urbanisation interne par API est, elle, largement documentée.

[^6-2]: ✓ Séparation commande/requête (*Command-Query Separation*, Bertrand Meyer) et son extension architecturale CQRS : les commandes mutent l'état, les requêtes le lisent sans effet de bord. Analogie transposée ici à l'échelle de l'organisation.

---

## Notes de rédaction (hors manuscrit)

- Structure : l'exemple Git/DoD/DoR ouvre le chapitre au lieu de l'illustrer — application de la recommandation éditoriale de [git-dod-dor-dsi](../03-exemples/git-dod-dor-dsi.md) ("l'exemple devrait porter l'abstraction dès le départ").
- Le test des cinq questions et la compression fiduciaire : [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md). Le cas RH : [arbitrage — tranché](../04-objections/arbitrage-regle-gestion-vs-interface.md). L'argument 5 (garanties non négociables) est absorbé ici : les garanties = les cinq critères.
- L'objection "l'IA code des deux côtés" est tranchée par la 3ᵉ voie (ni "organisationnelle" ni "implicite") : le critère porte sur l'artefact, pas sur l'auteur — décision de rédaction, cohérente avec la doctrine ; mise à jour du fichier objection à faire.
- ~ Mandat Bezos : "vers 2002", "selon le témoignage qui nous l'a transmis" (Yegge 2011) — le texte assume l'absence de source primaire sans le cacher, conformément à [amazon-mandat-api](../03-exemples/amazon-mandat-api.md). La citation finale est paraphrasée, pas guillemétée.
- La coïncidence avec la ligne haut risque AI Act est volontairement ABSENTE de ce chapitre (prévue au plan) : elle sera plus forte au ch. 14, une fois l'AI Act exposé — le renvoi anticipé aurait exigé d'expliquer l'AI Act ici. Décision à valider ; le plan v2 la mentionnait à ce chapitre (alors numéroté ch. 5).
- Le chapitre ferme la Partie II et ouvre la III par la question de l'enforcement — la maxime "préparer librement, acter par le SI" est posée ici pour être outillée au ch. 9.
- Ouverture et résumé retouchés le 2026-07-12 (option B) : la transition vient désormais du ch. 5 (harnais/pièges) et le résumé de Partie II intègre "aucun harnais ne se suffit".
- Grille lecteur : tous les postes ("qu'est-ce qui reste à moi ?") ; le DSI reçoit en plus l'honnêteté du coût (chantier en années).
- Sources ontologie : doctrine, arbitrage, frontiere-si-ia-genere-code, git-dod-dor-dsi, amazon-mandat-api, 05-garanties-non-negociables.
