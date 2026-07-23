# Le harnais, enfin défini

*Phase 1 — Accroche · Article 6/38 · Publication prévue : jeudi 17 septembre 2026*

**Dépend de :** rien de spécifique, cet article se lit seul. Le mot est déjà apparu, informellement, dans l'article 3 — le voici précisément défini.
**Suite :** le harnais est défini. Reste à voir qui l'utilise, tous les jours, pour produire vite ce dont une équipe métier a besoin. (Article 7 : *Le développeur de terrain*)

---

## Ce livre appelle ça un harnais depuis l'article 3. OpenAI, Stripe et Thoughtworks viennent chacun, en quelques mois et sans se concerter, d'en publier leur propre définition.

### Le réflexe qu'on a tous eu

Toute étude de productivité IA publiée depuis deux ans part de la même hypothèse implicite : l'IA génère, un humain relit et valide à la main avant de merger. C'est le mode d'usage qu'on imagine par défaut quand on pense "assistant de code". C'est aussi, de plus en plus, un mode d'usage dépassé par ce que font réellement les équipes qui vont vite.

### Ce qu'un harnais désigne précisément

Le terme n'a pas été inventé par ce livre. Il circule dans le secteur depuis fin 2025 sous un raccourci devenu courant, popularisé notamment par un billet de [LangChain](https://blog.langchain.com/the-anatomy-of-an-agent-harness/) : agent égale modèle plus harnais. En avril 2026, [Thoughtworks](https://martinfowler.com/articles/harness-engineering.html) en publie la formalisation la plus complète à ce jour, sous la plume de Birgitta Böckeler. Un harnais combine des guides, qui orientent l'agent avant qu'il agisse, et des capteurs, qui observent après coup et le corrigent. Certains de ces contrôles sont computationnels : tests, analyseurs statiques, vérificateurs de types, rapides et déterministes. D'autres sont inférentiels : revue par un second modèle, jugement sémantique, plus lents et probabilistes. Un harnais, au sens où cette série l'emploie depuis l'article 3, c'est cette combinaison : tests générés, analyse statique, revue croisée, boucle de correction.

### Ce que le secteur construit déjà, chacun de son côté

Ce qui frappe n'est pas la définition. C'est que trois organisations concurrentes, sans se concerter, ont documenté la même pratique à quelques semaines d'intervalle. [OpenAI](https://openai.com/index/harness-engineering/) a construit en interne un produit entier sans une seule ligne de code écrite à la main : environ un million de lignes en cinq mois, 1 500 pull requests fusionnées par une équipe passée de trois à sept ingénieurs, un rythme de 3,5 PR par ingénieur et par jour. Ce qui rend ce rythme possible n'est pas le modèle. C'est une architecture en couches imposée mécaniquement par des linters et des tests structurels sur mesure, plus un processus récurrent que l'équipe appelle son "ramassage des ordures", qui traque la dérive du code au fil du temps.

Chez [Stripe](https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents), des agents internes surnommés "minions" produisent plus de mille pull requests par semaine, du début à la fin, avec la revue humaine comme dernier filtre plutôt que comme seule ligne de défense. Anthropic a publié, de son côté, sa propre note d'ingénierie sur la construction de harnais pour des agents qui tournent plusieurs heures sans interruption. Trois entreprises concurrentes, trois vocabulaires proches, la même architecture en dessous.

### Pourquoi ça compte maintenant

