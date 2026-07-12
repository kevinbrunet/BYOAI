# Délégation d'identité pour agents IA — séparer transport et application

## Pourquoi ce concept est pertinent pour BYOIA

Le [BYOIA](./byoia.md) pose l'exigence d'une "facade MCP" et d'une "allowlist de modèles (OAuth 2.1)" pour gouverner ce à quoi l'IA personnelle d'un collaborateur a réellement accès. Ce fichier détaille un mécanisme technique concret qui répond à cette exigence : comment autoriser un agent IA à agir *pour le compte de* quelqu'un, sans lui donner l'identité complète de cette personne, et sans perdre la traçabilité de la chaîne de délégation.

## Le principe central : deux couches indépendantes, deux questions différentes

Un agent IA qui appelle des services au nom d'un utilisateur pose deux questions distinctes, qui doivent être vérifiées séparément :

- **mTLS (transport)** : "quel service m'appelle ?" — identité d'infrastructure.
- **JWT (application)** : "pour le compte de qui ?" — chaîne de délégation utilisateur → agent.

~ Un service compromis ne peut pas forger le JWT, et un JWT volé ne peut pas contourner le mTLS — les deux vérifications sont indépendantes. *(Marqueur ~ : principe cohérent avec l'architecture décrite, mais garantie à valider dans une implémentation réelle plutôt qu'à prendre comme acquis.)*

Important : SPIFFE/SPIRE (mTLS) ne fait qu'authentifier le service qui porte la requête à un saut donné — il ne sait rien de la chaîne de délégation logique. C'est le JWT imbriqué qui porte cette information, indépendamment du transport.

## Le mécanisme de délégation : claim `act` imbriqué

Chaque saut de délégation ajoute une couche `act` dans le JWT plutôt que de remplacer l'information précédente :

```json
{
  "sub": "summarizer-tech",
  "act": {
    "sub": "alice",
    "act": { "...": "et ainsi de suite si multi-sauts" }
  }
}
```

Chaque service qui reçoit ce JWT peut remonter toute la chaîne de délégation, pas juste le dernier maillon — ce qui permet de répondre à "qui a initié cette action" même après plusieurs sauts agent-à-agent.

✓ Ce mécanisme s'appuie sur la RFC 8693 (Token Exchange), spec IETF finalisée. ⚠ Son implémentation native dans Keycloak avec claim `act`/délégation complète reste, à la date de la conversation source, en discussion GitHub ouverte — pas out-of-the-box.

## Le calcul d'autorisation : intersection sur toute la chaîne, pas sur le dernier maillon

Point le plus important, et différence structurelle avec le RBAC classique : la décision d'autorisation se fait contre la chaîne de délégation complète, pas juste contre le dernier maillon. Même si l'agent final détient un token valide reçu via la chaîne, si un maillon intermédiaire (l'utilisateur d'origine ou un agent) n'a pas le droit demandé, la requête est refusée. C'est une intersection appliquée à toute la chaîne, pas juste user↔agent final — impossible à reproduire avec du RBAC traditionnel sans connaître le chemin à l'avance.

### Cas concrets illustrant l'intersection

- Accès direct : utilisateur accède à une ressource de son périmètre → autorisé.
- Agent sans délégation : agent générique accède à une ressource sans contexte utilisateur → refusé.
- Accès délégué : utilisateur délègue à un agent scopé sur le bon périmètre → autorisé.
- **Réduction de permission** (cas le plus révélateur) : l'utilisateur a le droit d'accéder à la ressource, mais délègue à un agent qui n'a pas ce droit dans sa propre configuration → refusé, malgré les droits de l'utilisateur. L'intersection coupe dans les deux sens.
- Cross-scope : deux identités différentes, mêmes droits sur une ressource partagée → autorisé.

## La nature de l'appelant : humain ou agent — et les API interdites à l'IA

Ajout (2026-07-11). La chaîne `act` dit *qui* a délégué à *qui*. Il faut y ajouter une information de nature : **chaque maillon déclare s'il est un humain ou un agent**. La structure de la chaîne le permet déjà (le `sub` final est l'initiateur, les couches `act` sont les intermédiaires), mais l'API réceptrice doit pouvoir le vérifier sans ambiguïté — typage explicite de chaque acteur de la chaîne (humain authentifié vs workload/agent), pas une convention de nommage.

Ce que ça rend possible : des **API interdites à l'IA**. Une politique d'autorisation à trois régimes par endpoint :

1. **Ouvert** — humain ou agent délégué, indifférent (lectures, projections).
2. **Agent autorisé sous délégation** — l'agent peut appeler si la chaîne est valide et l'intersection des droits le permet (écritures ordinaires).
3. **Humain uniquement** — l'endpoint refuse tout appel dont l'initiateur direct n'est pas un humain authentifié, même avec une chaîne de délégation valide. L'IA peut tout préparer en amont, mais le clic final est humain, et prouvablement humain.

Le troisième régime est le verrou technique de deux choses à la fois :

- **la doctrine** ([frontière fiduciaire](../05-questions-ouvertes/doctrine-frontiere-si-interface.md)) : "l'IA prépare, l'humain acte" cessait d'être un vœu de gouvernance — c'est l'API qui refuse. Réponse partielle à la question restée ouverte "frontière organisationnelle ou technique ?" : technique, dans la couche d'autorisation.
- **la supervision humaine de l'AI Act** ([art. 26](../06-etat-de-lart/eu-ai-act.md)) : pour les actions à haut risque (rejeter un candidat, valider un licenciement), la supervision humaine n'est pas un processus documenté mais une propriété vérifiable du système — le log de l'endpoint prouve que chaque décision haut risque a été actée par un humain. Conformité par construction, démontrable à l'audit.

Points de vigilance :

- ⚠ **Le problème du "human-washing"** : si l'humain se contente de cliquer "OK" sur tout ce que l'IA prépare, le régime 3 est satisfait techniquement mais vide de sens (rubber-stamping — c'est exactement la critique classique de la supervision humaine). Le verrou technique est nécessaire, pas suffisant ; le livre doit le dire.
- ⚠ Prouver que l'appelant est un humain et pas un agent qui pilote son navigateur est un problème non trivial (l'agent peut cliquer aussi). Pistes : authentification forte au moment de l'acte (re-authentification, passkey/WebAuthn avec user presence), pas seulement session ouverte. À creuser dans la cartographie de maturité.

## Où ça se loge dans l'architecture : couche infrastructure, pas applicative

Le choix de design clé est de placer la traduction transport → application dans la couche infrastructure (un sidecar qui intercepte la requête), pas dans le code métier de l'agent. Le service applicatif ne fait pas lui-même l'échange de token — l'infrastructure s'en charge de manière transparente. C'est le principe "auth-unaware" : le collaborateur (ou son IA) consomme une identité déjà vérifiée, sans avoir à implémenter la vérification lui-même.

Voir l'exemple complet d'implémentation : [Kagenti / AuthBridge (Red Hat)](../03-exemples/kagenti-authbridge-red-hat.md).

## Portée et limites

Ce mécanisme reste, à la date de la conversation source, majoritairement de la R&D upstream documentée (articles techniques, démo, discussion GitHub ouverte) plutôt qu'un produit livré et éprouvé en production. Voir la cartographie complète de maturité : [cartographie de maturité des méthodes d'authentification](../05-questions-ouvertes/cartographie-maturite-authentification.md).
