# Doctrine sur la frontière SI/interface — TRANCHÉ (2026-07-11)

## La question (historique)

C'était le nœud de toute la série : où passe exactement la limite entre ce qui doit rester une règle de gestion côté SI (API commune) et ce qui peut être une logique de traitement codée par le collaborateur dans son interface ?

## La doctrine : le test des cinq questions

Cinq questions. **Un seul "oui" suffit : c'est le SI.** Cinq "non" : c'est l'interface.

1. **La donnée est-elle partagée ?** — entre un service, deux rôles/postes, ou l'entreprise entière : dès que quelqu'un d'autre s'appuie dessus, le formalisme passe par le SI.
2. **Le document est-il réglementaire ?** → SI.
3. **La règle de gestion est-elle auditable ?** — si un auditeur peut demander à la voir appliquée, elle vit dans le SI.
4. **Y a-t-il besoin de traçabilité ?** → SI.
5. **Y a-t-il changement d'état ?** — toute mutation du domaine passe par le SI.

Tout le reste — présentation, priorisation personnelle, projections, brouillons, assistance à la décision, ergonomie — est de l'interface, librement spécifique.

## La compression en une phrase

Les cinq critères ont un dénominateur commun : **si quelqu'un d'autre que toi doit pouvoir s'y fier (un collègue, un auditeur, un régulateur, le futur), c'est le SI. Si personne d'autre n'a besoin de s'y fier, c'est l'interface.** La frontière n'est pas technique, elle est fiduciaire.

## Lecture architecturale : écriture vs lecture

Le critère 5 recoupe une séparation connue : les **écritures** (commandes, mutations d'état du domaine) passent par le SI ; les **lectures** (projections, vues, agrégations personnelles) sont libres côté interface. C'est le découpage CQRS, et il s'emboîte directement avec [DCB — décisions comme events](../01-concepts/dcb-decisions-comme-events.md) : le stream d'events est côté SI, chaque interface construit ses propres projections.

Précision nécessaire sur le critère 5 : "changement d'état" signifie changement d'état **du domaine partagé**. L'état local de l'interface (un tri, un cache, une note personnelle) n'est pas concerné — sinon le critère avale tout.

## Le test appliqué au cas limite (dossier RH)

Le collaborateur RH qui accélère le traitement des dossiers avec son harnais ([cas posé ici](../04-objections/arbitrage-regle-gestion-vs-interface.md)) :

- lire les dossiers, les prioriser, préparer des brouillons de réponse, agréger des vues → cinq "non" → **interface**, libre ;
- changer le statut d'un dossier, valider une décision, notifier le salarié → changement d'état + traçabilité (+ souvent réglementaire) → **SI** : l'action passe par l'API commune, avec l'identité déléguée ([JWT/claim act](../01-concepts/delegation-agents-jwt-mtls.md)).

Le test tranche le cas en deux proprement : l'IA du collaborateur peut tout préparer, mais rien acter hors du SI.

## Conséquences en cascade

- **L'[argument 5](../02-arguments/05-garanties-non-negociables.md)** (garanties non négociables) cesse d'être sous-développé : les garanties, ce sont les cinq critères.
- **L'[objection low-code](../04-objections/destin-low-code-no-code.md)** tient désormais debout : la parade "mini-DSI dispersées" a son critère opérationnel.
- **Le [cycle de promotion](../01-concepts/cycle-promotion-specifique.md)** gagne son déclencheur naturel : le critère 1 (partage) est exactement le moment où un spécifique utilisateur doit être promu — dès que deux postes s'appuient sur la même chose, le formalisme monte au SI.
- **La [recette de cuisine](../01-concepts/captivite-logicielle-happy-path-social.md)** est une violation historique du critère 1 : de la donnée partagée entre postes qui ne passait pas par le SI. La doctrine ne crée pas une contrainte nouvelle — elle formalise ce qui aurait toujours dû l'être.

## Reste ouvert

- ⚠ Frontière organisationnelle ou technique ? Le test dit *quoi* mettre où ; [comment on l'impose](../04-objections/frontiere-si-ia-genere-code.md) reste à développer. **Élément de réponse (2026-07-11)** : le typage humain/agent dans la chaîne de délégation permet des API à trois régimes (ouvert / agent délégué / humain uniquement) — la frontière devient exécutoire dans la couche d'autorisation. Voir [délégation d'identité](../01-concepts/delegation-agents-jwt-mtls.md).
- Cas limites à tester dans le livre : le critère 3 (auditable) suppose de savoir *à l'avance* ce qu'un auditeur demandera — recoupe la [taxonomie des angles morts](../01-concepts/taxonomie-angles-morts-empirique.md) construite empiriquement.
