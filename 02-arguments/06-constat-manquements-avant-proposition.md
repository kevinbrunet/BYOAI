# Le constat des manquements avant la proposition — ce que la plupart ne voit pas

## Le principe rhétorique

Ne pas ouvrir par la proposition (BYOIA). Ouvrir par ce que tout le monde croit — cité textuellement — puis montrer ce que ces croyances ne voient pas. La proposition n'arrive qu'après, comme réponse aux trous constatés. Deux effets : le lecteur se reconnaît dans les citations (elles sont partout sur LinkedIn), et la proposition ne semble plus sortie de nulle part — elle comble des manques que le lecteur vient de voir.

Structure type d'un chapitre/post : **citation de la croyance → ce qu'elle voit juste → ce qu'elle ne voit pas → ce que ça exige (la proposition)**.

## Les croyances populaires — citations vérifiées

- ✓ *"The hottest new programming language is English."* — Andrej Karpathy, tweet, janvier 2023. Et ✓ le même a forgé **"vibe coding"** (février 2025) : coder en acceptant ce que l'IA produit sans lire le diff.
- ✓ *"Everyone is a programmer now — you just have to say something to the computer."* — Jensen Huang (CEO Nvidia), keynote Computex, mai 2023 ([CNBC](https://www.cnbc.com/2023/05/30/everyone-is-a-programmer-with-generative-ai-nvidia-ceo-.html)).
- ✓ *"AI won't take your job. It's somebody using AI that will take your job."* — Richard Baldwin (économiste), WEF Growth Summit, mai 2023 ([WEF](https://www.weforum.org/press/2023/05/growth-summit-2023-job-creation-and-reskilling-must-be-central-to-growth-in-the-age-of-uncertainty-advancing-ai-and-the-green-transition/)). Souvent citée sans attribution — c'est devenu un proverbe d'entreprise.
- ✓ *"Thin harness, fat skills."* — Garry Tan (CEO Y Combinator), doctrine du skill pack GStack.
- ~ *"Code should be regenerated, not maintained."* — mouvement spec-driven (Codeplain, relayé The New Stack) — déjà traité dans [logiciel malléable/jetable](../06-etat-de-lart/logiciel-malleable-jetable.md).
- ⚠ Croyances du discours praticien anonyme (ex. [guide "Coder avec l'IA"](../06-etat-de-lart/guide-coder-avec-ia-pratiques-harnais.md), auteur non identifié) — citables comme *symptômes* du discours ambiant, pas comme autorités : *"la qualité d'un agent dépend à 90 % de son contexte, à 10 % de son modèle"* ; *"IA plus autonome = moins de travail pour moi"* (que ce guide réfute d'ailleurs lui-même) ; *"ne pas connaître MCP = avoir deux ans de retard"* ; *"arrêtez de lire, commencez à livrer"*.

## Ce que ces croyances voient juste

Le coût de production du code s'effondre ; la formalisation en langage naturel devient l'actif ; l'avantage se déplace vers celui qui pilote. Sur tout ça, le discours dominant a raison — inutile de le combattre, il faut le prendre au mot.

## Le constat des manquements — ce que la plupart ne voit pas

Chaque manquement renvoie à la fiche qui le développe :

1. **Qui répond de ce qui sort ?** "Everyone is a programmer" — mais programmer n'a jamais été le problème ; *répondre de* ce qu'on met en production, si. Aucune des citations ne parle de responsabilité → [responsabilité du pilote](../01-concepts/responsabilite-pilote-diversite-harnais.md).
2. **Sous quelle identité l'agent agit-il ?** Le discours praticien branche des agents sur tout (MCP partout) sans jamais poser la question de la délégation d'identité et de la traçabilité de la chaîne `act` → [délégation JWT/mTLS](../01-concepts/delegation-agents-jwt-mtls.md).
3. **Le coût ne disparaît pas, il se déplace en aval.** Production ÷ 10, mais validation, revue, maintenance restent — et le vibe coding les gonfle → [déplacement du coût en aval](../04-objections/deplacement-cout-aval.md), [méta-analyse](../06-etat-de-lart/meta-analyse-cout-aval.md).
4. **Qui maintient quand ça se partage ?** "Everyone is a programmer" produit des artefacts individuels ; dès qu'un collègue s'y fie, quelqu'un doit maintenir et répondre — mécanisme que personne ne décrit → [cycle de promotion](../01-concepts/cycle-promotion-specifique.md).
5. **La monoculture de l'outil béni.** La réponse réflexe des DSI ("un outil validé pour tous") installe un angle mort unique partagé par toute l'entreprise → diversité des harnais, [même fiche que 1](../01-concepts/responsabilite-pilote-diversite-harnais.md).
6. **Où s'arrête le droit de bricoler ?** Aucune doctrine de frontière entre ce que l'individu peut générer et ce qui appartient au SI → [doctrine frontière SI/interface](../05-questions-ouvertes/doctrine-frontiere-si-interface.md).
7. **Le droit du travail existe.** Outiller les salariés d'agents modifie l'organisation du travail — consultation CSE, AI Act art. 26 : absents de 100 % du discours praticien → [cadre CSE](../01-concepts/cadre-juridique-cse-consultation.md), [EU AI Act](../06-etat-de-lart/eu-ai-act.md).

Le pattern d'ensemble : **le discours dominant outille l'individu et laisse la gouvernance vide.** C'est vrai du malleable software (agency sans conformité), du guide praticien (harnais sans responsabilité), des keynotes (démocratisation sans maintenance). Les manquements ne sont pas des oublis indépendants — c'est le même trou vu de sept angles : personne ne pense l'*insertion organisationnelle*.

## Le pivot vers la proposition

Une fois les sept manquements posés, le BYOIA se présente non comme une idée de plus, mais comme la réponse structurée : chaque manquement correspond à un composant du modèle (frontière fiduciaire, cycle de promotion, délégation d'identité, diversité des harnais, conformité par design). La proposition est la table des matières inversée du constat.

## Généralisation — la méthode à chaque étage

Décision Kevin (2026-07-15) : cette structure ne vaut pas que pour l'ouverture — elle s'applique à chaque chapitre, dans les deux sens (périmètre de la croyance d'en face + risques/mitigations de la facette BYOIA proposée). Voir la [grille périmètre/risques par chapitre](../00-meta/grille-perimetre-risques-par-chapitre.md).

## Liens

- [Objectif de la série](../00-meta/objectif-serie.md) — ce fichier fixe l'ordre d'exposition, pas le contenu
- [BYOIA](../01-concepts/byoia.md) — la proposition elle-même
- [Guide "Coder avec l'IA"](../06-etat-de-lart/guide-coder-avec-ia-pratiques-harnais.md) — corpus de croyances praticiennes citables
