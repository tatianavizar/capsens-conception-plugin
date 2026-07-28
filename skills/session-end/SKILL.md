---
name: session-end
description: >
  Clôture une session de travail sur une mission de conception Capsens : met à jour
  la mémoire projet, la synthèse, l'index des sessions et l'index des fichiers avant
  de se quitter. Déclencher quand le PM dit : "on s'arrête", "fin de session", "à demain",
  "on ferme la session", "c'est bon pour aujourd'hui", "on clôture", ou tout équivalent
  signalant la fin d'une session de travail. À proposer aussi spontanément en fin de
  conversation si des décisions ont été prises ou des fichiers créés/modifiés sans que
  le protocole ait encore été appliqué.
---

# Session End

Clôture une session de travail pour garantir que la prochaine session — avec ou sans
mémoire de celle-ci — puisse repartir sans perte d'information.

## Étape 1 — Vérifier qu'il y a matière à clôturer

Repasse en revue la session : nouveaux fichiers créés, décisions actées, questions
tranchées, arbitrages du PM.

Si rien de tout ça ne s'est produit (pure discussion, question ponctuelle sans suite),
dis-le simplement et ne force pas une mise à jour vide.

## Étape 2 — Mettre à jour la mémoire projet

Dans `00_Reference/[PROJET]_Memoire.md` :
- Ajoute les décisions prises aujourd'hui dans la section concernée
- Retire des "Points ouverts" ce qui vient d'être tranché
- N'ajoute que ce qui a été réellement décidé — pas les hypothèses encore en discussion

## Étape 3 — Mettre à jour la synthèse

Dans `00_Reference/[PROJET]_Synthese.md`, mets à jour l'état d'avancement si la phase,
le pourcentage de scope couvert ou la prochaine étape a changé.

## Étape 4 — Mettre à jour l'index des sessions

Dans `SESSIONS_INDEX.md` :
- Ajoute une ligne pour cette conversation (sujet, ce qui a été produit, fichier(s))
- Si un sujet reste inachevé, ajoute-le dans la section "À reprendre"

## Étape 5 — Mettre à jour l'index des fichiers

Dans `INDEX.md` :
- Ajoute les nouveaux fichiers créés pendant la session
- Mets à jour le statut des fichiers modifiés (ex : "🔴 À rédiger" → "✅ Acté")

## Étape 6 — Résumé final

Termine toujours par un résumé en 5 points maximum de ce qui a été acté ou produit
aujourd'hui, pour validation par le PM avant de fermer la conversation.

## Règles strictes

- Ne jamais écrire dans `[PROJET]_Notes_Internes.md` du contenu qui vient d'un livrable
  — ce fichier est réservé aux observations confidentielles du PM
- Si aucun fichier mémoire n'existe encore (mission non initialisée via `init-mission`),
  signale-le au lieu d'improviser une structure
- Ne jamais publier ou partager un fichier au client à cette étape — ce protocole ne
  fait que mettre à jour la mémoire locale
