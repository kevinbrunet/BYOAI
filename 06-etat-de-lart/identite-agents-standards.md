# État de l'art — Identité et délégation pour agents IA (recherche web, juillet 2026)

## Où en est la standardisation

- ✓ **IETF draft actif** : *OAuth 2.0 Extension: On-Behalf-Of User Authorization for AI Agents* (draft-oauth-ai-agents-on-behalf-of-user, version -02) — étend l'authorization code flow pour porter l'identité de l'agent à travers l'écran de consentement jusque dans l'access token : l'utilisateur accorde à *un agent précis* des *pouvoirs précis*, et chaque système aval voit qui a agi. Confirme et actualise [délégation-agents-jwt-mtls](../01-concepts/delegation-agents-jwt-mtls.md).
- ✓ **WIMSE (IETF)** : drafts actifs début 2026 — architecture (incluant explicitement les agents IA comme cas d'usage), credentials de workload, format d'identifiant, profil mTLS. **Mais WIMSE ne définit pas l'autorité de délégation** — le trou est officiel.
- ✓ **MCP** exige OAuth 2.1 pour les serveurs distants — valide la brique "allowlist de modèles OAuth 2.1" de [byoia.md](../01-concepts/byoia.md).
- ✓ **Fragmentation assumée** : densité inhabituelle de drafts agent-identity à l'IETF au T1 2026 ; ~ cinq vendeurs auraient annoncé cinq frameworks d'identité d'agents la même semaine à RSAC 2026 (source secondaire, à vérifier) — pas de consensus, risque réel de fragmentation.
- ✓ Recherche académique active : *AIP — Agent Identity Protocol for Verifiable Delegation Across MCP and A2A* (arXiv 2026) ; *Deterministic Pre-Action Authorization for Autonomous AI Agents* (arXiv 2026).

## À couvrir au niveau "principe de fonctionnement" (profondeur voulue par Kevin)

- ✓ **Biscuit** (biscuitsec.org, initié chez Clever Cloud) : token porteur à **atténuation hors ligne** — le détenteur peut restreindre lui-même les droits d'un token (ajouter des caveats) sans contacter l'émetteur, chaque atténuation étant scellée cryptographiquement ; politiques d'autorisation exprimées en Datalog. Pertinence directe : l'atténuation EST l'intersection de permissions de la chaîne de délégation, réalisée par construction dans le token — le principe que le claim `act` + policy engine obtiennent avec un serveur, Biscuit l'obtient dans l'objet lui-même. Candidat idéal pour illustrer "le principe de fonctionnement sans le code". ~ Maturité et adoption à re-vérifier au moment de la rédaction.
- Autres briques à traiter à cette profondeur : token exchange RFC 8693 (mécanique de l'échange), mTLS/SPIFFE (identité de workload), sidecar Envoy (interception), MCP (négociation OAuth), passkeys/WebAuthn user presence (pour le régime humain-only).

## Lecture critique pour la série

1. La [cartographie de maturité](../05-questions-ouvertes/cartographie-maturite-authentification.md) peut maintenant être finalisée avec des ancres réelles : draft OBO -02, WIMSE (sans délégation), MCP OAuth 2.1, AIP.
2. **Le gap identifié dans la série est confirmé par l'état des drafts** : personne ne standardise l'autorité de délégation de bout en bout. La série avait vu juste — à dire avec les références.
3. Conséquence éditoriale : le chapitre technique doit s'écrire au niveau des **invariants** (séparation transport/application, intersection de permissions sur la chaîne, identité de l'agent visible en aval) et renvoyer les noms de drafts en annexe datée — c'est la réponse à la question 17 (obsolescence).

## Sources

- [IETF — draft-oauth-ai-agents-on-behalf-of-user-02](https://datatracker.ietf.org/doc/draft-oauth-ai-agents-on-behalf-of-user/)
- [CapiscIO — What WIMSE, OAuth & OWASP say about agent authorization](https://capisc.io/blog/what-ietf-wimse-oauth-and-owasp-actually-say-about-agent-authorization)
- [WorkOS — OAuth On-Behalf-Of flow for AI agents](https://workos.com/blog/oauth-on-behalf-of-ai-agents)
- [arXiv — AIP: Agent Identity Protocol](https://arxiv.org/pdf/2603.24775)
- [arXiv — Deterministic Pre-Action Authorization](https://arxiv.org/pdf/2603.20953)
- [Zylos — Agent Authentication & Delegated Access 2026](https://zylos.ai/research/2026-04-11-agent-authentication-delegated-access-oauth-scoped-tokens)
