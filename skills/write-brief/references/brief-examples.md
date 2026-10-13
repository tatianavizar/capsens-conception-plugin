# Exemples de briefs fonctionnels de référence

Ces exemples illustrent le niveau de précision attendu.

## Exemple de flux d'utilisation type (bonne pratique)

```
## Flux d'utilisation type

1. L'analyste accède à la file d'attente depuis le dashboard
2. Il sélectionne un bien en statut "À analyser"
3. Le système affiche la fiche bien avec le score d'opportunité et le score de liquidité
4. L'analyste consulte les lots et ajuste la thèse d'investissement
   - Si prix idéal dans fourchette : verdict GO possible
   - Si prix hors fourchette : explication obligatoire avant de continuer
5. L'analyste rend son verdict (GO / NO GO / En attente)
6. Le système enregistre le verdict et notifie le COO si GO
```

## Exemple de règles métier (bonne pratique)

```
## Règles métier

1. Un bien ne peut pas avoir deux verdicts actifs simultanément. (D14)
2. Le verdict GO est impossible si le score d'opportunité est inférieur au seuil configuré
   dans les paramètres (défaut : 60/100). (D21)
3. Si l'analyste saisit un prix max supérieur de plus de 15% au prix idéal calculé,
   une justification devient obligatoire avant validation. (D22)
4. Le statut "En attente" suspend les relances automatiques pour 30 jours. (D25)
5. Seul le COO peut modifier un verdict après validation initiale. (D14)
```

## Exemple de cas limites (bonne pratique)

```
## Cas limites

| Situation | Comportement attendu |
|-----------|---------------------|
| Score non disponible (calcul en cours) | Afficher "Score en calcul" — verdict GO impossible |
| Bien déjà analysé par un autre analyste | Afficher le verdict existant + auteur + date |
| Perte de connexion pendant la saisie | Sauvegarder le brouillon, reprendre au même état |
| Données du fournisseur externe incomplètes | Signaler les données manquantes, verdict GO impossible |
```

## Ce qu'il NE FAUT PAS mettre dans un brief

```
❌ "Le bouton GO sera vert et positionné en bas à droite de la fiche"
   → Ça va dans le brief design

❌ "Le champ `opportunity_score` en base de données sera de type FLOAT"
   → Ça va dans les specs techniques

❌ "En Phase 2, on ajoutera une vue comparateur multi-biens"
   → Hors scope V1 : à lister en ❌ Exclus (§2), pas à spécifier

❌ "Il faudra probablement prévoir une API pour les notaires"
   → À mettre en question en suspens (Dev) si non tranché, pas dans les règles métier
```

## Exemple de questions en suspens (bonne pratique)

```
## 7. Questions en suspens

### Client
- ⏳ Q12 — Le seuil de 15 % est-il le même pour tous les types de biens ? — en attente du fondateur
- ✅ Q9 — Qui peut rouvrir un verdict NO GO ? — le COO uniquement (D14)

### Dev
- ⏳ Q13 — Le recalcul du score après modification des paramètres est-il immédiat ou différé ?

### Design
- Aucune question en suspens — décisions actées (D21, D22)
```
