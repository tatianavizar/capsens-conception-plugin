# Template — Prompt Brief Fonctionnel

Copier-coller ce template dans `00_Reference/[PROJET]_Prompt_Brief_Fonctionnel.md`
en remplaçant [PROJET] et [CLIENT].

---

## Prompt à utiliser pour chaque brief fonctionnel

```
Tu vas rédiger un brief fonctionnel (PRD au format Capsens) pour le projet [PROJET] ([CLIENT]).

Commence par lire dans l'ordre :
1. CLAUDE.md — règles et conventions du projet
2. INDEX.md — pour te repérer dans les fichiers
3. 00_Reference/[PROJET]_Memoire.md — pour comprendre où on en est
4. 01_Briefs_Fonctionnels/[PROJET]_Brief_Projet.md et [PROJET]_Plan_Briefs.md
5. Les briefs déjà rédigés dans 01_Briefs_Fonctionnels/ — pour caler le format
   et vérifier la cohérence

RÈGLES DE CONTENU

Ce que le brief DOIT couvrir :
- Contexte & problème, solution et scope (✅ Inclus / ❌ Exclus)
- Les personas impactés
- Le découpage en features numérotées (001, 002…)
- Pour chaque feature : flux d'utilisation (séquence numérotée avec embranchements),
  règles métier numérotées citant leur décision (Dn), cas limites avec comportement
  attendu, actions par rôle, informations tracées (fonctionnel, pas noms de champs)
- Les contraintes connues (réglementaire, outils externes, design, calendrier)
- Les questions en suspens (Client / Dev / Design) uniquement si réellement non tranchées

Ce que le brief NE DOIT PAS contenir :
- Descriptions visuelles (placement, couleurs, composants) → brief design
- Noms de champs techniques, modèles de données → dev
- Contenu Phase 2/V2 → ❌ Exclus, avec la raison
- Questions déjà tranchées dans la mémoire projet (sauf en ✅ avec la décision)
- Un sujet que le plan des briefs attribue à un autre brief → le citer en dépendance

RÈGLES DE FORME
- Rôles uniquement (ex : analyste, admin, investisseur), jamais de prénoms — seule exception :
  les champs Méta CDP et Devs prévus, si le CDP a donné les prénoms
- Un brief = un PRD, numéroté BF-NN dans le plan des briefs
- Dépendances : citer par numéro et nom ("BF-06 Vue Analyste", "BF-02 / 003"),
  jamais par chemin
- Dates JJ/MM/AAAA ; statut 🔴 Draft / 🟡 En validation / 🟢 Validé

STRUCTURE TYPE
# PRD : BF-[NN] [Nom]
## Méta                          ← tableau : Statut, Date création, Source, CDP,
                                   Devs prévus, Priorité, Figma, Timeline
## 1. Contexte & Problème
## 2. Solution proposée & Scope  ← ✅ Inclus / ❌ Exclus
## 3. Personas impactés
## 4. Découpage en features      ← tableau # | Feature | Priorité | Dépendances | Statut spec
## 5. Spécifications fonctionnelles  ← une sous-section par feature
## 6. Contraintes connues
## 7. Questions en suspens       ← Client / Dev / Design, ⏳ ou ✅

PUBLICATION
⚠️ Ne jamais publier sans validation explicite du CDP.
Rédiger et sauvegarder localement d'abord.
Terminer en présentant le fichier et en demandant la validation avant toute publication.
```
