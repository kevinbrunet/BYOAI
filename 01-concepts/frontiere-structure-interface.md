# Frontière structure / interface

## Le principe transversal

L'entreprise ne possède pas des outils. Elle possède une mémoire, des garanties, et une coordination. Les logiciels de gestion existent pour quatre raisons précises :

1. capitaliser la connaissance et les pratiques
2. garantir le respect de processus et de réglementations
3. faciliter l'accès à l'information et accompagner la tâche
4. conserver une mémoire organisationnelle qui survive à la rotation des personnes sur un même poste

## Pourquoi l'entreprise imposait l'outil jusqu'ici

Trois raisons rationnelles :

- **échange d'information** : un référentiel commun évite la fragmentation
- **sécurité** : une stack maîtrisée est une stack auditable
- **économie d'échelle** : mutualiser le développement divise le coût par le nombre d'utilisateurs

## Comment l'IA brouille (et redessine) la frontière

L'IA ne fait pas disparaître le besoin de généricité, elle déplace la frontière de ce qui doit rester générique. Voir [générique vs spécifique](./generique-vs-specifique.md).

La frontière proposée :

- **Structure (reste centralisée)** : données, règles de gestion, cohérence transverse, conformité réglementaire, exposée via API — voir [approche data-centrique](./approche-datacentrique.md)
- **Interface (redevient individuelle)** : la façon dont chacun consomme ces API au quotidien, construite et administrée par l'IA de chacun — voir [BYOIA](./byoia.md)

## Où ça coince (à trancher)

Cette frontière est nette dans la théorie mais floue en pratique dès que l'IA touche potentiellement aux deux couches (génère aussi du code côté SI). Voir [frontière SI/interface si l'IA génère du code des deux côtés](../04-objections/frontiere-si-ia-genere-code.md) et [arbitrage règle de gestion vs interface](../04-objections/arbitrage-regle-gestion-vs-interface.md).

## Écho organisationnel

Cette séparation structure/organe de production a déjà été théorisée il y a quinze ans par l'holacratie, au niveau organisationnel plutôt que technique. Voir [parallèle holacratique](./holacratie-parallele.md).
