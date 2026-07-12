# État de l'art — InnerSource, golden paths et promotion d'outils internes (recherche web, juillet 2026)

## Le cycle de promotion a des précédents industriels

- ✓ **Backstage** (Spotify 2016, open-sourcé 2020, CNCF) est lui-même un cas de promotion réussie : outil interne → open source → standard de facto des developer portals. Méta-exemple utilisable tel quel pour le [cycle de promotion](../01-concepts/cycle-promotion-specifique.md).
- ✓ **Golden paths** (platform engineering) : chemins outillés, opinionated et documentés pour construire au standard de l'organisation — c'est la couche "mise à disposition de l'outil" du cycle, avec templates (Backstage Software Templates) comme mécanisme concret. Exemple d'adoption : Toyota Motors North America.
- ✓ **InnerSource** : pratiques open source appliquées en interne (réutilisation, contribution inter-équipes, ownership) — le modèle social du transfert de maintenance existe et a une communauté (InnerSource Commons).
- ✓ Constat récurrent de la littérature platform engineering : **l'adoption par décret sous-performe l'adoption volontaire** — une plateforme assez utile pour être choisie bat une plateforme imposée. Converge exactement avec l'uniformisation a posteriori (sélection par l'usage) du cycle de promotion.

## Lecture critique pour la série

1. Le cycle de promotion n'est pas une spéculation : c'est la généralisation aux **outils générés par les utilisateurs** de ce que le platform engineering fait déjà pour les outils des développeurs. Formulation possible : "le BYOIA étend le golden path au-delà de la DSI".
2. Ce qui reste original dans la série : la **descente comme opération de premier ordre** et la **fenêtre de complexité**. La littérature golden paths parle beaucoup de montée, très peu d'élagage. Contribution à revendiquer.
3. Les métriques d'utilisation comme déclencheur de promotion : Backstage a déjà la mécanique (catalogue + scorecard) — le livre peut citer l'outillage existant au lieu d'inventer.

## Sources

- [platformengineering.org — Golden paths that actually go somewhere](https://platformengineering.org/blog/how-to-pave-golden-paths-that-actually-go-somewhere)
- [Red Hat — What is a golden path](https://www.redhat.com/en/topics/platform-engineering/golden-paths)
- [Mia-Platform — Golden Paths](https://mia-platform.eu/blog/golden-paths-platform-engineering/)
- [DevelopersVoice — Platform Engineering Handbook (Backstage)](https://developersvoice.com/blog/technology/building_net_platform_backstage_azure/)
