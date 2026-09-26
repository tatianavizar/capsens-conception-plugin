---
name: write-project-brief
description: >
  Rédige ou met à jour le brief projet (niveau mission) et le plan des briefs fonctionnels :
  vision, personas, périmètre global, découpage en briefs (BF-01, BF-02…), contraintes et
  questions en suspens. Le plan des briefs est l'outil de suivi de toute la mission.
  Déclencher quand le CDP dit : "rédige le brief projet", "brief projet", "vue d'ensemble
  du projet", "découpe le projet en briefs", "plan des briefs", "quels briefs on a ?",
  "mets à jour le plan", ou équivalent.
---

# Write Project Brief

Produit deux fichiers :
- `01_Briefs_Fonctionnels/[PROJET]_Brief_Projet.md` — la vue d'ensemble de la mission, stable
- `01_Briefs_Fonctionnels/[PROJET]_Plan_Briefs.md` — le suivi des briefs fonctionnels, mis à
  jour à chaque brief (par ce skill et par `write-brief`)

Un brief fonctionnel = un PRD au format Capsens (skill `write-brief`).

## Étape 1 — Charger le contexte

- Lis `INDEX.md`, `00_Reference/[PROJET]_Synthese.md` et `00_Reference/[PROJET]_Memoire.md`
- Lis les CRs de `04_Workshops/CR/`
- Si le brief projet ou le plan existent déjà, pars de ces fichiers : c'est une mise à jour

## Étape 2 — Vérifier les prérequis

Le brief projet a besoin au minimum du contexte, du problème et d'une première idée du
périmètre. S'ils ne sont pas dans la mémoire, liste ce qui manque et demande au CDP avant
de rédiger. N'invente rien : une info absente devient une question en suspens.

## Étape 3 — Rédiger le brief projet

Structure exacte :

```markdown
# Brief projet : [PROJET]

## Méta

| Info | Valeur |
|---|---|
| Statut | 🔴 Draft / 🟡 En validation / 🟢 Validé |
| Date création | [JJ/MM/AAAA] |
| Mis à jour | [JJ/MM/AAAA] |
| Source | [W0 (kick-off), W1, W2… — Dn] |
| CDP | [Prénom si le CDP l'a donné, sinon "CDP Capsens"] |
| Client | [Client] |
| Verticale | [Verticale] |

## 1. Contexte & Ambition

### Contexte
[Qui est le client, pourquoi ce projet maintenant.]

### Ambition
[Ce que le produit doit permettre, en quelques lignes.]

## 2. Personas

- **[Persona 1]** : [qui il est, ce qu'il attend du produit]
- **[Persona 2]** : …

## 3. Périmètre global

- ✅ **Inclus V1** : [grands blocs fonctionnels]
- ❌ **Exclus V1** : [ce qui est hors scope et pourrait être ambigu — et pourquoi]

## 4. Briefs fonctionnels

Voir `[PROJET]_Plan_Briefs.md` pour le statut et l'ordre de rédaction.

| BF | Nom | Ce que ça couvre |
|----|-----|------------------|
| BF-01 | [Nom] | [1 ligne] |

## 5. Contraintes connues

### Réglementaire
[— ou "Aucune"]

### Outils externes
[— ou "Aucun"]

### Design
[— ou "Aucun"]

### Calendrier
[— ou "Aucune"]

## 6. Questions en suspens

### Client
- ⏳ Qn — [Question] — en attente de [rôle]
- ✅ Qn — [Question] — [Réponse validée] (Dn)

### Dev
- ⏳ Qn — [Question]

### Design
- ⏳ Qn — [Question]
```

## Étape 4 — Rédiger ou mettre à jour le plan des briefs

Structure exacte :

```markdown
# [PROJET] — Plan des briefs fonctionnels
Mis à jour : [JJ/MM/AAAA]

## Vue d'ensemble

| BF | Nom | Priorité | Statut | Bloqué par | Dépendances | Fichier |
|----|-----|----------|--------|------------|-------------|---------|
| BF-01 | [Nom] | P0 | ⚪ À rédiger | — | — | — |
| BF-02 | [Nom] | P1 | ⚪ À rédiger | Q4 | BF-01 | — |

Statuts : ⚪ À rédiger / 🔴 Draft / 🟡 En validation / 🟢 Validé / ❌ Abandonné (avec raison)

## Ordre de rédaction recommandé
1. **BF-01 [Nom]** — [pourquoi en premier : débloque X, aucun blocker]
2. …

## Frontières entre briefs
| Sujet | Couvert par | Pas par |
|-------|-------------|---------|
| [ex : emails de souscription] | BF-03 | BF-02 |
```

## Règles de rédaction

- **Numérotation** : `BF-01`, `BF-02`… Un numéro attribué ne change jamais, même si le brief
  est abandonné (il passe alors en ❌ avec la raison).
- **Bloqué par** : les `Qn` de la mémoire qui empêchent de rédiger le brief.
- **Dépendances** : jamais circulaires. Si deux briefs dépendent l'un de l'autre, trancher dans
  les frontières lequel porte le sujet commun.
- **Nouvelles questions** : toute nouvelle `Qn` est ajoutée immédiatement au tableau
  "Points ouverts" de la mémoire, avec sa catégorie (Client / Dev / Design).
- **Frontières** : dès que deux briefs pourraient couvrir le même sujet, trancher ici qui le porte.
- **Rôles uniquement**, jamais de prénoms — y compris dans "en attente de" (seule exception :
  le champ Méta CDP, si le CDP a donné son prénom).
- **Questions** : numérotation `Qn` identique à celle des points ouverts de la mémoire.
  Une question tranchée reste listée, en ✅, avec la décision `Dn` qui la tranche.
- **Contraintes réglementaires** : si la verticale du projet est renseignée, charge le skill
  `verticale-metier` pour compléter cette section.
- Pas de design, pas de technique : le brief projet dit quoi et pourquoi, pas comment.

## Étape 5 — Sauvegarder et demander validation

1. Sauvegarde les deux fichiers dans `01_Briefs_Fonctionnels/`. Statut du brief projet :
   🔴 Draft pendant la rédaction, 🟡 En validation dès qu'il est présenté au CDP, 🟢 Validé
   quand le CDP le valide
2. Mets à jour `INDEX.md`
3. Présente-les au CDP et demande la validation explicite.
   Ne jamais publier (Slite, Notion, etc.) sans accord explicite.
4. Propose le premier brief à rédiger (skill `write-brief`) selon l'ordre recommandé.
