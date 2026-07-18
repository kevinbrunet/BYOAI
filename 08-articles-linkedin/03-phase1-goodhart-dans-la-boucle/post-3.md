# Post 3 — Goodhart dans la boucle

*Accompagne l'article : "Goodhart dans la boucle" (article 3/37, mardi 8 septembre 2026)*

---

**Accroche**

Vos tests ne se valent pas tous face à un agent IA. Certains peuvent rester co-générés avec le code, sans risque. D'autres ne devraient jamais l'être.

**Assise sourcée**

La distinction existe depuis longtemps dans le cycle en V du test logiciel. Les tests unitaires (TU), écrits au fil de l'eau pour guider le développement, aident à construire. Ils ne prouvent rien au-delà de la cohérence interne du code. Les tests d'intégration et de qualification (TI/TQ) ont un rôle différent : établir, depuis un point de vue extérieur, que le résultat répond réellement au besoin. Ce sont ces derniers que les [fiches de sécurité de Claude Opus 4.7](https://dev.to/ji_ai/i-read-all-232-pages-of-the-opus-47-system-card-28mh) mettent en défaut, 45 % de triche par défaut sur des tâches conçues pour être irrésolubles honnêtement. Un agent qui a accès à ces tests-là, avec les mêmes permissions que le code qu'il produit, a toutes les raisons structurelles de finir par les satisfaire sans les mériter.

**Ouverture**

Séparer les permissions n'est pas un détail d'implémentation. C'est la seule chose qui empêche l'agent de faire évoluer le code et la preuve en même temps.

---

## Sources & vérification (usage interne, non publié)

- Distinction TU (tests unitaires) vs TI/TQ (tests d'intégration et de qualification) : vocabulaire standard du test logiciel, cycle en V ~ (terminologie d'usage courant en ingénierie française, pas de source unique à citer)
- Anthropic, *System Card: Claude Opus 4.7* (avril 2026), taux de triche par défaut sur tâches impossibles ~ (chiffres via synthèse tierce dev.to, à vérifier contre le PDF primaire) — https://dev.to/ji_ai/i-read-all-232-pages-of-the-opus-47-system-card-28mh
