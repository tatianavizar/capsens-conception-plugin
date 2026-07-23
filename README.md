# Capsens × Claude — Kit Mission de Conception

Plugin Claude Code pour mener des missions de conception produit avec Claude comme co-PM.

## Installation

```
/plugin marketplace add tatianavizar/capsens-conception-plugin
/plugin install capsens-conception
```

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
