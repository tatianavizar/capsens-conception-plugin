---
name: workshop-prep
description: >
  Prépare une trame complète pour un workshop client : objectifs, points ouverts à trancher,
  séquence de sujets avec timing, hypothèses à valider, checklist décisions.
  Déclencher quand le PM dit : "prépare le workshop [N]", "trame workshop", "on a un workshop
  demain", "prépare la session avec [client]", "je dois animer [sujet] avec [client]",
  "prépare les questions pour [réunion]", "atelier [sujet]", ou tout équivalent indiquant
  qu'une session de travail avec le client est à venir.
---

# Workshop Prep

Génère une trame opérationnelle pour conduire un workshop client.

## Ce que tu dois faire

1. **Charge le contexte du projet** si ce n'est pas déjà fait :
   - Lis `00_Reference/[PROJET]_Memoire.md`
   - Lis les CRs des workshops précédents dans `04_Workshops/CR/`
   - Lis les briefs fonctionnels des features qui seront abordées

2. **Identifie les informations manquantes** pour préparer la trame :
   - Numéro du workshop (W1, W2, W3...)
   - Thème ou sujet principal
   - Durée prévue
   - Participants côté client
   - Objectifs spécifiques si le PM les a déjà en tête

3. **Génère la trame** avec cette structure exacte :

   ```
   # Trame Workshop [N] — [Thème]
   Date : [date] | Durée : [X]h | Participants : [liste]

   ## Objectifs de la session
   Ce qu'on doit avoir décidé à la fin :
   1. [Objectif 1]
   2. [Objectif 2]

   ## Points ouverts à trancher
   (extraits de la mémoire projet)
   | Point ouvert | Contexte | Options envisagées |
   |--------------|----------|--------------------|

   ## Séquence et timing
   | Bloc | Durée | Sujet | Hypothèses à valider |
   |------|-------|-------|----------------------|

   ## Checklist décisions
   À cocher pendant la session :
   ☐ [Décision 1 à prendre]
   ☐ [Décision 2 à prendre]

   ## Si on manque de temps
   Sujets reportables : [liste]
   ```

4. **Sauvegarde la trame** dans `04_Workshops/Trames/[PROJET]_Trame_Workshop_W[N].md`

5. **Mets à jour INDEX.md** avec le nouveau fichier

## Ton approche

- Priorise les points ouverts qui débloquent le plus de briefs fonctionnels en attente
- Identifie les dépendances : si on tranche A, ça débloque B et C
- Pour chaque bloc, note les hypothèses à valider — pas de liste de questions détaillées,
  c'est le PM qui conduit la session à sa façon

## Important
Cette trame est une aide-mémoire pour le PM, pas un document client.
Style opérationnel et direct.
