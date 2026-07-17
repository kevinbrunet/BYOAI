# Chapitre 9 — Des API interdites à l'IA

Depuis trois ans, les comités sécurité du monde entier se posent la même question : qu'est-ce que l'IA a le droit de lire ? Quelles données lui exposer, lesquelles filtrer, comment anonymiser. C'est une vraie question — le chapitre suivant lui est consacré. Mais ce n'est pas la bonne première question. Une IA qui lit trop crée un risque de fuite. Une IA qui **acte** — qui rejette un candidat, valide un licenciement, notifie un client, engage l'entreprise — crée un fait accompli. La bonne première question est : qu'est-ce que l'IA a le droit d'acter ? Et ce chapitre défend une réponse que l'air du temps rend presque provocante : pour certaines actions, la réponse doit être *jamais* — et ce *jamais* doit être une propriété technique de l'API, pas une consigne.

## Le bit manquant

Le chapitre 8 a construit la chaîne de délégation : chaque requête arrive avec son mandat — *l'agent Untel, pour le compte d'Alice, via tel intermédiaire*. La chaîne dit qui agit pour qui. Elle ne dit pas encore ce qu'**est** chaque maillon.

Car "Alice" au bout d'une chaîne, qu'est-ce que c'est ? Une personne, assise devant un écran, qui vient de cliquer ? Ou une session ouverte ce matin par une personne partie déjeuner, dont l'agent poursuit le travail ? La différence ne se voit pas dans un nom. Elle doit se voir dans le jeton : chaque maillon de la chaîne porte un **type** — humain authentifié ou charge de travail logicielle — établi par l'infrastructure d'identité, pas par une convention de nommage. Le serveur d'identité sait comment chaque identité s'est authentifiée : une personne par ses facteurs (mot de passe, passkey, biométrie), un workload par ses credentials machine. Ce savoir-là doit descendre dans le jeton et survivre à chaque échange, couche après couche. Un bit par maillon. C'est peu. C'est tout.

## Trois régimes par endpoint

Ce bit rend possible une politique d'autorisation que rien d'autre ne permet : typer non seulement les appelants, mais les **actions**. Chaque endpoint du socle se range dans l'un de trois régimes.

**Ouvert.** Humain ou agent, peu importe — les lectures, les projections, tout ce qui n'engage personne. C'est le régime par défaut de la couche interface : on l'a vu, les projections sont libres.

**Agent sous délégation.** L'action est ouverte aux agents si la chaîne est valide, le type de chaque maillon connu, et l'intersection des droits favorable. C'est le régime des écritures ordinaires — créer un brouillon partagé, mettre à jour un statut intermédiaire, déposer un résultat de calcul. L'agent agit, le mandat est lisible, le journal enregistre l'agent ET son mandant.

**Humain uniquement.** L'endpoint refuse tout appel dont l'initiateur direct n'est pas un humain authentifié — même si la chaîne de délégation est parfaitement valide, même si tous les droits sont réunis. Rejeter une candidature. Valider un licenciement. Signer un engagement. Notifier une décision à un client. L'IA peut avoir tout préparé — le dossier, l'analyse, le brouillon, la recommandation — mais le dernier appel, celui qui fait basculer l'état du monde, ne peut provenir que d'une personne.

Relisez maintenant la maxime du chapitre 6 — *l'IA peut tout préparer, elle ne peut rien acter hors du socle* — et complétez-la : et pour les actes les plus graves, elle ne peut rien acter **du tout**. "L'IA propose, l'humain décide" existe dans toutes les chartes d'usage de l'IA écrites depuis trois ans. La différence, ici, est catégorielle : ce n'est plus une phrase dans un document — le chapitre 1 a établi ce que valent les phrases dans les documents. C'est un refus que l'API oppose, mécaniquement, à chaque tentative, avec la raison en clair (chapitre 7) et la trace en journal. La règle la plus importante de la gouvernance de l'IA vient de passer du wiki au code.

Et mesurez l'avance que cela représente : l'enquête française citée au chapitre 3 révèle que la moitié des entreprises n'a défini **aucune** "ligne rouge" sur l'intégration de l'IA dans certains métiers ou certains usages — même déclarative, même sur le papier. Six sur dix n'ont aucun protocole pour gérer une décision erronée prise ou assistée par une IA[^9-1]. La question que ce chapitre outille n'est donc pas en retard sur le marché : dans la plupart des organisations, elle n'est pas encore posée.

