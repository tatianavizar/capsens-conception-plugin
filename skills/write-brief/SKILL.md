---
name: write-brief
description: >
  Rédige un brief fonctionnel dev-ready au format PRD Capsens : contexte, scope, personas,
  découpage en features, spécifications fonctionnelles par feature (flux, règles métier,
  cas limites, actions par rôle), contraintes et questions en suspens.
  Déclencher quand le CDP dit : "rédige le brief [feature]", "brief fonctionnel [sujet]",
  "PRD [sujet]", "on a validé [feature] écris le brief", "BF-[N] [feature]",
  "documente [feature]", "écris les specs de [feature]", "brief [nom parcours]",
  "prochain brief", "quel brief on fait ?", ou équivalent.
---

# Write Brief

Rédige un brief fonctionnel — un PRD au format Capsens — cohérent avec le brief projet,
le plan des briefs et tous les autres briefs de la mission.

## Étape 0 — Identifier quel brief rédiger

Si le CDP n'a pas précisé de brief :

1. Lis `01_Briefs_Fonctionnels/[PROJET]_Plan_Briefs.md` et `00_Reference/[PROJET]_Memoire.md`
2. Identifie les briefs en ⚪ À rédiger sans blocker ouvert
3. Suis l'"Ordre de rédaction recommandé" du plan
4. Pour le candidat, fais le test de maturité de l'étape 2 : s'il échoue, passe au suivant et
   signale au CDP qu'aucun brief mûr n'est disponible si tous échouent :
   ```
   ⚠️ Aucun brief n'est mûr. Le plus avancé est BF-[NN] ([N] décisions). Il manque surtout :
   [sujets]. Je te propose de préparer un workshop dessus (skill `workshop-prep`).
   ```
5. Propose au CDP le brief le plus prioritaire avec une justification courte :
   ```
   Le prochain brief à rédiger est **BF-[NN] [NOM]** car :
   - Statut : ⚪ À rédiger, aucun blocker ouvert
   - Matière : [N] décisions l'alimentent (Dn, Dn…)
   - Il débloque : [briefs dépendants]
   - Priorité : [P0/P1/P2/P3]

   Je continue avec celui-là ? Ou tu préfères [alternative] ?
   ```
6. Attends la confirmation avant de commencer.

Si le plan n'existe pas encore, propose de le créer d'abord (skill `write-project-brief`).
Si le CDP veut un brief absent du plan, ajoute-le au plan avec le numéro suivant.

Si le CDP a précisé un brief → aller directement à l'étape 1.

## Étape 1 — Charger le contexte

- Lis `INDEX.md`, `00_Reference/[PROJET]_Memoire.md`, le brief projet et le plan des briefs
- Lis `00_Reference/[PROJET]_Prompt_Brief_Fonctionnel.md` (règles spécifiques au projet)
- Lis les briefs déjà rédigés dans `01_Briefs_Fonctionnels/` pour caler le format,
  respecter les frontières du plan et éviter les contradictions
- Si la verticale du projet est renseignée, charge le skill `verticale-metier`

## Étape 2 — Vérifier les prérequis

**Test de maturité** : liste les `Dn` de la mémoire qui alimentent ce brief et, pour chaque
feature pressentie, ce qui est acté (flux, règles, rôles). Si une feature n'a aucune décision
qui la porte, ou si la plupart des règles seraient des questions, le brief n'est pas mûr :
```
⚠️ BF-[NN] n'est pas mûr : [N] décisions seulement ([Dn…]), la feature [X] n'a aucune
règle actée. Je te propose plutôt de préparer un workshop sur [sujets] (skill `workshop-prep`).
On rédige quand même un brouillon ?
```

Vérifie ensuite si des décisions manquantes bloqueraient le brief.
Si oui, liste-les clairement :
```
⚠️ Avant de rédiger ce brief, ces points doivent être tranchés :
1. Qn — [Question non résolue] — impact : [ce qui est bloqué]
2. ...

On continue quand même (je mets ces points en "questions en suspens") ?
Ou tu veux d'abord trancher ces points ?
```

## Étape 3 — Rédiger le brief

Structure exacte :

