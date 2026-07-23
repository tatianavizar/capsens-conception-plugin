---
name: workshop-debrief
description: >
  Transforme un workshop en CR structuré et met à jour toute la mémoire projet.
  Peut récupérer automatiquement la transcription depuis tl;dv si configuré.
  Déclencher quand le PM dit : "je rentre du workshop", "CR workshop [N]", "compte-rendu
  [sujet]", "voici mes notes de la session", "on vient de finir l'atelier", "rédige le CR",
  "debrief workshop", "le meeting tldv de ce matin", ou quand des notes brutes de réunion
  sont partagées — avec ou sans lien/ID tl;dv.
---

# Workshop Debrief

Transforme un workshop en CR structuré et met à jour toute la mémoire projet.
Utilise tl;dv automatiquement si le connecteur est disponible — sinon travaille sur notes brutes.

## Étape 1 — Obtenir la matière première

### Si tl;dv est disponible (connecteur configuré)

Utilise le skill **`fetch-transcript`** pour récupérer et formater la transcription.
Ce skill gère la liste des réunions, la confirmation, la récupération et le format PMO.

La sortie de `fetch-transcript` (Résumé + Actions + Points d'accord + Hypothèses + Questions)
devient ta matière première pour les étapes suivantes.

### Si tl;dv n'est pas configuré ou que le PM préfère les notes brutes

Travaille à partir des notes collées par le PM. Demande-les si elles ne sont pas dans le message.

## Étape 2 — Charger le contexte projet

Lis ces fichiers pour avoir le fil du projet :
- `00_Reference/[PROJET]_Memoire.md`
- La trame du workshop si elle existe dans `04_Workshops/Trames/`
- Les briefs fonctionnels des features abordées (pour identifier les impacts)

## Étape 3 — Rédiger le CR

Structure exacte à produire :

```markdown
# CR Workshop [N] — [Thème principal]

**Date** : [date]
**Participants** : [liste]
**Durée** : [durée effective]
**PM** : [nom]
**Source** : [Notes PM / Transcription tl;dv / Les deux]

## Objectifs initiaux vs atteints

| Objectif | Atteint ? | Note |
|----------|-----------|------|

## Décisions actées

1. **[Décision en gras]** — [contexte court]
2. **[Décision]** — [contexte]

## Sujets abordés

### [Sujet 1]
[Synthèse : ce qui a été dit, les tensions éventuelles, la conclusion]

## Points ouverts

| Point ouvert | Impact | Décision prévue | Responsable | Deadline |
|--------------|--------|----------------|-------------|---------|

## Implications produit

| Brief impacté | Nature de l'impact | Action requise |
|---------------|-------------------|----------------|

## Prochaines étapes

1. [Action] — [Responsable] — [Deadline]
```

## Étape 4 — Mettre à jour la mémoire projet

1. Ajoute `### W[N] — [date]` dans `00_Reference/[PROJET]_Memoire.md`
2. Liste toutes les décisions actées sous cette section
3. Retire des "Points ouverts" ce qui a été tranché aujourd'hui
4. Ajoute les nouveaux points ouverts

## Étape 5 — Mettre à jour les fichiers

- Sauvegarde le CR dans `04_Workshops/CR/[PROJET]_CR_Workshop_W[N].md`
- Mets à jour `00_Reference/[PROJET]_Synthese.md` si l'avancement a changé
- Mets à jour `SESSIONS_INDEX.md`
- Mets à jour `INDEX.md` avec le nouveau fichier CR

## Étape 6 — Résumé final

Termine toujours par :
- Nombre de décisions actées
- Briefs fonctionnels à modifier/créer
- Points ouverts restants
- Prochaine action prioritaire recommandée

## Règles strictes

- Ne pas inventer de décisions absentes de la transcription ou des notes
- Si c'est ambigu dans la transcription, le mettre en "point ouvert" — pas l'interpréter
- Ne pas supprimer des points ouverts existants s'ils n'ont pas été explicitement tranchés
- Ne jamais publier sans validation explicite du PM
