---
name: workshop-prep
description: >
  Prépare une trame complète pour un workshop client : objectifs, point ouvert pivot, points
  ouverts à trancher, séquence de sujets avec timing, hypothèses à valider, checklist décisions.
  Déclencher quand le CDP dit : "prépare le workshop [N]", "trame workshop", "on a un workshop
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
   - Lis le plan des briefs et les briefs des sujets qui seront abordés
   - Si la verticale du projet est renseignée, charge le skill `verticale-metier`

2. **Identifie les informations manquantes** pour préparer la trame :
   - Numéro du workshop (W1, W2, W3… = numéro de workshop, pas de semaine)
   - Thème ou sujet principal
   - Date et durée prévue
   - Participants côté client (rôles)
   - Objectifs spécifiques si le CDP les a déjà en tête

3. **Génère la trame** avec cette structure exacte :

   ```
   # Trame Workshop W[N] — [Thème]
   Date : [JJ/MM/AAAA] | Durée : [X]h | Participants : [rôles]

   > Aide-mémoire CDP — pas un document client.

   ## Objectifs de la session
   Ce qu'on doit avoir décidé à la fin :
   1. [Objectif 1]
   2. [Objectif 2]

   ## Point ouvert pivot
   **Qn — [La question qui conditionne le plus de choses]**
   - Si [option A] → [conséquences, briefs débloqués]
   - Si [option B] → [conséquences]

   ## Points ouverts à trancher
   (numérotation identique à la mémoire projet)
   | # | Point ouvert | Contexte | Options envisagées |
   |---|--------------|----------|--------------------|
   | Qn | | | (a) … (b) … |

   ## Séquence et timing
   | Bloc | Durée | Sujet | Hypothèses à valider |
   |------|-------|-------|----------------------|
   | 0 | 5 min | Intro / cadre | — |
   | … | | | |
   | N | 5 min | Synthèse & prochaines étapes | — |

   ## Checklist décisions
   À cocher pendant la session :
   - [ ] [Décision 1 à prendre]
   - [ ] [Décision 2 à prendre]

   ## Si on manque de temps
   - **Non reportable** : [ce qui doit être tranché aujourd'hui, et pourquoi]
   - **Reportable en W[N+1]** : [liste]

   ## Points de vigilance (CDP)
   - [Sujet sensible, posture à adopter, point réglementaire à signaler au client…]
   ```

   Si le workshop touche à un sujet réglementaire, ajoute en fin de trame :
   ```
   ## Annexe — Cadre réglementaire
   ### Établi (sources primaires)
   - [Fait] — [source]
   ### À confirmer
   - [Point] — [qui peut confirmer : juriste client, conformité…]
   ```

4. **Sauvegarde la trame** dans `04_Workshops/Trames/[PROJET]_Trame_W[N]_[AAAA-MM-DD].md`

5. **Mets à jour INDEX.md** avec le nouveau fichier

## Ton approche

- Priorise les points ouverts qui débloquent le plus de briefs en attente (colonne
  "Bloqué par" du plan des briefs)
- Identifie les dépendances : si on tranche A, ça débloque B et C
- Pour chaque bloc, note les hypothèses à valider — pas de liste de questions détaillées,
  c'est le CDP qui conduit la session à sa façon
- Sur le légal et le RGPD : Capsens signale, le client décide — formule-le comme tel

## Important
Cette trame est une aide-mémoire pour le CDP, pas un document client.
Style opérationnel et direct. Rôles uniquement, jamais de prénoms.
Après le workshop, la trame ne se modifie plus : le CR fait foi.
