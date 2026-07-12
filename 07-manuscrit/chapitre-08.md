# Chapitre 8 — La délégation : qui agit, pour le compte de qui

Une requête arrive sur une API du socle : *changer le statut du dossier 4712*. Avant toute chose — avant même de vérifier des droits —, le socle doit répondre à une question qui paraît simple et ne l'est pas : qui est là ?

Ce n'est pas une question, en réalité. C'en est deux, presque toujours confondues, et leur confusion est la source de la plupart des dettes de sécurité qui s'accumulent en ce moment même autour des agents d'IA. Première question : **quel logiciel m'appelle ?** — quel service, quel processus, tournant où, déployé par qui. Seconde question : **pour le compte de qui agit-il ?** — quel humain, au bout de quelle chaîne d'intermédiaires, a voulu cette action. La première est une question d'infrastructure ; la seconde, une question de mandat. Ce chapitre construit la réponse aux deux, séparément puis ensemble — jusqu'au principe de fonctionnement des mécanismes, car c'est là que se joue la différence entre une gouvernance réelle et une gouvernance déclarée.

## L'anti-modèle : le prête-nom

Commençons par ce qu'il ne faut pas faire, parce que c'est ce que presque tout le monde fait. La façon la plus simple de donner des droits à un agent d'IA est de lui donner le jeton d'accès de son utilisateur — le token de session, tel quel. L'agent devient l'utilisateur : mêmes droits, mêmes accès, indiscernable dans les journaux. C'est l'**impersonation**, et la littérature de sécurité récente la range unanimement parmi les anti-patterns, pour deux raisons qui devraient suffire à la bannir du socle.

D'abord l'étendue : l'agent hérite de *tout* — l'utilisateur voulait qu'on lui résume des dossiers, son agent peut aussi les supprimer, consulter la paie, réinitialiser des mots de passe, puisque l'utilisateur le peut. Ensuite la trace : dans chaque journal, l'action apparaît comme celle de l'humain. Le jour où quelque chose tourne mal, il est impossible de distinguer ce que la personne a fait de ce que son IA a fait en son nom. Pour un socle dont la raison d'être est la confiance d'autrui, c'est disqualifiant : l'impersonation dissout précisément l'information qu'il fallait conserver — le fait qu'il y avait un mandataire.

## Deux couches, deux vérités

La réponse propre sépare les deux questions dans deux couches techniques indépendantes.