```markdown
# PRD : BF-[NN] [Nom]

## Méta

| Info | Valeur |
|---|---|
| Statut | 🔴 Draft / 🟡 En validation / 🟢 Validé |
| Date création | [JJ/MM/AAAA] |
| Source | [Workshops et décisions d'origine, ex : W3, W4 — D12, D15] |
| CDP | [Prénom si le CDP l'a donné, sinon "CDP Capsens"] |
| Devs prévus | [Prénoms si le CDP les a donnés, sinon "À définir"] |
| Priorité | P0 / P1 / P2 / P3 |
| Figma | [Lien ou "À venir — à ajouter après les maquettes"] |
| Timeline | [Contraintes de calendrier connues] |

## 1. Contexte & Problème

### Contexte
[Pourquoi ce brief existe. Quel est le besoin business/utilisateur.]

### Problème
[Quel problème concret on résout. Points de douleur actuels.]

## 2. Solution proposée & Scope

[Description de la solution en quelques lignes.]

- ✅ **Inclus** : [ce qui est dans le scope V1]
- ❌ **Exclus** : [ce qui est hors scope V1 et qui pourrait être ambigu — et pourquoi]

## 3. Personas impactés

- **[Persona 1]** : [ce qui change pour lui]
- **[Persona 2]** : [ce qui change pour lui]

## 4. Découpage en features

| # | Feature | Priorité | Dépendances | Statut spec |
|---|---------|----------|-------------|-------------|
| 001 | [Titre] | P0 | — | 🔴 |
| 002 | [Titre] | P1 | 001 | 🔴 |

## 5. Spécifications fonctionnelles

### 001 — [Feature]

**Flux d'utilisation**
1. [Le rôle fait X]
2. [Le système répond Y]
   - Si cas A : ...
   - Si cas B : ...

**Règles métier**
1. [Règle] (Dn)

**Cas limites**
| Situation | Comportement attendu |
|-----------|---------------------|

**Actions par rôle**
| Action | [Rôle 1] | [Rôle 2] |
|--------|----------|----------|

**Informations tracées**
[Fonctionnel uniquement — pas de noms de champs techniques]

### 002 — [Feature]
…

## 6. Contraintes connues

### Réglementaire
[— ou "Aucune"]

### Outils externes
[— ou "Aucun"]

### Design
[Figma disponible ? Mobile/desktop first ? — ou "Aucun"]

### Calendrier
[— ou "Aucune"]

## 7. Questions en suspens

### Client
- ⏳ Qn — [Question] — en attente de [rôle]
- ✅ Qn — [Question] — [Réponse validée] (Dn)

### Dev
- ⏳ Qn — [Question]

### Design
- ⏳ Qn — [Question]
```

Règles de remplissage :
- **Dépendances** (§4) : uniquement les prérequis amont (features du brief ou d'un autre brief
  déjà dans le plan, ex : `BF-01 / 002`), dans le même sens que le plan. Jamais un brief aval,
  jamais de dépendance circulaire.
- **Features** : numérotées `001`, `002`… à l'intérieur du brief. Hors du brief, on les cite
  `BF-02 / 003`. Un numéro attribué ne change jamais.
- **Statut spec** : 🔴 non spécifiée / 🟡 spécifiée, en validation / 🟢 validée.
- **Citation des décisions** : chaque règle métier issue d'une décision cite son `(Dn)`.
- **Questions** : numérotation `Qn` identique à celle de la mémoire. Une question tranchée
  reste listée en ✅ avec sa décision. Si aucune : "Aucune question en suspens — décisions
  actées (Dn, Dn)".
- **Cas limites** : un comportement attendu qui n'est pas acté s'écrit
  "À définir → Qn" (et la `Qn` est créée) — jamais inventé.
- **Risques de la verticale** : si elle est chargée, passe en revue ses risques types et
  n'intègre que ceux qui s'appliquent vraiment à la feature — aucun si aucun ne s'applique.
- **Nouvelles questions** : toute nouvelle `Qn` créée par le brief est ajoutée immédiatement
  au tableau "Points ouverts" de la mémoire, avec la même catégorie (Client / Dev / Design).
- **Emails transactionnels** propres au brief : les décrire dans la feature concernée, en
  blockquote (Objet / Destinataire (rôle) / Déclencheur / Contenu / CTA).

## Étape 4 — Sauvegarder et demander validation

1. Sauvegarde dans `01_Briefs_Fonctionnels/[PROJET]_BF-[NN]_[Nom].md` (nom sans accents ni
   espaces, `_` comme séparateur)
2. Statut : 🔴 Draft pendant la rédaction ; 🟡 En validation dès que le brief est présenté au
   CDP ; 🟢 Validé quand le CDP le valide. Un brief rédigé malgré un test de maturité négatif
   reste 🔴 Draft. Reporte le même statut dans le plan des briefs, avec la colonne Fichier.
   Dans "Bloqué par", mets les `Qn` ouvertes qui bloquent ce brief lui-même, et celles qui
   bloquent d'autres briefs
3. Mets à jour `INDEX.md`
4. **Présente le fichier au CDP et demande la validation explicite.**
   Ne jamais publier (Slite, Notion, etc.) sans accord explicite.

## Règles strictes

- **Rôles uniquement** — jamais de prénoms, y compris dans les questions en suspens
  (seule exception : les champs Méta CDP et Devs prévus, si le CDP a donné les prénoms)
- **V1 uniquement** — Phase 2 / futur → ❌ Exclus, avec la raison
- **Pas de design** — pas de description d'interface, placement, couleurs
- **Pas de technique** — pas de noms de colonnes, endpoints, modèles de données
- **Pas d'invention** — règle métier absente de la mémoire → question en suspens, pas invention
- **Frontières** — ne pas spécifier un sujet que le plan attribue à un autre brief : le citer
  en dépendance
