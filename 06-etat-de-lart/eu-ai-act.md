# État de l'art — EU AI Act (règlement 2024/1689), détaillé (recherche web, juillet 2026)

## L'architecture du règlement : une pyramide de risques

✓ Le règlement (UE) 2024/1689 classe les systèmes d'IA par niveau de risque :

1. **Risque inacceptable** (article 5) — interdits : notation sociale, manipulation exploitant les vulnérabilités, reconnaissance des émotions au travail (sauf sécurité/médical), etc. ~ L'omnibus 2026 y ajoute les "nudifiers" (imagerie intime non consentie générée par IA) et le CSAM.
2. **Haut risque** (annexe III + annexe I) — autorisés sous obligations lourdes. **La catégorie "emploi" est en annexe III** : recrutement, sélection de candidats, évaluation de performance, allocation des tâches, surveillance des travailleurs, décisions de promotion/licenciement.
3. **Risque limité** — obligations de transparence (chatbots, deepfakes…).
4. **Risque minimal** — libre.

Plus un régime séparé pour les **modèles à usage général (GPAI)** : documentation, droit d'auteur, et obligations renforcées pour les modèles à "risque systémique".

## Le calendrier — ATTENTION, il vient de changer

- ✓ **2 février 2025** : interdictions (art. 5) + obligation de **maîtrise de l'IA** ("AI literacy", art. 4) — déjà applicables. L'art. 4 concerne toute organisation qui déploie de l'IA : former les personnes qui l'utilisent.
- ✓ **2 août 2025** : obligations GPAI — déjà applicables.
- ✓ **Le report omnibus (frais — juin 2026)** : le "Digital Omnibus" a été définitivement adopté (accord politique 7 mai 2026, Parlement 16 juin, Conseil 29 juin 2026). Les obligations **haut risque annexe III sont reportées du 2 août 2026 au 2 décembre 2027** (16 mois), et au 2 août 2028 pour l'IA embarquée dans les produits réglementés (annexe I). Publication au JO imminente au moment de cette recherche.
- ⚠ Conséquence : tout contenu écrit avant juin 2026 (y compris [jurisprudence-cse-ia-2026](./jurisprudence-cse-ia-2026.md)) citant "applicable août 2026" pour le haut risque est périmé — corrigé.
- ~ L'omnibus apporte aussi : usage élargi de données sensibles pour la détection de biais, rôle renforcé de l'AI Office, flexibilités étendues aux "small mid-caps", accès facilité aux sandboxes réglementaires.

## Les obligations du "déployeur" (article 26) — le cœur pour le BYOIA

L'entreprise qui *utilise* un système haut risque (le "deployer", par opposition au "provider" qui le construit) doit notamment :

- ✓ utiliser le système conformément à sa notice et assurer une **supervision humaine** effective (pas une déclaration d'intention — des contrôles opérationnels) ;
- ✓ conserver les **logs générés automatiquement** au moins six mois ;
- ✓ pour l'emploi : **informer les travailleurs et leurs représentants** avant la mise en service d'un système haut risque les concernant — la passerelle directe avec la [consultation CSE](../01-concepts/cadre-juridique-cse-consultation.md) ;
- ✓ réaliser une **analyse d'impact sur les droits fondamentaux (FRIA)** dans certains cas.
- ~ Sanctions : jusqu'à 35 M€ ou 7 % du CA mondial pour les pratiques interdites ; 15 M€ ou 3 % pour la plupart des autres violations (à re-vérifier sur le texte).

## Les questions que l'AI Act pose spécifiquement au BYOIA

1. **Qui est le déployeur quand le salarié apporte son IA ?** Le règlement exclut l'usage personnel non professionnel — mais un salarié qui utilise *son* IA *pour son travail* avec l'infrastructure de l'entreprise place très probablement l'employeur en position de déployeur. ⚠ Zone grise non tranchée par les textes trouvés — question juridique de fond pour le livre, à faire expertiser (recoupe la question 12 de [questions-livre](../00-meta/questions-livre.md)).
2. **La qualification dépend de l'usage, pas de l'outil** : le même harnais IA passe de "risque minimal" (préparer un brouillon) à "haut risque" (évaluer des dossiers RH). C'est un argument massif pour la [doctrine de la frontière](../05-questions-ouvertes/doctrine-frontiere-si-interface.md) : le test des cinq questions et la classification AI Act convergent — ce qui change l'état du domaine partagé (décisions RH, notations…) est précisément ce qui bascule en haut risque.
3. **L'infrastructure BYOIA fabrique la conformité** : logs de six mois → la traçabilité de la façade/gateway les produit nativement ; supervision humaine → le "préparer librement / acter par le SI" de la doctrine EST une supervision humaine par construction ; information des travailleurs → le [cycle CSE](./jurisprudence-cse-ia-2026.md). L'argument [conformité par design](../01-concepts/conformite-par-design.md) trouve ici sa substance réglementaire précise, article par article.
4. **L'obligation de maîtrise de l'IA (art. 4, déjà en vigueur)** est un cheval de Troie favorable : former les salariés à l'IA est obligatoire depuis février 2025 — autant les former à *bien* apporter leur IA plutôt qu'à s'en cacher.
5. **Le report à décembre 2027 est une fenêtre stratégique** : les obligations haut risque emploi arrivent, mais l'entreprise a 17 mois pour construire l'architecture qui les rendra triviales au lieu de les subir. Timing éditorial idéal pour un livre publié avant cette échéance.

## Sources

- [artificialintelligenceact.eu — Implementation Timeline](https://artificialintelligenceact.eu/implementation-timeline/)
- [Consilium — Council/Parliament agree to simplify rules (7 mai 2026)](https://www.consilium.europa.eu/en/press/press-releases/2026/05/07/artificial-intelligence-council-and-parliament-agree-to-simplify-and-streamline-rules/)
- [Gibson Dunn — EU AI Act Omnibus Agreement](https://www.gibsondunn.com/eu-ai-act-omnibus-agreement-postponed-high-risk-deadlines-and-other-key-changes/)
- [DLA Piper — Deferral of high risk AI obligations](https://knowledge.dlapiper.com/dlapiperknowledge/globalemploymentlatestdevelopments/2026/The-Digital-AI-Omnibus-Proposed-deferral-of-high-risk-AI-obligations-under-the-AI-Act)
- [Covington — Timeline Relief, Targeted Simplification, New Prohibitions](https://www.insideprivacy.com/artificial-intelligence/eu-ai-act-update-timeline-relief-targeted-simplification-and-new-prohibitions/)
- [Kiteworks — Prepare High-Risk Deployers](https://www.kiteworks.com/regulatory-compliance/eu-ai-act-deadline-compliance/)
- [CSA — High-Risk Deadline Pushed to December 2027](https://labs.cloudsecurityalliance.org/research/csa-research-note-eu-ai-act-omnibus-vii-deadline-delay-20260/)
