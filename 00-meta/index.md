# BYOIA — Index / carte de l'ontologie

Cette série d'articles explore une philosophie de développement où l'IA générative déplace la frontière entre ce qui doit rester centralisé (structure, données, règles de gestion) et ce qui peut redevenir individuel (interfaces, outils métier, façon de travailler).

## Fil conducteur

L'uniformisation logicielle des 20 dernières années reposait sur une confusion entre deux couches : la donnée/les règles de gestion d'un côté, l'interface qui les manipule au quotidien de l'autre. L'IA générative rend possible de séparer proprement ces deux couches et de laisser le coût de production s'effondrer sur celle qui n'a jamais eu besoin d'être centralisée : l'interface.

## Carte des dossiers

- **01-concepts/** — les briques conceptuelles réutilisables dans toute la série
  - [générique vs spécifique](../01-concepts/generique-vs-specifique.md)
  - [approche data-centrique](../01-concepts/approche-datacentrique.md)
  - [BYOIA (Bring Your Own IA)](../01-concepts/byoia.md)
  - [frontière structure/interface](../01-concepts/frontiere-structure-interface.md)
  - [parallèle avec l'holacratie](../01-concepts/holacratie-parallele.md)
  - [accès conversationnel aux services](../01-concepts/acces-conversationnel.md)
  - [DCB — les décisions comme events](../01-concepts/dcb-decisions-comme-events.md)
  - [Délégation d'identité pour agents (JWT/mTLS)](../01-concepts/delegation-agents-jwt-mtls.md)
  - [Sagesse des foules et Condorcet](../01-concepts/sagesse-des-foules-condorcet.md)
  - [Taxonomie des angles morts construite empiriquement](../01-concepts/taxonomie-angles-morts-empirique.md)
  - [Conseil d'agents et pondération bayésienne](../01-concepts/conseil-agents-ponderation-bayesienne.md)
  - [Cadre juridique — obligation de consultation du CSE](../01-concepts/cadre-juridique-cse-consultation.md)
  - [Conformité par design](../01-concepts/conformite-par-design.md)
  - [Le paradoxe de l'armoire à fibre optique](../01-concepts/paradoxe-armoire-fibre-optique.md)
  - [L'épidémiologiste du backlog](../01-concepts/epidemiologiste-du-backlog.md)
  - [Presidio — fonctionnement technique de l'anonymisation](../01-concepts/presidio-anonymisation-technique.md)
  - [L'argument IA locale — souveraineté](../01-concepts/argument-ia-locale-souverainete.md)
  - [Le happy path n'existe pas — illusion statistique](../01-concepts/happy-path-illusion-statistique.md)
  - [Équipe agile interne — le développeur-harnais](../01-concepts/equipe-agile-developpeur-harnais.md)
  - [Cycle de promotion du spécifique](../01-concepts/cycle-promotion-specifique.md)
  - [Captivité logicielle — happy path social](../01-concepts/captivite-logicielle-happy-path-social.md)
  - [Positionnement — versant organisationnel du malleable software](../01-concepts/positionnement-malleable-software.md)
  - [La règle exécutable — la fin du wiki](../01-concepts/regle-executable-fin-du-wiki.md)
  - [Responsabilité du pilote et diversité des harnais](../01-concepts/responsabilite-pilote-diversite-harnais.md)
  - [Industrialisation — la chaîne de montage et le vivant](../01-concepts/industrialisation-chaine-montage.md)

- **02-arguments/** — les 5 arguments qui justifient le changement de régime économique
  - [1. Effondrement de l'économie d'échelle sur le code](../02-arguments/01-effondrement-economie-echelle-code.md)
  - [2. Interconnexion facilitée](../02-arguments/02-interconnexion-facilitee.md)
  - [3. Phase d'expérimentation, pas de maturité](../02-arguments/03-phase-experimentation.md)
  - [4. Le spécifique redevient supérieur au générique](../02-arguments/04-specifique-superieur-generique.md)
  - [5. Les garanties non négociables](../02-arguments/05-garanties-non-negociables.md)

- **03-exemples/** — cas concrets qui ancrent la théorie
  - [Claude Tag / Slack](../03-exemples/claude-tag-slack.md)
  - [Git, DoD, DoR dans la DSI](../03-exemples/git-dod-dor-dsi.md)
  - [Analogie Kubernetes / pods pour les rôles](../03-exemples/kubernetes-pods-roles.md)
  - [Kagenti / AuthBridge (Red Hat)](../03-exemples/kagenti-authbridge-red-hat.md)
  - [Architectures de référence pour l'agrégation multi-agents](../03-exemples/architectures-agregation-references.md)
  - [Moussaïd — "A-t-on besoin d'un chef ?"](../03-exemples/moussaid-a-t-on-besoin-dun-chef.md)
  - [Gateways de sécurisation LLM](../03-exemples/gateways-securisation-llm.md)
  - [Le mandat API d'Amazon (2002)](../03-exemples/amazon-mandat-api.md)
  - [Haier et le modèle RenDanHeYi](../03-exemples/haier-rendanheyi.md)

- **04-objections/** — points de friction identifiés, à trancher avant publication
  - [Déplacement du coût vers l'aval](../04-objections/deplacement-cout-aval.md)
  - [Frontière SI/interface si l'IA génère du code des deux côtés](../04-objections/frontiere-si-ia-genere-code.md)
  - [Arbitrage règle de gestion vs interface](../04-objections/arbitrage-regle-gestion-vs-interface.md)
  - [Fiabilité des synchronisations écrites par l'IA](../04-objections/synchronisation-fiabilite.md)
  - [Limite de l'analogie Kubernetes](../04-objections/limite-analogie-kubernetes.md)
  - [Trop de couches pour un seul post](../04-objections/trop-de-couches-un-seul-post.md)
  - [Le BYOIA n'est pas plus sûr juridiquement](../04-objections/byoia-pas-plus-sur-juridiquement.md)
  - [Pourquoi le BYOIA échapperait-il au destin du low-code/no-code ?](../04-objections/destin-low-code-no-code.md)

- **05-questions-ouvertes/** — arbitrages non tranchés, à creuser dans les prochaines sessions
  - [Doctrine sur la frontière SI/interface](../05-questions-ouvertes/doctrine-frontiere-si-interface.md)
  - [Série vs article unique](../05-questions-ouvertes/serie-vs-article-unique.md)
  - [Chiffres et références manquantes](../05-questions-ouvertes/chiffres-references-manquantes.md)
  - [Navigation guidée et contexte de projection](../05-questions-ouvertes/navigation-guidee-contexte.md)
  - [Cartographie de maturité des méthodes d'authentification](../05-questions-ouvertes/cartographie-maturite-authentification.md)
  - [Chef-arbitre vs chef-détecteur](../05-questions-ouvertes/chef-arbitre-vs-detecteur.md)
  - [Typologie explicite de Moussaïd](../05-questions-ouvertes/typologie-moussaid-explicite.md)
  - [Distinguo filtrage URL vs inspection de contenu](../05-questions-ouvertes/distinguo-filtrage-url-inspection-contenu.md)
  - [Le nom : BYOIA vs BYOAI](../05-questions-ouvertes/nom-byoia-vs-byoai.md)

- **07-manuscrit/** — chapitres rédigés (numérotation v3, 2026-07-12)
  - [Chapitre 1 — Le logiciel qu'on ne peut pas quitter](../07-manuscrit/chapitre-01.md)
  - [Chapitre 2 — Le happy path n'existe pas](../07-manuscrit/chapitre-02.md)
  - [Chapitre 3 — Le BYOAI est déjà dans vos murs](../07-manuscrit/chapitre-03.md)
  - [Chapitre 4 — L'économie du code s'est inversée](../07-manuscrit/chapitre-04.md)
  - [Chapitre 5 — Aucun harnais n'est parfait](../07-manuscrit/chapitre-05.md)
  - [Chapitre 6 — La frontière fiduciaire](../07-manuscrit/chapitre-06.md)
  - [Chapitre 7 — La structure : tout passe par l'API](../07-manuscrit/chapitre-07.md)
  - [Chapitre 8 — La délégation : qui agit, pour le compte de qui](../07-manuscrit/chapitre-08.md)
  - [Chapitre 9 — Des API interdites à l'IA](../07-manuscrit/chapitre-09.md)
  - [Chapitre 10 — La sécurisation est déjà payée](../07-manuscrit/chapitre-10.md)
  - [Chapitre 11 — Le cycle de promotion](../07-manuscrit/chapitre-11.md)
  - [Chapitre 12 — La fenêtre de complexité](../07-manuscrit/chapitre-12.md)
  - [Chapitre 13 — Le métier augmenté](../07-manuscrit/chapitre-13.md)
  - [Chapitre 14 — Le droit comme allié](../07-manuscrit/chapitre-14.md)
  - [Chapitre 15 — Ceux qui en ont déjà fait la moitié](../07-manuscrit/chapitre-15.md)
  - [Chapitre 16 — Les prédictions falsifiables](../07-manuscrit/chapitre-16.md)

- **06-etat-de-lart/** — recherche web (juillet 2026) : exemples, tentatives, méthodes existantes, avec lecture critique pour la série
  - [BYOAI, Shadow AI et le marché](../06-etat-de-lart/byoai-shadow-ai-marche.md)
  - [Logiciel malléable, personnel et jetable](../06-etat-de-lart/logiciel-malleable-jetable.md)
  - [Bilan low-code / citizen developer](../06-etat-de-lart/bilan-low-code-citizen-developer.md)
  - [Identité et délégation pour agents — standards](../06-etat-de-lart/identite-agents-standards.md)
  - [DCB et event sourcing](../06-etat-de-lart/dcb-event-sourcing.md)
  - [InnerSource et golden paths](../06-etat-de-lart/innersource-golden-paths.md)
  - [Jurisprudence CSE et IA 2025-2026](../06-etat-de-lart/jurisprudence-cse-ia-2026.md)
  - [Agrégation multi-agents](../06-etat-de-lart/multi-agents-agregation.md)
  - [Méthodologies de gouvernance des grandes entreprises](../06-etat-de-lart/methodologies-grandes-entreprises.md)
  - [Les solutions existantes face au BYOAI](../06-etat-de-lart/byoai-solutions-existantes.md)
  - [EU AI Act détaillé](../06-etat-de-lart/eu-ai-act.md)
  - [Méta-analyse — coût aval du code généré](../06-etat-de-lart/meta-analyse-cout-aval.md)
  - [Mesurer la complexité — outiller la fenêtre](../06-etat-de-lart/mesure-complexite-fenetre.md)
  - [IA et emploi — note Trésor-Éco](../06-etat-de-lart/ia-emploi-note-tresor.md)
  - [AI Readiness des dirigeants français (Kéa 2026)](../06-etat-de-lart/ai-readiness-kea-2026.md)

## Autres fichiers meta

- [Objectif de la série](./objectif-serie.md)
- [Backlog des posts (enrichissements + nouveaux posts)](./backlog-posts.md)
- [Série LinkedIn — les 10 posts, du BYOAI à l'assemblage](./serie-linkedin-10-posts.md)
- [Questions pour le livre](./questions-livre.md)
- [Questions restantes — état consolidé](./questions-restantes.md)
- [Plan chapitré du livre — v1](./plan-livre.md)