Et ce déplacement règle au passage la question laissée ouverte au chapitre 6 : le gradient est-il organisationnel ou technique ? Réponse : il est organisationnel dans sa définition — c'est un choix humain de classer un endpoint dans un régime, donc à un niveau d'assurance donné — et technique dans son application. On décide en comité ; on applique dans la couche d'autorisation. Exactement la répartition qui manquait à toutes les gouvernances déclaratives.

## Ce que le droit va en faire

Une conséquence mérite d'être soulignée dès maintenant, avant même le chapitre juridique. Le règlement européen sur l'IA exige, pour les systèmes à haut risque — et les décisions touchant à l'emploi en font partie —, une "supervision humaine effective"[^9-2]. Toutes les organisations écriront des procédures pour en attester. Une organisation dont le socle applique le régime humain-uniquement n'attestera pas : elle **montrera**. Chaque décision à haut risque, dans ses journaux, porte la preuve qu'elle a été actée par un humain authentifié — parce qu'il était techniquement impossible qu'il en soit autrement. La supervision humaine cesse d'être un processus documenté pour devenir une propriété vérifiable du système. Le jour d'un audit, d'un contentieux prud'homal, d'une consultation CSE houleuse, la différence entre "nous avons une procédure" et "voici les journaux, et voici pourquoi ils ne peuvent pas mentir" est la différence entre se défendre et démontrer.

## Première faille : le tampon humain

Il faut maintenant faire ce que les vendeurs de solutions ne font jamais : attaquer honnêtement son propre dispositif. Il a deux failles, et les taire serait offrir au premier RSSI critique le plaisir de les trouver.

La première est vieille comme la supervision : le **tampon humain** — *rubber-stamping*. Si l'humain requis par le régime humain-uniquement se contente de cliquer "valider" sur tout ce que l'IA lui présente, le verrou est techniquement satisfait et humainement vide. Quarante validations à l'heure ne sont pas quarante décisions ; ce sont quarante clics. C'est la critique classique de toute supervision humaine, et le verrou technique n'y répond pas — il faut le dire sans détour : **le régime humain-uniquement est nécessaire, pas suffisant.**

Deux réponses s'emboîtent, aucune n'est magique. La première est de conception : rendre le clic coûteux à proportion de l'acte — présenter ce qui va être acté, ses conséquences, les points que l'analyse signale comme fragiles, et exiger davantage qu'un bouton pour les cas que l'IA elle-même déclare incertains. La seconde est le principe posé au chapitre 5 : **la responsabilité reste au pilote**. Si valider est un acte dont on répond personnellement — et le journal, qui enregistre le type de chaque maillon, établit précisément qui a validé quoi —, alors tamponner sans regarder n'est plus une faiblesse du système : c'est une faute de son opérateur, identifiable et imputable. Le verrou technique ne peut pas fabriquer l'attention ; il peut garantir que l'inattention a un nom.

## Seconde faille : prouver l'humain

La seconde faille est plus troublante : comment savoir que le "clic humain" est humain ? Un agent d'IA moderne sait piloter un navigateur, remplir un formulaire, cliquer un bouton — c'est même sa spécialité montante. Si l'humain requis délègue à son IA jusqu'à sa propre session, le typage de la chaîne certifie un mensonge.

La réponse honnête a trois étages. Techniquement : le régime humain-uniquement ne doit pas se contenter d'une session ouverte — il exige une **ré-authentification au moment de l'acte**, par un facteur que l'agent ne peut pas produire : une passkey avec preuve de présence utilisateur — le standard WebAuthn prévoit exactement ce test[^9-3] —, une biométrie locale, un geste physique sur un appareil enrôlé. L'agent peut cliquer ; il ne peut pas poser un doigt. Lucidement, ensuite : c'est une course. Chaque barrière élève le coût du contournement sans le rendre impossible — un humain complice peut toujours prêter son doigt. Juridiquement, enfin, et c'est l'étage décisif : la barrière transforme la *nature* du contournement. Franchir une ré-authentification forte pour faire acter une IA à sa place n'est pas une zone grise d'usage — c'est un acte délibéré, tracé, dont son auteur répond. On retrouve la même conclusion qu'au paragraphe précédent, et ce n'est pas un hasard : dans les deux cas, la technique ne remplace pas la responsabilité — elle la rend **inesquivable**.

