---
name: session-start
description: >
  Charge le contexte complet d'une mission Capsens en début de conversation.
  Permet à Claude de reprendre le travail là où on s'est arrêtés sans avoir
  à tout réexpliquer. Déclencher quand le CDP dit : "reprends le projet [nom]",
  "on reprend [projet]", "contexte [projet]", "charge le projet", "où on en est
  sur [projet]", "je veux travailler sur [projet]", "session [projet]",
  ou en début de toute conversation sur une mission en cours.
---

# Session Start

Charge le contexte d'une mission en cours pour pouvoir travailler immédiatement.

## Ce que tu dois faire

1. **Identifie le projet** si ce n'est pas déjà clair dans le message du CDP.

2. **Lis les fichiers dans cet ordre précis** :
   - `CLAUDE.md` — règles et conventions du projet, verticale
   - `INDEX.md` — pour te repérer dans tous les fichiers du projet
   - `00_Reference/[PROJET]_Synthese.md` — pour comprendre l'état d'avancement actuel
   - `SESSIONS_INDEX.md` — pour voir ce que les conversations précédentes ont produit,
     et la section "À reprendre"
   - `01_Briefs_Fonctionnels/[PROJET]_Plan_Briefs.md` s'il existe — l'état des briefs

3. **Si la verticale est renseignée** dans `CLAUDE.md` ou la Synthèse, charge le skill
   `verticale-metier`.

4. **Si la session porte sur un sujet précis** (ex : "on va travailler sur le brief scoring"),
   lis aussi le fichier pertinent avant de confirmer le chargement.

5. **Confirme en 3 lignes** :
   - Ce que tu as compris de l'état du projet (1 ligne)
   - Ce que les dernières sessions ont produit ou laissé "À reprendre" (1 ligne)
   - Ce sur quoi tu es prêt à travailler aujourd'hui (1 ligne)

6. **Propose les actions disponibles** selon le contexte :
   - Pas encore de brief projet ni de plan des briefs → proposer `write-project-brief`
   - Des briefs en 🔴 À rédiger sans blocker → proposer `write-brief`
   - Un workshop est prévu prochainement → proposer `workshop-prep`
   - Beaucoup de briefs rédigés récemment → proposer `consistency-check`
   - Sinon → demander sur quoi le CDP veut travailler

## Ton comportement pendant la session

Une fois le contexte chargé, tu es le co-PM du projet. Tu connais toutes les décisions,
les personas, le pipeline métier, la stack technique. Tu peux :
- Répondre à des questions sur le projet sans relire les fichiers (tu les as en mémoire)
- Rédiger des livrables en cohérence avec les décisions existantes
- Détecter les incohérences par rapport à ce que tu sais

## Fin de session

Si le CDP dit "on s'arrête", "fin de session", "à demain", ou équivalent,
applique le skill `session-end`.
