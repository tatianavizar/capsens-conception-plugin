---
name: session-start
description: >
  Charge le contexte complet d'une mission Capsens en début de conversation.
  Permet à Claude de reprendre le travail là où on s'est arrêtés sans avoir
  à tout réexpliquer. Déclencher quand le PM dit : "reprends le projet [nom]",
  "on reprend [projet]", "contexte [projet]", "charge le projet", "où on en est
  sur [projet]", "je veux travailler sur [projet]", "session [projet]",
  ou en début de toute conversation sur une mission en cours.
---

# Session Start

Charge le contexte d'une mission en cours pour pouvoir travailler immédiatement.

## Ce que tu dois faire

1. **Identifie le projet** si ce n'est pas déjà clair dans le message du PM.

2. **Lis les fichiers dans cet ordre précis** :
   - `INDEX.md` — pour te repérer dans tous les fichiers du projet
   - `00_Reference/[PROJET]_Synthese.md` — pour comprendre l'état d'avancement actuel
   - `SESSIONS_INDEX.md` — pour voir ce que les conversations précédentes ont produit

3. **Si la session porte sur un sujet précis** (ex : "on va travailler sur le brief scoring"),
   lis aussi le fichier pertinent avant de confirmer le chargement.

4. **Confirme en 3 lignes** :
   - Ce que tu as compris de l'état du projet (1 ligne)
   - Ce que les dernières sessions ont produit (1 ligne)
   - Ce sur quoi tu es prêt à travailler aujourd'hui (1 ligne)

5. **Propose les actions disponibles** selon le contexte :
   - Si des briefs sont "À rédiger" → proposer write-brief
   - Si un workshop est prévu prochainement → proposer workshop-prep
   - Si beaucoup de briefs ont été rédigés récemment → proposer consistency-check
   - Sinon → demander sur quoi le PM veut travailler

## Ton comportement pendant la session

Une fois le contexte chargé, tu es le co-PM du projet. Tu connais toutes les décisions,
les personas, le pipeline métier, la stack technique. Tu peux :
- Répondre à des questions sur le projet sans relire les fichiers (tu les as en mémoire)
- Rédiger des livrables en cohérence avec les décisions existantes
- Détecter les incohérences par rapport à ce que tu sais

## Fin de session

Si le PM dit "on s'arrête", "fin de session", "à demain", ou équivalent,
applique automatiquement le Protocole SESSION END :

1. Mets à jour `00_Reference/[PROJET]_Memoire.md` avec les décisions de la session
2. Mets à jour `00_Reference/[PROJET]_Synthese.md` si l'avancement a changé
3. Ajoute cette conversation à `SESSIONS_INDEX.md`
4. Mets à jour `INDEX.md` si de nouveaux fichiers ont été créés
5. Résume en 5 points ce qui a été acté ou produit aujourd'hui
