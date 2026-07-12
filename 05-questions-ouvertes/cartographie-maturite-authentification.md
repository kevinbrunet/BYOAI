# Cartographie de maturité — méthodes de délégation d'identité pour agents

Synthèse consolidée des approches de délégation de droits pour agents IA, avec niveau de maturité et de certitude par source. Marqueurs conservés tels qu'établis dans la conversation source (✓ = fiable, ~ = approximatif à vérifier, ⚠ = incertain/extrapolé).

## Vue d'ensemble par paradigme

| Approche | Principe | Maturité | Certitude |
|---|---|---|---|
| Impersonation (token complet) | L'agent hérite de tous les droits de l'utilisateur | ✓ Répandu, reconnu comme anti-pattern par la littérature récente | ✓ |
| OAuth 2.1 sur MCP | Auth standard resource server, mandatée par le spec | ⚠ Mandatée en théorie, ~8,5–18% d'adoption réelle selon sources secondaires non confirmées | ⚠ pour les chiffres, ✓ pour le mandat spec |
| RFC 8693 Token Exchange (impersonation) | Échange un token pour un autre, scope réduit | ✓ Mature, implémenté nativement dans Keycloak, démos en prod (Spring Cloud Gateway) | ✓ |
| RFC 8693 Token Exchange (délégation, claim `act`) | Préserve l'identité déléguante via `act`/`may_act` imbriqués | ⚠ Spec finalisée, implémentation Keycloak native en discussion GitHub ouverte (#43108) — pas out-of-the-box | ✓ pour la RFC, ⚠ pour l'implémentation Keycloak |
| Capability-based / macaroons | Droits encodés dans le token, atténuation offline par chaînage HMAC | ✓ Solide en théorie (papier fondateur Google 2014), usage réel limité et peu documenté hors gros acteurs | ✓ théorie, ⚠ adoption |
| Biscuit (Eclipse) | Macaroon + Datalog + crypto asymétrique | ✓ Projet Eclipse Foundation, cas d'usage prod documenté (Clever Cloud depuis 2021) | ✓ pour Rust/référence, ⚠ fort pour un binding C# (projet individuel non officiel) |
| Permission intersection (Red Hat/OPA) | Intersection droits user ∩ droits agent, calculée à chaque requête | ⚠ Architecture de référence documentée en 3 articles (mai-juin 2026), explicitement qualifiée "pas en produit supporté" par la source elle-même | ✓ sur le principe, ⚠ sur la maturité produit |
| SPIFFE/SPIRE | Identité cryptographique de workload (mTLS), pas de la délégation | ✓ Projet CNCF graduated | ✓ |
| Kagenti + AuthBridge | Orchestration lifecycle agent + injection de la chaîne `act` signée | ⚠ Prévu "preview à venir", pas encore livré en produit à la date de la source | ⚠ |
| Credential gateway (S3/STS) | Traduit l'intersection en credentials scopées côté ressource réelle | ⚠ Démo fonctionnelle documentée, un seul backend cible (AWS S3) prouvé | ⚠ |
| Okta XAA/ID-JAG | Produit commercial, token exchange + révocation native | ✓ Produit propriétaire mature, mais fermé — pas auditable, pas self-hostable | ✓ maturité produit |
| SatGate | Capability tokens as-a-service, budget/TTL/scope | ⚠ Produit commercial très récent, aucun retour client trouvé, aucune certification identifiée | ⚠ fort |
| Keycloak (IdP de base) | OIDC/OAuth2.1 self-hosted, open source | ✓ Très mature, Red Hat-backed | ✓ |

## La ligne de fracture centrale

Deux familles s'opposent structurellement, sans réconciliation mature identifiée à ce jour :

- **Vérification centralisée à chaque appel** (Red Hat/OPA, Keycloak/RFC 8693, Okta) : auditable, révocable immédiatement, mais dépendance réseau à chaque décision.
- **Vérification offline par crypto embarquée** (macaroons, Biscuit) : pas de dépendance réseau, mais révocation structurellement difficile, écosystème d'outillage plus pauvre.

## Le gap identifié

⚠ Aucune solution recensée dans la conversation source ne combine à la fois : (a) atténuation offline vérifiable sans réseau, (b) maturité produit/écosystème équivalente à OAuth, (c) auditabilité simple pour un contexte réglementaire type dispositif médical logiciel. Signalé comme un vrai gap de marché plutôt qu'une lacune de recherche — donc à ne pas forcer un choix "clé en main" qui n'existe pas encore.

## Lien avec le reste de la série

Cette cartographie documente les options concrètes pour implémenter la gouvernance décrite dans [BYOIA](../01-concepts/byoia.md) (facade MCP, allowlist de modèles OAuth 2.1) et détaillée dans [délégation d'identité pour agents](../01-concepts/delegation-agents-jwt-mtls.md) / [exemple Kagenti-AuthBridge](../03-exemples/kagenti-authbridge-red-hat.md).
