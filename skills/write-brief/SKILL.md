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

1. Lis `01_Briefs_Fonctionnels/[PROJET]_Plan_Briefs.md`
2. Identifie les briefs en 🔴 À rédiger sans blocker ouvert
3. Suis l'"Ordre de rédaction recommandé" du plan
4. Propose au CDP le brief le plus prioritaire avec une justification courte :
   ```
   Le prochain brief à rédiger est **BF-[NN] [NOM]** car :
   - Statut : 🔴 À rédiger, aucun blocker ouvert
   - Il débloque : [briefs dépendants]
   - Priorité : [P0/P1/P2/P3]

   Je continue avec celui-là ? Ou tu préfères [alternative] ?
   ```
5. Attends la confirmation avant de commencer.

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

Avant de rédiger, vérifie si des décisions manquantes bloqueraient le brief.
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
| CDP | [Nom du CDP] |
| Devs prévus | [Noms ou "À définir"] |
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
| 002 | [Titre] | P1 | 001, BF-02 / 003 | 🔴 |

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
- **Features** : numérotées `001`, `002`… à l'intérieur du brief. Hors du brief, on les cite
  `BF-02 / 003`. Un numéro attribué ne change jamais.
- **Statut spec** : 🔴 non spécifiée / 🟡 spécifiée, en validation / 🟢 validée.
- **Citation des décisions** : chaque règle métier issue d'une décision cite son `(Dn)`.
- **Questions** : numérotation `Qn` identique à celle de la mémoire. Une question tranchée
  reste listée en ✅ avec sa décision. Si aucune : "Aucune question en suspens — décisions
  actées (Dn, Dn)".
- **Cas limites** : si la verticale est chargée, passe en revue ses risques types et intègre
  les 3 à 5 plus probables pour chaque feature.
- **Emails transactionnels** propres au brief : les décrire dans la feature concernée, en
  blockquote (Objet / Destinataire (rôle) / Déclencheur / Contenu / CTA).

## Étape 4 — Sauvegarder et demander validation

1. Sauvegarde dans `01_Briefs_Fonctionnels/[PROJET]_BF-[NN]_[Nom].md`
2. Mets à jour le plan des briefs : statut (🟡 En validation, puis 🟢 Validé une fois validé
   par le CDP), colonne Fichier, et "Bloqué par" si de nouvelles questions bloquent d'autres briefs
3. Mets à jour `INDEX.md`
4. **Présente le fichier au CDP et demande la validation explicite.**
   Ne jamais publier (Slite, Notion, etc.) sans accord explicite.

## Règles strictes

- **Rôles uniquement** — jamais de prénoms, nulle part, y compris dans les questions en suspens
- **V1 uniquement** — Phase 2 / futur → ❌ Exclus, avec la raison
- **Pas de design** — pas de description d'interface, placement, couleurs
- **Pas de technique** — pas de noms de colonnes, endpoints, modèles de données
- **Pas d'invention** — règle métier absente de la mémoire → question en suspens, pas invention
- **Frontières** — ne pas spécifier un sujet que le plan attribue à un autre brief : le citer
  en dépendance