Le rapport [DORA 2025](https://dora.dev/research/2025/dora-report/) de Google Cloud tranche sur un point précis : l'IA joue avant tout un rôle d'amplificateur, elle grossit les forces et les faiblesses déjà présentes dans une organisation. Le retour sur investissement le plus élevé ne vient pas de l'outil IA lui-même, mais d'un travail stratégique sur le système organisationnel qui l'entoure. Un harnais est exactement ce système, appliqué à la ligne de production du code. Une équipe qui en a un voit l'amplification jouer en sa faveur, au rythme de 3,5 pull requests par ingénieur et par jour chez OpenAI. Une équipe qui n'en a pas voit l'IA amplifier ses angles morts existants, ce que l'article 3 de cette série documentait déjà avec la triche sur les tests.

### Ce que ça change concrètement

Le harnais ne supprime pas le coût de validation. Il en automatise l'exécution, pas le jugement. OpenAI résume l'idée en une phrase : les humains pilotent, les agents exécutent. Le travail d'ingénieur ne disparaît pas, il change de niveau. Designer des environnements, spécifier des intentions, construire des boucles de feedback, plutôt qu'écrire chaque ligne à la main.

La responsabilité, elle, reste attachée à qui pilote ce harnais, pas à l'agent qui produit dedans. Un dispositif qui repère qu'un test a été affaibli, qu'une couche architecturale a été violée, ou qu'une pull request dérive du principe qu'elle devait suivre, ne remplace jamais ce jugement humain. Il le rend simplement exerçable à l'échelle à laquelle les agents produisent désormais.

---

## Sources & vérification

*(Article produit le 19/07. Recherche approfondie menée pour remplacer la référence vague du fichier maître ("cohérent avec le verdict DORA 2025") par des citations directes et datées. Trois découvertes notables : (1) le terme "harnais" est un raccourci sectoriel réel et daté ("agent = modèle + harnais"), popularisé par LangChain fin 2025 puis formalisé en détail par Thoughtworks en avril 2026, ce qui confirme la directive de ne pas se l'attribuer ; (2) OpenAI et Stripe ont chacun publié, début 2026, un compte-rendu détaillé et chiffré de leur propre harnais de production, avec des chiffres vérifiables directement sur leurs sites ; (3) le rapport DORA 2025 confirme mot pour mot, en accès libre sur dora.dev, l'idée que l'IA amplifie l'existant plutôt qu'elle ne le corrige. Vigilance biais pro-Anthropic appliquée : Anthropic n'est mentionnée qu'une fois, brièvement, au même niveau qu'OpenAI et Stripe, sans mise en avant ni minimisation.)*

- LangChain, *The Anatomy of an Agent Harness* (blog, fin 2025), origine du raccourci "agent = modèle + harnais" ~ (relayé via la citation qu'en fait Thoughtworks, page non consultée directement) — https://blog.langchain.com/the-anatomy-of-an-agent-harness/
- Thoughtworks / Martin Fowler, *Harness engineering for coding agent users*, par Birgitta Böckeler (publié le 2 avril 2026) ✓ (consulté directement) — https://martinfowler.com/articles/harness-engineering.html
- OpenAI, *Harness engineering: leveraging Codex in an agent-first world*, par Ryan Lopopolo (publié le 11 février 2026) ✓ (consulté directement, tous les chiffres vérifiés sur la page : ~1 million de lignes en 5 mois, 1 500 PR fusionnées, équipe de 3 à 7 ingénieurs, 3,5 PR/ingénieur/jour) — https://openai.com/index/harness-engineering/
- Stripe, *Minions: Stripe's one-shot, end-to-end coding agents*, par Alistair Gray (publié le 9 février 2026) ✓ (description et chiffre clé — plus de 1 000 PR fusionnées par semaine — confirmés sur la page ; le corps détaillé de l'article n'a pas pu être entièrement chargé, à revérifier avant citation approfondie) — https://stripe.dev/blog/minions-stripes-one-shot-end-to-end-coding-agents
- Anthropic, note d'ingénierie sur les harnais pour agents longue durée ~ (relayée via la citation de Thoughtworks, page non consultée directement) — https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents
- DORA (Google Cloud), *State of AI-assisted Software Development 2025* : "AI's primary role is as an amplifier, magnifying an organization's existing strengths and weaknesses" ✓ (citation confirmée directement sur dora.dev) — https://dora.dev/research/2025/dora-report/
