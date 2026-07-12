# État de l'art — Logiciel malléable, personnel et jetable (recherche web, juillet 2026)

## Le courant "malleable software" — le cousin intellectuel du BYOIA

- ✓ **Geoffrey Litt** (ex-Ink & Switch, aujourd'hui Notion, PhD MIT) est la référence du domaine. Essai fondateur : *"Malleable software in the age of LLMs"* (mars 2023) — les LLM comme technologie manquante de l'end-user programming.
- ✓ **Ink & Switch** a publié en 2025 l'essai *"Malleable software: Restoring user agency in a world of locked-down apps"* (Litt, Horowitz, van Hardenberg, Matthews) — l'utilisateur doit pouvoir remodeler ses outils à l'exécution, sans attendre l'éditeur.
- ✓ Le terme "malleable software" a été forgé par Philip Tchernavskij (2019), étendu par Litt (2023).
- ✓ La métaphore de Litt : le logiciel devrait ressembler à une "cuisine de maison" (home kitchen) — outils qu'on arrange à sa main — plutôt qu'à un restaurant où on subit le menu. Très proche de la [captivité logicielle](../01-concepts/captivite-logicielle-happy-path-social.md) et des recettes de cuisine — la convergence de vocabulaire est frappante et exploitable.

### Contenu détaillé de l'essai Ink & Switch (juin 2025, lu en source)

- ✓ Structure de l'argument : les humains adaptent naturellement leurs environnements ; le logiciel de masse est trop rigide ; les approches existantes (settings, plugins, modding, open source, codage assisté par IA) sont toutes insuffisantes seules.
- ✓ Concepts clés : **"gentle slope from user to creator"** (pente douce de l'utilisateur au créateur — pas de falaise entre utiliser et modifier) ; **"tools, not apps"** avec la formule *"apps are avocado slicers"* (l'app = gadget monofonction imposé, vs l'outil composable) ; partage de données entre outils ; composition de l'interface par l'utilisateur ; **création communautaire** (communal creation).
- ✓ Prototypes Ink & Switch : Pushpin (canvas extensible), Cambria (compatibilité de schémas entre outils), Farm ("code is data"), Patchwork (version control), Potluck (documents dynamiques — recettes), Embark (planification de voyage).
- ✓ Généalogie : "situated software" (Clay Shirky, 2004) ; *"An app can be a home-cooked meal"* (Robin Sloan, 2020) — l'app cuisinée maison pour sa famille.

**Positionnement pour le livre** : le courant malleable software pense l'*individu* (agency, outils personnels) mais traite peu l'*entreprise* (conformité, traçabilité, mutualisation). Le BYOIA est essentiellement "malleable software + gouvernance d'entreprise" — la frontière fiduciaire et le cycle de promotion sont exactement ce qui manque à ce courant pour entrer dans l'organisation. Citer Litt, se positionner comme le versant organisationnel.

## Le débat "logiciel jetable / régénérable" — l'argument existe déjà, et sa critique aussi

- ✓ Le concept de **disposable/ephemeral software** est un débat actif : applications générées à la demande, détruites après usage ; "le code cesse d'être un actif".
- ✓ **Spec-driven development** : la spécification devient l'artefact durable, le code devient jetable — *"Code should be regenerated, not maintained"* (Codeplain, relayé par The New Stack). Converge avec le [cycle de promotion](../01-concepts/cycle-promotion-specifique.md) (jetable en bas, pérenne en haut) et avec DCB (la décision comme artefact durable, pas le code).
- ✓ **La critique structurée existe** : *"The Flawed Ephemeral Software Hypothesis"* (Andreas Kirsch) — les données d'usage réelles (Cursor, Copilot, YC) montrent du code produit plus vite *dans des workflows durables* (PR, CI, Git, review), pas du code jetable ; les systèmes critiques/régulés continueront d'exiger la discipline classique. À lire et à traiter : c'est l'objection sérieuse au versant "jetable" du cycle de promotion.

**Ce que la série apporte au débat** : les deux camps s'opposent en bloc (tout jetable vs rien jetable). Le cycle de promotion + la doctrine de la frontière donnent le critère de partage que le débat n'a pas : jetable tant que personne d'autre ne s'y fie, durable dès que promu. Position médiane argumentée — c'est une contribution.

## Sources

- [Geoffrey Litt — Malleable software in the age of LLMs](https://www.geoffreylitt.com/2023/03/25/llm-end-user-programming.html)
- [Ink & Switch — Malleable software (2025)](https://www.inkandswitch.com/essay/malleable-software/)
- [Dialectic — Geoffrey Litt, Software You Can Shape](https://jacksondahl.com/dialectic/geoffrey-litt)
- [The New Stack — Codeplain, spec-driven regenerative code](https://thenewstack.io/codeplain-spec-driven-regenerative-code/)
- [Andreas Kirsch — The Flawed Ephemeral Software Hypothesis](https://www.blackhc.net/essays/future_of_software/)
- [HarrisonAIX — Disposable Software](https://harrisonaix.com/blog/disposable-software-code-asset/)
- [Medium — The Rise of Ephemeral Software Engineering](https://medium.com/@zhiminzhao/when-code-becomes-cheaper-than-debugging-the-rise-of-ephemeral-software-78b210aadb9d)
