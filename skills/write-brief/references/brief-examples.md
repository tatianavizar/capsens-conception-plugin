# Exemples de briefs fonctionnels de référence

Ces exemples illustrent le niveau de précision attendu.

## Exemple de flux d'utilisation type (bonne pratique)

```
## Flux d'utilisation type

1. L'analyste accède à la file d'attente depuis le dashboard
2. Il sélectionne un bien en statut "À analyser"
3. Le système affiche la fiche bien avec le score MarketAnomaly et le score de liquidité
4. L'analyste consulte les lots et ajuste la thèse d'investissement
   - Si prix idéal dans fourchette : bouton GO disponible
   - Si prix hors fourchette : explication obligatoire avant de continuer
5. L'analyste rend son verdict (GO / NO GO / En attente)
6. Le système enregistre le verdict et notifie le COO si GO
```

## Exemple de règles métier (bonne pratique)

```
## Règles métier

1. Un bien ne peut pas avoir deux verdicts actifs simultanément.
2. Le bouton GO est désactivé si le score MarketAnomaly est inférieur au seuil configuré
   dans les paramètres (défaut : 60/100).
3. Si l'analyste saisit un prix max supérieur de plus de 15% au prix idéal calculé,
   un champ "Justification" devient obligatoire avant validation.
4. Le statut "En attente" suspend les relances automatiques pour 30 jours.
5. Seul le COO peut modifier un verdict après validation initiale.
```

## Exemple de cas limites (bonne pratique)

```
## Cas limites

| Situation | Comportement attendu |
|-----------|---------------------|
| Score non disponible (calcul en cours) | Afficher "Score en calcul" — bouton GO désactivé |
| Bien déjà analysé par un autre analyste | Afficher le verdict existant + auteur + date |
| Perte de connexion pendant la saisie | Sauvegarder le brouillon, reprendre au même état |
| Données Casafari incomplètes | Afficher les champs manquants en orange, bloquer GO |
```

## Ce qu'il NE FAUT PAS mettre dans un brief

```
❌ "Le bouton GO sera vert et positionné en bas à droite de la fiche"
   → Ça va dans le brief design

❌ "Le champ `market_anomaly_score` en base de données sera de type FLOAT"
   → Ça va dans les specs techniques

❌ "En Phase 2, on ajoutera une vue comparateur multi-biens"
   → Hors scope V1

❌ "Il faudra probablement prévoir une API pour les notaires"
   → À mettre en question ouverte si non tranché, pas dans les règles métier
```
