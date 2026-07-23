---
name: consistency-check
description: >
  Audite la cohérence de tous les briefs fonctionnels d'un projet : détecte les contradictions,
  les dépendances non documentées, les décisions déjà tranchées mais encore listées en
  questions ouvertes, et les zones couvertes dans la mémoire mais absentes des briefs.
  Déclencher quand le PM dit : "audit de cohérence", "vérifie la cohérence des briefs",
  "consistency check", "est-ce que les briefs sont alignés", "cherche les contradictions",
  "avant le chiffrage vérifie tout", "revue des briefs", ou équivalent.
  À utiliser systématiquement avant la rédaction du brief exécutif final.
---

# Consistency Check

Audite la cohérence de l'ensemble des livrables d'une mission de conception.

## Ce que tu dois faire

1. **Charge le contexte complet** :
   - `INDEX.md`
   - `00_Reference/[PROJET]_Memoire.md` (source de vérité)
   - Tous les briefs dans `01_Briefs_Fonctionnels/`
   - L'architecture technique si elle existe

2. **Effectue les 5 vérifications** :

   ### Vérification 1 — Contradictions entre briefs
   Cherche les cas où deux briefs décrivent la même règle différemment.
   Ex : BF-A dit "seul l'admin peut modifier X" et BF-B dit "le manager peut modifier X".

   ### Vérification 2 — Zones couvertes dans la mémoire mais absentes des briefs
   Cherche les features ou règles actées en workshop (dans la mémoire) qui n'ont
   pas encore été documentées dans un brief fonctionnel.

   ### Vérification 3 — Dépendances non documentées
   Cherche les cas où un brief utilise des concepts définis dans un autre brief
   sans le citer dans sa section "Dépendances fonctionnelles".

   ### Vérification 4 — Questions ouvertes déjà tranchées
   Cherche les questions ouvertes listées dans les briefs qui sont en fait déjà
   répondues dans la mémoire projet (décision prise en workshop mais pas répercutée).

   ### Vérification 5 — Cohérence des rôles
   Vérifie que les mêmes rôles ont les mêmes noms et les mêmes droits dans tous les briefs.
   Cherche les incohérences de permissions (rôle X peut faire Y dans BF-A mais pas dans BF-B).

3. **Présente les résultats** sous forme de tableau :

   ```
   ## Rapport d'audit de cohérence — [PROJET]
   Date : [date]
   Briefs analysés : [N]

   ### Contradictions (Vérification 1)
   | # | Problème | Brief(s) impacté(s) | Recommandation |
   |---|----------|---------------------|----------------|

   ### Zones non couvertes (Vérification 2)
   | # | Feature/règle dans la mémoire | Status | Action recommandée |
   |---|-------------------------------|--------|--------------------|

   ### Dépendances manquantes (Vérification 3)
   | # | Brief | Dépendance manquante | Action |
   |---|-------|---------------------|--------|

   ### Questions ouvertes déjà tranchées (Vérification 4)
   | # | Brief | Question | Décision dans la mémoire | Action |
   |---|-------|----------|--------------------------|--------|

   ### Incohérences de rôles (Vérification 5)
   | # | Rôle | Brief A | Brief B | Incohérence | Recommandation |
   |---|------|---------|---------|-------------|----------------|

   ### Score de cohérence
   - Contradictions : [N] trouvées
   - Zones non couvertes : [N] trouvées
   - Dépendances manquantes : [N] trouvées
   - Questions obsolètes : [N] trouvées
   - Incohérences de rôles : [N] trouvées

   ### Priorité de correction avant chiffrage
   1. [Action la plus critique]
   2. ...
   ```

4. **Sauvegarde le rapport** dans `00_Reference/[PROJET]_Audit_Coherence_[date].md`

5. **Propose** de corriger les problèmes identifiés, en commençant par les plus critiques.
   Ne corrige pas automatiquement — attends la validation du PM pour chaque correction.

## Important
Sois exhaustif même si ça prend du temps. Un bug de cohérence découvert pendant le
chiffrage ou le développement coûte 10x plus cher qu'un bug découvert ici.
