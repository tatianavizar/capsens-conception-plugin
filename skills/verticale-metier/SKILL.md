---
name: verticale-metier
description: >
  Charge le vocabulaire, les règles métier récurrentes et les risques types d'une verticale
  (ex : fintech) pour une mission de conception Capsens. Le plugin reste agnostique : ce skill
  n'apporte du contenu que si un fichier existe pour la verticale. Déclencher quand le
  CLAUDE.md ou la Synthèse du projet indique une verticale, quand un autre skill du plugin
  le demande, ou quand le CDP dit : "charge la verticale [domaine]", "vocabulaire [domaine]",
  "règles [fintech/…]", "c'est un projet [domaine]", ou équivalent.
---

# Verticale métier

Apporte le savoir métier d'une verticale : vocabulaire, règles récurrentes d'un projet à
l'autre, questions à poser en workshop, risques et cas limites typiques.

## Étape 1 — Identifier la verticale

Dans l'ordre :
1. La verticale demandée explicitement par le CDP
2. La ligne `Verticale :` du `CLAUDE.md` du projet
3. La ligne `Verticale :` de `00_Reference/[PROJET]_Synthese.md`

Si aucune verticale n'est renseignée, ne charge rien et continue sans.

## Étape 2 — Charger le fichier de la verticale

Lis `references/[verticale].md` (nom en minuscules, ex : `references/fintech.md`).

Verticales disponibles :
- `fintech` — crowdfunding, investissement, paiement, épargne

Si aucun fichier n'existe pour la verticale : dis-le en une ligne au CDP et continue sans.
N'invente pas de règles de domaine.

## Comment utiliser le contenu

- **Vocabulaire** : utilise les termes exacts du domaine dans les livrables.
- **Règles récurrentes** : ce sont des points à **vérifier** avec le client, pas des décisions.
  Une règle n'entre dans un brief que si elle est actée dans la mémoire projet (`Dn`) ;
  sinon elle devient une question en suspens.
- **Réglementaire** : Capsens signale, le client décide. Chaque point réglementaire est
  présenté comme "à confirmer par le client / son juriste", jamais comme un avis juridique.
  Les seuils et dates évoluent : les citer avec la date du fichier de référence.
- **Risques types** : à passer en revue en fin de brief (`write-brief`), en préparation de
  workshop (`workshop-prep`) et en audit (`consistency-check`) — ne retenir que ceux qui
  s'appliquent vraiment à la feature, aucun si aucun ne s'applique. Dans un brief, seul le
  comportement attendu va dans le tableau des cas limites (ou "À définir → Qn").

## Ajouter une verticale

Créer `references/[verticale].md` avec les mêmes sections que `fintech.md` : Vocabulaire,
Règles récurrentes, Questions à poser en workshop, Risques types. N'y mettre que ce qui
s'est vérifié sur au moins deux projets, sans nom de client.