## Le gradient, gardé

Fermons la boucle ouverte au chapitre 6. L'Assurance Level n'est plus une doctrine : le socle expose ses données et ses règles (chapitre 7), se souvient de ses décisions et refuse en expliquant (chapitre 7), sait qui l'appelle, pour le compte de qui, et ce qu'est chaque maillon de la chaîne (chapitre 8), et oppose aux actes qui exigent l'assurance maximale un refus que seule une personne authentifiée peut lever (ce chapitre). Une règle qu'on respecte est devenue une propriété qu'on constate.

Reste un angle que nous avons volontairement laissé de côté : entre l'IA du salarié et le socle, il y a un trajet — des requêtes qui partent vers des modèles externes, des données qui transitent, des réponses qui reviennent. Ce trajet-là aussi doit être gardé : filtré, anonymisé, journalisé. La bonne nouvelle, et c'est l'objet du chapitre suivant, est que cette infrastructure-là, vous n'aurez presque pas à la construire : le marché l'a déjà payée — pour d'autres raisons.

## Notes et sources

[^9-1]: Mêmes chiffres que l'enquête Kéa × OpinionWay 2026 (voir ch. 3) : ~ 51 % des organisations n'ont défini aucune « ligne rouge » sur l'intégration de l'IA (19 % l'ont fait) ; ~ 60 % n'ont aucun protocole pour gérer une décision erronée prise ou assistée par une IA. ⚠ Source primaire à revérifier.

[^9-2]: ✓ Règlement européen sur l'IA — *AI Act*, règlement (UE) 2024/1689 : obligation de supervision humaine effective pour les systèmes à haut risque (art. 14) ; l'emploi et la gestion des travailleurs figurent à l'annexe III. ⚠ Numéros d'articles et périmètre exacts à valider en relecture juridique — développé au ch. 14.

[^9-3]: ✓ WebAuthn (W3C) / FIDO2 : l'authentification par passkey avec vérification de présence utilisateur fournit un facteur qu'un agent logiciel ne peut pas produire seul. Exploité ici pour la ré-authentification au moment de l'acte.

---

## Notes de rédaction (hors manuscrit)

- Chapitre issu du concept marqué **critique** par Kevin : [delegation-agents-jwt-mtls — section humain/agent](../01-concepts/delegation-agents-jwt-mtls.md) et structure du post prioritaire du [backlog](../00-meta/backlog-posts.md). L'angle d'attaque du post ("lire vs acter") ouvre le chapitre.
- Les deux failles sont traitées dans l'ordre et avec les réponses actées : rubber-stamping → conception (friction proportionnelle) + responsabilité au pilote ([responsabilite-pilote-diversite-harnais](../01-concepts/responsabilite-pilote-diversite-harnais.md)) ; prouver l'humain → ré-authentification à l'acte (WebAuthn/user presence ✓ standard existant), lucidité sur la course, et requalification juridique du contournement.
- Formules candidates pour la promo du livre : "la règle la plus importante de la gouvernance de l'IA vient de passer du wiki au code" ; "l'agent peut cliquer ; il ne peut pas poser un doigt" ; "la technique ne remplace pas la responsabilité — elle la rend inesquivable" ; "le verrou peut garantir que l'inattention a un nom".
- La question ch. 6 "frontière organisationnelle ou technique" est fermée ici (définition organisationnelle, application technique) — mettre à jour le "reste ouvert" de la [doctrine](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) après validation.
- L'AI Act est annoncé sans être exposé (une phrase sur l'art. 26 sans le numéroter) — l'exposition complète reste au ch. 14, conformément à la décision du ch. 6.
- ⚠ "Les décisions touchant à l'emploi sont haut risque" : exact (annexe III) mais vérifier la formulation juridique précise à la relecture avocat.
- Grille lecteur : RSSI/DPO ("comment garantir que l'IA n'acte jamais seule ?") — le RSSI reçoit en plus deux critères d'audit : présence du typage humain/workload dans les jetons, et ré-authentification à l'acte sur les endpoints critiques.
- Sources ontologie : delegation-agents-jwt-mtls (section humain/agent), responsabilite-pilote-diversite-harnais, regle-executable-fin-du-wiki (raison à l'activation), backlog-posts (post prioritaire).
