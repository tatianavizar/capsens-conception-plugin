---
name: fetch-transcript
description: >
  Récupère la transcription d'une réunion tl;dv et la formate en CR PMO structuré.
  Déclencher quand le PM dit : "récupère le workshop", "fetch le transcript", "CR de la réunion",
  "récupère la transcription [réunion/workshop/call]", "résumé tl;dv", ou tout équivalent
  indiquant qu'on veut exploiter une réunion enregistrée dans tl;dv.
---

# Fetch Transcript

Récupère une transcription tl;dv et produit un CR PMO structuré prêt à l'emploi.

## Prérequis

tl;dv doit être configuré dans `.mcp.json`. Si les outils tl;dv ne sont pas disponibles,
demander au PM de coller ses notes brutes et passer directement à l'étape 3.

## Étape 1 — Identifier la réunion

1. Appelle `list-meetings` pour lister les réunions des 48 dernières heures
2. Présente la liste au PM :
   ```
   Réunions tl;dv récentes :
   1. [Titre] — [Date] — [Durée]
   2. [Titre] — [Date] — [Durée]
   ...
   
   C'est laquelle ?
   ```
3. Si aucune réunion n'est trouvée dans les 48h, élargis à 7 jours et préviens le PM
4. Attends la confirmation du PM avant de continuer

## Étape 2 — Récupérer la transcription

1. Appelle `get-transcript` avec l'ID de la réunion confirmée
2. Appelle `get-highlights` si disponible — les highlights complètent la transcription brute
3. Si la transcription est vide ou trop courte (< 500 mots), préviens le PM :
   ```
   ⚠️ La transcription semble incomplète ([N] mots). 
   Tu veux continuer quand même ou coller des notes complémentaires ?
   ```

## Étape 3 — Appliquer le format PMO

Utilise le prompt suivant pour structurer le CR :

---

### RÔLE

Tu agis en tant que PMO (Project Management Officer) ultra-synthétique et rigoureux.
Ta mission est de transformer une transcription de réunion en compte-rendu exploitable.

### PARAMÈTRE DE DÉTAIL

- **Niveau de synthèse** : élevé — ne retenir que ce qui a une valeur décisionnelle ou opérationnelle
- **Langue** : français
- **Ton** : neutre, factuel, professionnel

### RÈGLES D'OR

1. **Anti-hallucination** : ne jamais inventer ou inférer des informations absentes de la transcription
2. **Attributions** : toujours mentionner qui a dit quoi pour les décisions et actions (utiliser les rôles, pas les prénoms sauf si un rôle n'est pas identifiable)
3. **Décisions vs opinions** : distinguer clairement ce qui a été décidé de ce qui a été discuté ou suggéré
4. **Actions = SMART** : chaque action doit avoir un responsable et, si mentionné, une échéance
5. **Questions en suspens** : ne jamais "résoudre" une question ouverte — si la réponse n'est pas dans la transcription, la question reste ouverte

---

### STRUCTURE DE SORTIE

## 📌 RÉSUMÉ DE LA RÉUNION

*[2-4 phrases max. Contexte de la réunion, objectif, conclusion principale.]*

---

## ✅ ACTIONS ET RESPONSABILITÉS

| Action | Responsable | Échéance |
|--------|-------------|----------|
| [Action SMART extraite de la transcription] | [Rôle/Prénom si rôle non identifiable] | [Date si mentionnée / "Non définie"] |

---

## 🤝 POINTS D'ACCORD & INSIGHTS

*[Liste des décisions actées et constats partagés — bullet points, une ligne par point]*

- [Décision ou insight 1]
- [Décision ou insight 2]

---

## ⚠️ HYPOTHÈSES ET SUPPOSITIONS

*[Ce qui a été présenté comme probable ou anticipé, mais pas confirmé — distingué des faits]*

- [Hypothèse 1 — qui l'a formulée si identifiable]
- [Hypothèse 2]

---

## ❓ QUESTIONS EN SUSPENS (BACKLOG)

| # | Question | Soulevée par | Impact |
|---|----------|--------------|--------|
| 1 | [Question ouverte non résolue] | [Rôle/Prénom] | [Ce que ça bloque ou influence] |

---

## Étape 4 — Livrer le CR

1. Affiche le CR complet dans la conversation
2. Demande au PM : **"Tu veux que je sauvegarde ce CR quelque part ?"**
   - Si oui → propose `04_Workshops/CR/[PROJET]_CR_Workshop_W[N].md` et sauvegarder
   - Si non → le PM copiera manuellement

> **Note** : Ce skill produit la matière brute. Si tu débriefes un workshop projet,
> utilise le skill `workshop-debrief` qui charge le contexte projet et met à jour la mémoire.
