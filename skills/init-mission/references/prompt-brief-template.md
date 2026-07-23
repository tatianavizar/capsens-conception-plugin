# Template — Prompt Brief Fonctionnel

Copier-coller ce template dans `00_Reference/[PROJET]_Prompt_Brief_Fonctionnel.md`
en remplaçant [PROJET] et [CLIENT].

---

## Prompt à utiliser pour chaque brief fonctionnel

```
Tu vas rédiger un brief fonctionnel pour le projet [PROJET] ([CLIENT]).

Commence par lire dans l'ordre :
1. INDEX.md — pour te repérer dans les fichiers
2. 00_Reference/[PROJET]_Memoire.md — pour comprendre où on en est
3. Les briefs déjà rédigés dans 01_Briefs_Fonctionnels/ — pour caler le format
   et vérifier la cohérence

RÈGLES DE CONTENU

Ce que le brief DOIT couvrir :
- Un flux d'utilisation clair (séquence numérotée avec embranchements)
- La description fonctionnelle de chaque étape (user fait X → système répond Y)
- Un tableau des actions par rôle
- Les règles métier numérotées
- Les cas limites avec comportement attendu
- Les informations tracées par le système (fonctionnel, pas noms de champs)
- Les dépendances vers les autres briefs (par nom, pas par chemin de fichier)
- Les questions ouvertes uniquement si réellement non tranchées

Ce que le brief NE DOIT PAS contenir :
- Descriptions visuelles (placement, couleurs, composants) → brief design
- Noms de champs techniques, modèles de données → dev
- Contenu Phase 2/V2 → V1 uniquement
- Questions ouvertes déjà tranchées dans la mémoire projet

RÈGLES DE FORME
- Utiliser les rôles (ex : analyste, admin, client), jamais les prénoms
- Un brief = une feature ou un parcours
- Dépendances : citer par nom ("BF-06 Vue Analyste"), jamais par chemin

STRUCTURE TYPE
# [Nom feature] — Brief Fonctionnel
Date · PM · Client · Statut

> ☐ Action post-design : ajouter les liens Figma une fois les maquettes produites.

## Contexte
## Rôles
## Flux d'utilisation type   ← séquence numérotée avec embranchements
## Description fonctionnelle des étapes
## Actions par rôle          ← tableau
## Règles métier             ← liste numérotée
## Cas limites               ← tableau
## Informations tracées      ← fonctionnel uniquement
## Dépendances fonctionnelles
## Questions ouvertes        ← uniquement ce qui est réellement non tranché

PUBLICATION
⚠️ Ne jamais publier sans validation explicite du PM.
Rédiger et sauvegarder localement d'abord.
Terminer en présentant le fichier et en demandant la validation avant toute publication.
```
