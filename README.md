# Capsens × Claude — Kit Mission de Conception

Plugin Cowork pour mener des missions de conception produit avec Claude comme co-PM.

## Installation (Cowork)

### Option A — via le repo (recommandé, mises à jour automatiques)

1. Dans Cowork, ouvrez **Customize** (barre latérale) → **Plugins**
2. Cliquez **Add marketplace**
3. Collez l'URL : `https://github.com/tatianavizar/capsens-conception-plugin`
4. Le plugin **capsens-conception** apparaît → cliquez **Install**

### Option B — via fichier

1. **Customize** → **Plugins** → **Upload plugin**
2. Sélectionnez le fichier `.plugin`
3. **Install**

Vérifiez ensuite les skills activés dans **Customize → Plugins → capsens-conception**.

## Skills

| Skill | Quand l'utiliser |
|-------|-----------------|
| **init-mission** | Début de mission — crée le workspace |
| **session-start** | Début de chaque conversation sur le projet |
| **workshop-prep** | 24-48h avant chaque atelier |
| **workshop-debrief** | Après l'atelier — transcription tl;dv ou notes → CR |
| **write-brief** | Documenter une feature validée |
| **consistency-check** | Tous les 3-4 workshops + avant le brief final |

## tl;dv (optionnel)

Récupère automatiquement les transcriptions de workshops. Ajoutez la clé API dans les réglages :

```
TLDV_API_KEY=votre_clé_api
```

Clé : https://tldv.io/app/settings/personal-settings/api-keys

Sans tl;dv, `workshop-debrief` travaille sur les notes brutes collées dans la conversation.
