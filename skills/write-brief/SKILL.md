---
name: write-brief
description: >
  Rédige un brief fonctionnel dev-ready pour une feature ou un parcours utilisateur.
  Couvre flux d'utilisation, règles métier, cas limites, actions par rôle et dépendances.
  Déclencher quand le PM dit : "rédige le brief [feature]", "brief fonctionnel [sujet]",
  "on a validé [feature] écris le brief", "BF-[N] [feature]", "documente [feature]",
  "écris les specs de [feature]", "brief [nom parcours]", "prochain brief", "quel brief
  on fait ?", ou équivalent.
---

# Write Brief

Rédige un brief fonctionnel complet, cohérent avec tous les autres briefs de la mission.

## Étape 0 — Identifier quel brief rédiger

Si le PM n'a pas précisé de feature :

1. Lis `01_Briefs_Fonctionnels/[PROJET]_Plan_Briefs.md` (ou l'équivalent dans le projet)
2. Identifie tous les briefs dont le statut est "À rédiger" ou équivalent
3. Identifie les dépendances : quels briefs bloquent les suivants ?
4. Propose au PM le brief le plus prioritaire avec une justification courte :
   ```
   Le prochain brief à rédiger est **[NOM]** car :
   - Statut : "À rédiger"
   - Il débloque : [briefs dépendants]
   - Priorité : [haute/moyenne/basse]
   
   Je continue avec celui-là ? Ou tu préfères [alternative] ?
   ```
5. Attends la confirmation avant de commencer.

Si le PM a précisé une feature → aller directement à l'étape 1.

## Étape 1 — Charger le contexte

- Lis `INDEX.md` et `00_Reference/[PROJET]_Memoire.md`
- Lis `00_Reference/[PROJET]_Prompt_Brief_Fonctionnel.md` (règles spécifiques au projet)
- Lis les briefs déjà rédigés dans `01_Briefs_Fonctionnels/` pour caler le format
  et éviter les contradictions

## Étape 2 — Vérifier les prérequis

Avant de rédiger, vérifie si des décisions manquantes bloqueraient le brief.
Si oui, liste-les clairement :
```
⚠️ Avant de rédiger ce brief, ces points doivent être tranchés :
1. [Question non résolue] — impact : [ce qui est bloqué]
2. ...

On continue quand même (je mets ces points en "questions ouvertes") ?
Ou tu veux d'abord trancher ces points ?
```

## Étape 3 — Rédiger le brief

Structure exacte :

```markdown
# [Nom Feature] — Brief Fonctionnel

**Date** : [date]
**PM** : [nom]
**Client** : [client]
**Statut** : Acté / En cours / À valider

> ☐ Action post-design : ajouter les liens Figma une fois les maquettes produites.

## Contexte
[2-3 phrases : pourquoi cette feature existe, quel problème elle résout]

## Rôles
| Rôle | Description dans ce parcours |
|------|------------------------------|

## Flux d'utilisation type
1. [L'utilisateur fait X]
2. [Le système répond Y]
   - Si cas A : ...
   - Si cas B : ...

## Description fonctionnelle des étapes
### Étape [N] — [Nom]
[Ce que l'utilisateur peut faire + ce que le système fait en réponse]

## Actions par rôle
| Action | [Rôle 1] | [Rôle 2] |
|--------|----------|----------|

## Règles métier
1. [Règle numérotée]

## Cas limites
| Situation | Comportement attendu |
|-----------|---------------------|

## Informations tracées
[Fonctionnel uniquement — pas de noms de champs techniques]

## Dépendances fonctionnelles
- **[BF-XX Nom]** — [nature de la dépendance]

## Questions ouvertes
| # | Question | Impact | Décideur |
|---|----------|--------|---------|
```

## Étape 4 — Sauvegarder et demander validation

1. Sauvegarde dans `01_Briefs_Fonctionnels/[PROJET]_Brief_Fonctionnel_[Feature].md`
2. Mets à jour `INDEX.md` et `[PROJET]_Plan_Briefs.md` (statut → "✅ Rédigé [date]")
3. **Présente le fichier au PM et demande la validation explicite.**
   Ne jamais publier (Slite, Notion, etc.) sans accord explicite.

## Règles strictes

- **Rôles uniquement** — jamais les prénoms
- **V1 uniquement** — Phase 2 / futur → hors scope
- **Pas de design** — pas de description d'interface, placement, couleurs
- **Pas de technique** — pas de noms de colonnes, endpoints, modèles de données
- **Pas d'invention** — règle métier absente de la mémoire → question ouverte, pas invention
