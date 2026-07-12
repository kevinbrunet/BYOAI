# Questions restantes — état consolidé au 2026-07-11

Remplace la vue d'ensemble de [questions-livre](./questions-livre.md) (qui garde le détail). Déjà tranché : ouverture du livre (captivité), doctrine de la frontière (5 questions), positionnement malleable software, réponse à l'objection low-code, série de 10 posts.

## 🔴 Bloquantes pour le livre

1. ✅ **Le lecteur cible — tranché (2026-07-11)** : le **leadership technique qui décide et gouverne** — DSI d'abord, avec les postes qui l'entourent : CTO, RSSI, DPO, DevSecOps, architectes d'entreprise. Ni plaidoyer COMEX (trop haut), ni manuel d'implémentation (trop bas). Conséquences :
   - **niveau de profondeur (précisé par Kevin)** : on descend loin dans les protocoles et les solutions existantes — jusqu'au **principe de fonctionnement** (ex. : comment Biscuit réalise l'atténuation hors ligne d'un token, comment le claim `act` s'imbrique, ce que fait un sidecar Envoy) — mais pas jusqu'au code. Le lecteur DevSecOps/architecte doit pouvoir évaluer et choisir les briques ; il ira lire les specs lui-même ;
   - **le juridique est un chapitre de premier rang**, pas une annexe : RSSI et DPO sont des lecteurs primaires (CSE, AI Act, proportionnalité) ;
   - **langue** : français (lectorat + différenciateur juridique franco-centré) — ferme la moitié de la Q25 ;
   - **ton** : entre pairs — le lecteur a vécu le low-code, le Shadow IT, les refontes ratées ; on peut s'appuyer sur cette expérience partagée (l'ouverture captivité fonctionne d'autant mieux) ;
   - chaque chapitre doit répondre à la question d'UN de ces postes (DSI : coût/gouvernance ; RSSI : surface d'attaque ; DPO : conformité ; DevSecOps : pipeline) — grille de relecture à appliquer au plan.
2. **La thèse falsifiable** (Q1) — quelle observation prouverait que le BYOIA est une mauvaise idée ? Sans réponse, c'est un manifeste.
3. 🔶 **Le nom — partiellement tranché (2026-07-11)** : le concept est positionné comme **extension du BYOAI** (on cite le phénomène documenté, on construit l'étage au-dessus). Un nouveau nom sera trouvé ; "BYOIA" reste le nom de travail. Critères du futur nom consignés dans [nom-byoia-vs-byoai](../05-questions-ouvertes/nom-byoia-vs-byoai.md).
4. ✅ **Zéro cas terrain — tranché (2026-07-11)** : il n'y aura pas de pilote. Le livre assume son genre : un **essai de philosophie d'architecture**, écrit pour exposer une vision et voir comment elle répond. Conséquences actées :
   - le genre est annoncé au lecteur dès l'introduction (proposition, pas retour d'expérience) — c'est une force si c'est assumé, une faiblesse si c'est dissimulé ;
   - les preuves empruntées remplacent le terrain : cas tiers documentés (Shell, Amazon, Haier, Deutsche Bahn), jurisprudence réelle, méta-analyse des données publiques — le corpus 06 devient le socle probatoire ;
   - tout ce qui n'a pas de données (régénérer vs maintenir, seuils de promotion) est présenté comme **prédiction falsifiable + protocole de mesure** — le livre fournit l'instrumentation (métriques du cycle, fenêtre) et invite le lecteur à produire les chiffres. Genre assumé : position paper, pas rapport d'étude ;
   - la série LinkedIn est le banc d'essai de la réception ("voir comment ça répond") — les retours des posts nourrissent la rédaction finale ;
   - recoupe la Q26 : le livre penche essai (vision) avec méthode actionnable en annexe, plutôt qu'ouvrage de référence.
5. **Le coût aval, chiffré** (Q7) — le cycle de promotion répond conceptuellement ; il manque toute donnée sur le coût réel de maintenance/régénération du code généré. Sans ça, l'argument 1 reste vulnérable.
6. **La relecture juridique** (Q11-12) — jurisprudences citées de seconde main, zone grise "qui est déployeur quand le salarié apporte son IA" (AI Act), distinguo filtrage URL/inspection contenu toujours ⚠. Un avocat en droit social doit passer sur les chapitres 4-5-7 avant publication.
7. ✅ **Le plan du livre — v1 écrite (2026-07-11)** : 15 chapitres en 5 parties (constat / régime économique / architecture / gouvernance / preuve et invitation) + 2 annexes. Chaque chapitre a sa question-lecteur et ses fichiers sources. Voir [plan-livre](./plan-livre.md). Décision par défaut incluse : le cluster multi-agents sort de ce livre (à confirmer).