La première couche répond à "quel logiciel m'appelle". Son mécanisme de référence est le **mTLS** — TLS mutuel : chaque service, chaque workload, détient une identité cryptographique propre (dans l'écosystème standard, une identité SPIFFE, délivrée et renouvelée automatiquement par une infrastructure dédiée), et chaque connexion entre deux services prouve les deux identités à la fois. C'est la carte d'identité des machines, mature, standardisée, graduée au CNCF. Mais comprenez bien sa limite : le mTLS authentifie le porteur de la requête *à un saut donné*. Il sait que "agent-service" appelle "document-service". Il ne sait rien — structurellement rien — de la chaîne humaine qui a voulu l'appel.

La seconde couche répond à "pour le compte de qui", et vit dans le jeton applicatif — un JWT, jeton signé dont chacun peut vérifier l'émetteur. Le mécanisme clé s'appelle l'**échange de jeton** (Token Exchange, normalisé par la RFC 8693) : à chaque saut de délégation, on n'emporte pas le jeton de l'utilisateur — on l'échange auprès du serveur d'identité contre un nouveau jeton, qui dit explicitement *je suis l'agent Untel, agissant pour le compte d'Alice*. Techniquement, chaque échange ajoute une couche dans une claim nommée `act` — "agit pour" — sans écraser la précédente :

le jeton final dit `sujet : summarizer-tech`, `act : { sujet : alice }` — et si l'agent délègue à son tour, une couche s'ajoute encore. N'importe quel service en aval peut dérouler la chaîne complète jusqu'à son origine humaine. C'est la différence entre un prête-nom et un mandat : le mandat se voit, se lit, s'audite.

Les deux couches se vérifient indépendamment, et c'est leur force : un service compromis ne peut pas forger le jeton de délégation — il n'a pas la clé du serveur d'identité ; un jeton volé ne suffit pas — il faut aussi passer le contrôle d'identité machine du transport. Chaque couche borne les dégâts d'une compromission de l'autre. (Principe d'architecture solide ; sa garantie effective dépend, comme toujours, de l'implémentation.)

## Le calcul qui change tout : l'intersection sur la chaîne

Savoir qui appelle et pour qui n'est que la moitié du travail. Reste à décider : a-t-il le droit ? Et ici se loge l'idée la plus importante du chapitre, celle qui distingue ce modèle de tout ce que le contrôle d'accès classique sait faire.

La décision d'autorisation ne se prend pas sur le dernier maillon de la chaîne. Elle se prend sur **l'intersection des droits de toute la chaîne** : l'action est permise si, et seulement si, chaque maillon — l'humain d'origine, chaque agent intermédiaire, l'agent final — la permet. Un cas concret révèle toute la portée de la règle : Alice a le droit de consulter un dossier sensible ; elle délègue à un agent dont la configuration ne couvre pas ce périmètre ; l'agent présente une chaîne parfaitement valide — et la requête est **refusée**. Les droits d'Alice ne "passent" pas à travers un mandataire qui ne les a pas. L'intersection coupe dans les deux sens : l'agent ne peut rien faire que son mandant ne pourrait pas, et le mandant ne peut rien faire *via l'agent* que l'agent n'est pas habilité à porter.

Mesurez l'écart avec le contrôle d'accès par rôles traditionnel, qui répond à "ce rôle a-t-il ce droit" — une question à un seul acteur. Ici la question est "cette chaîne d'acteurs, dans cet ordre, a-t-elle collectivement ce droit" — impossible à préconfigurer quand on ne connaît pas les chemins à l'avance, et c'est exactement la situation : chaque salarié composera ses propres chaînes d'agents. L'intersection est la seule règle qui reste juste quel que soit le graphe.

## Où ça se loge : dans l'infrastructure, pas dans le code

Troisième principe, architectural celui-là : rien de tout cela ne doit vivre dans le code des agents ou des services métier. Une implémentation de référence — publiée par Red Hat sous les noms de Kagenti et AuthBridge — montre le pattern : un **sidecar**, petit processus posé devant chaque service, intercepte les requêtes et fait la traduction entre les deux couches. Séquence type : Alice s'authentifie et délègue à un agent ; le sidecar intercepte la requête entrante, appelle le serveur d'identité pour l'échange de jeton, et transmet au service un jeton enrichi de la chaîne `act` ; le service en aval n'a qu'à valider une signature et lire la chaîne. Le service est "auth-unaware" : il consomme une identité déjà vérifiée, sans implémenter lui-même la mécanique. La vérification appartient à la structure ; l'agent reste libre de son travail — la frontière du chapitre 6, appliquée à la sécurité elle-même.

Le même pattern règle le "dernier kilomètre", quand l'action finale vise une ressource qui a son propre système de droits — un stockage cloud, par exemple : une passerelle traduit l'intersection calculée en credentials éphémères et déjà réduites de la ressource cible, si bien que l'agent ne détient jamais les vraies clés — seulement une capacité temporaire, exactement aussi large que l'intersection.

Honnêteté de calendrier, due au lecteur : à la date d'écriture, ce pattern complet relève de l'architecture de référence documentée et de la démonstration — pas du produit sur étagère supporté. Les briques élémentaires, elles, sont mûres : l'identité de workload, l'échange de jeton simple, le serveur d'identité open source. C'est l'assemblage bout-en-bout, chaîne `act` comprise, qui est encore jeune. Nous y reviendrons.

## Le contrepoint : porter ses droits avec soi

Tout ce qui précède partage une hypothèse : à chaque décision, on interroge un point central — le serveur d'identité, le moteur de politique. C'est auditable, révocable à l'instant, cohérent. C'est aussi une dépendance réseau à chaque appel, et un point de passage obligé qui doit tenir la charge et rester disponible.

Il existe une autre école, et elle mérite le détour parce qu'elle réalise la même idée — l'intersection — par un moyen opposé. Son représentant le plus abouti s'appelle **Biscuit** (projet de la fondation Eclipse, en production chez un hébergeur européen depuis 2021). Le principe de fonctionnement : le jeton *contient* ses droits, exprimés en faits et en règles logiques ; et surtout, tout détenteur d'un jeton peut fabriquer, seul, hors ligne, un jeton **plus restreint** — en ajoutant un bloc de restrictions ("caveats") scellé cryptographiquement à la suite des blocs précédents, chaque bloc étant signé de sorte qu'on peut toujours restreindre mais jamais élargir ni retirer une restriction. Alice reçoit un jeton "lecture des dossiers du service" ; avant de le confier à son agent, elle y appose elle-même "seulement le dossier 4712, seulement aujourd'hui" — sans contacter aucun serveur. Le service qui reçoit le jeton vérifie la chaîne de signatures et évalue les règles, hors ligne aussi. L'intersection n'est plus calculée *par* un serveur central : elle est réalisée *dans* l'objet, par construction — chaque délégation ne peut qu'atténuer.

Les deux écoles dessinent la vraie ligne de fracture du domaine. Vérification centralisée : auditable, révocation immédiate, mais dépendance réseau et point central. Attestation embarquée : autonome, atténuation gratuite à chaque saut, mais révocation structurellement difficile — un jeton émis vit sa vie — et écosystème d'outillage plus jeune. Aucune synthèse mûre des deux n'existe à ce jour ; c'est un gap reconnu, pas une lacune de ce livre. Le choix dépend de votre contexte : un environnement fortement réglementé, où la révocation immédiate et l'audit central priment, penchera vers la première ; des agents nombreux, autonomes, parfois déconnectés, feront regarder la seconde.

## Ce qu'un DSI doit décider maintenant

Ce paysage bouge vite — les organismes de standardisation produisent des brouillons à un rythme inhabituel, les fournisseurs annoncent des cadres concurrents, et le trou est officiel : les standards d'identité de workload en cours ne définissent pas *l'autorité de délégation*, précisément la question de ce chapitre. Dans dix-huit mois, des noms auront changé. Voici ce qui n'aura pas changé, et qui constitue la commande à passer à vos équipes dès maintenant, quelle que soit la brique retenue :

que le socle distingue toujours l'identité du logiciel et le mandat de l'humain, vérifiés indépendamment ; que l'impersonation soit bannie — aucun agent ne détient jamais le jeton nu d'un utilisateur ; que toute chaîne de délégation soit lisible jusqu'à son origine humaine, dans chaque jeton, dans chaque journal ; que l'autorisation se calcule par intersection sur la chaîne entière, jamais sur le dernier maillon ; et que tout cela vive dans l'infrastructure, pas dans le code des agents. Cinq invariants. Les noms des briques qui les réalisent sont en annexe, datés, parce qu'ils périmeront ; les invariants, non.

Un lecteur attentif aura pourtant repéré qu'il manque une information dans notre chaîne `act`. Elle dit qui agit pour qui — `summarizer-tech` pour `alice`. Elle ne dit pas ce qu'*est* chaque maillon. Alice est-elle une personne assise devant un écran, ou un agent nommé d'après sa propriétaire ? Ce bit d'information — humain ou machine — paraît anodin. Il est la clé du chapitre qui vient, et de la promesse faite au chapitre 6 : des actions que l'IA ne pourra jamais acter.

---

## Notes de rédaction (hors manuscrit)

- Profondeur conforme à la décision "principes de fonctionnement, pas le code" : la claim `act` est montrée en une ligne descriptive, pas en JSON complet ; Biscuit est expliqué au niveau du mécanisme (blocs de caveats scellés, vérification hors ligne) sans Datalog explicite.
- Statuts et marqueurs (détail dans [cartographie-maturite](../05-questions-ouvertes/cartographie-maturite-authentification.md) et [identite-agents-standards](../06-etat-de-lart/identite-agents-standards.md)) :
  - ✓ RFC 8693 finalisée ; ⚠ implémentation Keycloak native du claim `act` en discussion ouverte — rendu par "l'assemblage bout-en-bout est encore jeune".
  - ⚠ Kagenti/AuthBridge : "architecture de référence et démonstration, pas produit supporté" — dit tel quel. Les noms sont cités une fois ; séquence et table des sauts narrativisées. ⚠ Le fichier source signale une hallucination partielle corrigée dans la conversation d'origine : re-vérification sur les articles Red Hat OBLIGATOIRE avant publication.
  - ~ RFC 8705 (liaison cryptographique des deux couches) : OMISE du corps du chapitre — marqueur ~ trop fragile ; à réintroduire en Annexe A si re-vérifiée.
  - ✓ SPIFFE/SPIRE CNCF graduated ; ✓ Biscuit Eclipse + Clever Cloud prod 2021 ("un hébergeur européen" dans le corps, nom en annexe).
  - ⚠ Chiffres d'adoption OAuth/MCP (8,5-18 %) : omis, non confirmés.
  - ✓ WIMSE ne définit pas l'autorité de délégation — rendu par "le trou est officiel".
- Le "credential gateway" S3/STS est généralisé prudemment ("un stockage cloud, par exemple") — un seul backend prouvé (⚠ du fichier source respecté).
- Décision de rédaction : les cinq invariants en clôture sont LE livrable du chapitre pour le lecteur DevSecOps — formulés comme une commande à passer aux équipes. Ils devront figurer tels quels dans la feuille de route du ch. 16.
- Grille lecteur : DevSecOps/RSSI ("quelles briques, quelle maturité") + l'anti-pattern impersonation donne au RSSI un critère d'audit immédiat.
- Sources ontologie : [delegation-agents-jwt-mtls](../01-concepts/delegation-agents-jwt-mtls.md), [kagenti-authbridge](../03-exemples/kagenti-authbridge-red-hat.md), [cartographie-maturite](../05-questions-ouvertes/cartographie-maturite-authentification.md), [identite-agents-standards](../06-etat-de-lart/identite-agents-standards.md).
