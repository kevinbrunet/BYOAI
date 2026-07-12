# Exemple — Kagenti / AuthBridge (Red Hat)

## Source et statut de vérification

Contenu issu d'une série d'articles techniques Red Hat (mai-juin 2026) et d'un article Medium sur Kagenti. ⚠ Note de fiabilité : dans la conversation source, une première tentative de résumé a mêlé recherche réelle et reconstruction trop confiante (hallucination partielle reconnue et corrigée par la suite). Les éléments ci-dessous ont été revérifiés par une recherche ciblée ; ⚠ à re-vérifier directement sur les articles Red Hat avant toute citation publique.

Sources mentionnées : Red Hat ("Zero Trust for autonomous agentic AI systems", février 2026 ; série sur next.redhat.com, mai-juin 2026, dont la partie 3 datée du 24 juin 2026), un article Medium sur Kagenti.

## Le mécanisme : AuthBridge (sidecar Envoy)

Ce n'est pas le JWT et le mTLS qui se lient directement — c'est un sidecar Envoy (filtre ext-proc, external processing) qui intercepte la requête entre les deux couches et fait la traduction.

Séquence type (démo : Alice délègue à un agent `summarizer-tech`) :

1. Alice se connecte via Keycloak et obtient un token d'accès OIDC.
2. Elle délègue à `summarizer-tech` — sa requête arrive à l'agent-service.
3. Le filtre ext-proc d'Envoy intercepte la requête avant qu'elle n'atteigne l'agent-service.
4. L'ext-proc appelle l'endpoint de token exchange de Keycloak, échangeant le token OIDC d'Alice contre un nouveau JWT incluant le contexte de délégation (claim `act` imbriqué — voir [délégation d'identité agents](../01-concepts/delegation-agents-jwt-mtls.md)).
5. L'agent-service reçoit le JWT enrichi et le transmet au document-service.
6. Le document-service valide la signature du JWT contre l'endpoint JWKS de Keycloak, et extrait la chaîne de délégation.

## Table des sauts (transport vs application)

| Hop | identité mTLS (transport) | payload JWT (application) |
|---|---|---|
| Browser → User Service | TLS (pas de SVID) | Token OIDC : alice |
| User Service → Agent Service | SVID SPIFFE du user-service | Délégation : alice → summarizer-tech |
| Agent Service → Document Service | SVID SPIFFE de l'agent-service | JWT avec `sub: summarizer-tech`, `act: {sub: alice}` |
| Document Service → OPA Service | SVID SPIFFE du document-service | Requête policy : user=alice, agent=summarizer-tech |

La colonne mTLS répond à "quel service appelle ?" ; la colonne JWT répond à "pour le compte de qui ?".

## Le lien cryptographique entre les deux couches : RFC 8705

~ RFC 8705 (authentification client par mutual TLS) permettrait à Envoy, lors de l'échange de token, de présenter le certificat SPIFFE du service appelant comme preuve d'identité client auprès de Keycloak — le token JWT émis serait alors lié cryptographiquement au service qui a fait la demande, sans que le JWT lui-même contienne le certificat. *(Marqueur ~ : mentionné dans la conversation source avant la correction sur les hallucinations partielles — à revérifier directement sur la source Red Hat avant citation.)*

## Ce que Kagenti ajoute : attestation cryptographique de la chaîne

Format visé : `Client X acting on behalf of User Y for Audience Z with constrained authority`. La délégation resterait cryptographiquement préservée et auditable à travers les frontières de service, plutôt que de s'effondrer en simple impersonation ou identité de service autonome — chaque saut recevant son propre credential court terme et scopé.

⚠ Kagenti + AuthBridge sont annoncés dans Red Hat AI H2 2026 en "preview à venir" — pas encore livrés en produit à la date de la conversation source.

## Rétro-compatibilité

Point positif noté explicitement par la source : le format n'est pas un token custom — n'importe quel service qui sait valider un JWT standard peut participer à la chaîne de délégation, y compris une infra `[Authorize]` ASP.NET Core standard.

## La suite : credential gateway (partie 3, S3/STS)

La partie 3 de la série Red Hat (24 juin 2026) traite du "dernier kilomètre" : comment traduire un JWT scopé (résultat de l'intersection de permissions) en credentials spécifiques à une ressource réelle.

- Réutilise la même validation JWT que le document-service.
- Réutilise le même moteur OPA, étendu avec des règles spécifiques au service cible.
- Réutilise la même extraction de chaîne de délégation via les claims `act`.
- Seule pièce nouvelle : l'adaptateur qui traduit l'intersection en credentials acceptées par le service cible.

~ AWS S3/STS choisi en premier parce que les session policies STS implémenteraient nativement l'intersection de permissions (permissions effectives = policy du rôle IAM ∩ policy de session) — donc si le rôle IAM autorise deux périmètres mais que la session policy calculée n'en autorise qu'un, la session STS ne peut accéder qu'à ce périmètre. Les agents ne recevraient jamais les vraies credentials AWS, seulement des credentials de courte durée déjà scopées.

⚠ Un seul backend cible (AWS S3) prouvé dans une démo fonctionnelle à ce stade — le pattern se généralise en théorie à tout backend ayant son propre mécanisme de scope de session, pas seulement AWS.

## Lien avec le reste de la série

Ce mécanisme est une implémentation technique possible de la gouvernance décrite dans [BYOIA](../01-concepts/byoia.md) (facade MCP, allowlist de modèles, traçabilité) et du principe [structure/interface](../01-concepts/frontiere-structure-interface.md) : la vérification d'identité et de délégation reste dans l'infrastructure (structure), le travail de l'agent reste libre (interface).