## 🟡 Structurantes

8. **La mesure de la complexité** — la fenêtre de complexité n'a pas d'unité : dépendances ? coût de non-régression ? temps de prise en compte ? Sans métrique, c'est une image, et un DSI le verra.
9. **Les seuils de promotion** — les métriques d'utilisation déclenchent montée/descente, mais quels seuils, et l'usage suffit-il seul (un outil très utilisé mais risqué monte-t-il) ?
10. ✅ **Le droit de fork — tranché (2026-07-11)** : fork libre par défaut ; l'outil promu est une offre, pas une obligation. La contrainte vit à la couche accès (le SI restreint le nombre de chemins vers la donnée : humain-only, réglementaire), jamais à la couche outil. Voir [cycle-promotion-specifique](../01-concepts/cycle-promotion-specifique.md).
11. **L'arbitre humain** (Q18) — le cycle donne le processus, la doctrine donne le critère ; qui tranche les cas limites ? Rôle, comité, gouvernance — toujours vide.
12. **La collision DCB** — "Dynamic Consistency Boundary" est un terme établi (Pellegrini, Axon). Renommer ton concept, adopter le leur, ou désambiguïser ? Option (b) recommandée dans [dcb-event-sourcing](../06-etat-de-lart/dcb-event-sourcing.md), non validée par toi.
13. **Prouver l'humain** — le régime "API humain uniquement" suppose de distinguer un clic humain d'un agent qui clique. Ré-authentification forte (passkey, user presence) : à creuser jusqu'à une position ferme. Et traiter le rubber-stamping.
14. **Le cluster multi-agents** (Q4) — Condorcet, conseil d'agents, Moussaïd, chef-arbitre : dans ce livre, en annexe, ou second livre ? Le lien avec la thèse BYOIA n'est toujours pas explicité.
15. **La fiabilité des synchronisations** — deux options identifiées dans l'objection d'origine, aucune retenue.
16. **L'architecture de référence** (Q16) — le livre donne-t-il un schéma nommé complet (façade + gateway + délégation typée + cycle) ou des principes ? Le post 10 suppose que ce schéma existe — il n'est pas dessiné.
17. **Compétence des salariés** (Q19) — le développeur-harnais répond en partie ; reste à cadrer la proportion réaliste de salariés autonomes et le sort des autres.

## 🟢 Éditoriales

18. **Conversion posts → chapitres** (Q23) — réécriture ou compilation enrichie ?
19. **Le devenir du développeur** (Q20) — traité en creux (développeur-harnais, DIY coach) ; frontal ou pas ?
20. ✅ **Statut du parallèle holacratie — tranché (2026-07-11)** : c'était pour l'esprit, pas un fondement. Le label étant controversé, le livre s'appuie sur [Haier](../03-exemples/haier-rendanheyi.md) comme référence organisationnelle et évite le mot "holacratie" (au plus une mention en passant).
21. ✅ **Le happy path — tranché (2026-07-11)** : dans le livre, comme justification stratégique du problème de toute application d'entreprise et pivot vers la méthode — le générique n'implémente que le nominal (~35 % des sessions), le spécifique couvre les déviations, mais le spécifique naïf recrée le problème (pas de tests, mauvaise archi) → métier augmenté. Chaîne complète dans [happy-path-illusion-statistique](../01-concepts/happy-path-illusion-statistique.md).
22. **Titre, langue, canal, longueur** (Q25) — dépend de Q2.
23. **La méthode actionnable** (Q26) — checklist/canvas/feuille de route 90 jours en fin de livre : oui ou non ? (Le test des 5 questions + le cycle + la fenêtre en sont déjà les trois briques.)
24. **Anciens points ouverts hérités** — chef-arbitre vs détecteur (la recherche penche "chef-auditeur"), typologie Moussaïd (vérifier le livre réel), navigation guidée/contexte de projection, gap de la cartographie authentification (peut maintenant se fermer avec les drafts IETF 2026).

## Ordre d'attaque recommandé

Q2 (lecteur) → Q1 (thèse falsifiable) → plan chapitré (7) → architecture de référence (16) → pilote terrain (4). Les questions juridiques (6) peuvent avancer en parallèle chez un avocat ; les 🟡 se résolvent naturellement en écrivant les chapitres correspondants.
