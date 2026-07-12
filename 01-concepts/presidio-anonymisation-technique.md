# Presidio — fonctionnement technique de l'anonymisation

## Ce qui est connu avec confiance

✓ Développé par Microsoft, open source, disponible sur GitHub. Conçu explicitement pour la détection et l'anonymisation de PII dans du texte libre et des images.

✓ Architecture en deux composants principaux :

- **Presidio Analyzer** — détecte les entités (noms, emails, numéros de téléphone, IBAN, etc.) via une combinaison de NER (spaCy par défaut) + règles regex + context-aware scoring.
- **Presidio Anonymizer** — applique la transformation sur les entités détectées : suppression, remplacement, hachage, chiffrement, ou fake data via Faker.

✓ Supporte l'ajout de recognizers custom — on peut écrire des règles métier spécifiques (ex : détecter un identifiant patient interne, un numéro de dossier, un code service).

✓ Le scoring de confiance par entité est exposé — on peut choisir un seuil au-dessus duquel l'anonymisation s'applique.

## Ce qui est plus incertain

~ Qualité du NER français — spaCy a des modèles français mais leur performance sur du texte médical ou métier dense est variable. Aucun benchmark sérieux identifié sur ce cas précis.

~ Le risque de ré-identification sur du texte libre complexe — Presidio détecte ce qu'il reconnaît, pas ce qu'il ne reconnaît pas. Les entités implicites ou contextuelles passent à travers.

## Le vrai problème architectural pour le BYOIA : la reconstruction en sens inverse

Si on remplace "Jean Dupont" par "PERSON_1" avant envoi au LLM, la réponse contient "PERSON_1" — il faut remapper pour restituer quelque chose d'utile à l'utilisateur. Ça implique de garder une table de mapping en mémoire le temps de la session, ce qui crée un état à gérer côté proxy.

**Conséquence directe : le proxy n'est plus stateless.** C'est un changement d'architecture non trivial — voir comment d'autres outils (PII Shield, SovereignGuard) traitent ce même problème dans [gateways de sécurisation LLM](../03-exemples/gateways-securisation-llm.md).

## Lien avec le reste de la série

Cette contrainte de statefulness rejoint la remarque déjà faite sur [délégation d'identité pour agents](./delegation-agents-jwt-mtls.md) : dès qu'un composant d'infrastructure doit porter une mémoire de session (mapping PII, chaîne de délégation), il cesse d'être un simple filtre neutre et devient une pièce d'état à sécuriser et à faire évoluer à part entière.
