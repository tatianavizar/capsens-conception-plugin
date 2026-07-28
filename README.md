# Capsens × Claude — Kit Mission de Conception

Plugin Cowork pour mener des missions de conception produit avec Claude comme co-PM.

## Skills disponibles

| Skill | Quand l'utiliser |
|-------|-----------------|
| **init-mission** | En tout début de mission — crée tout le workspace |
| **session-start** | Au début de chaque conversation Claude sur le projet |
| **workshop-prep** | 24-48h avant chaque atelier client |
| **workshop-debrief** | Juste après chaque atelier — transcription tl;dv ou notes brutes → CR + mémoire |
| **write-brief** | Pour documenter chaque feature validée |
| **consistency-check** | Tous les 3-4 workshops + avant le brief exécutif final |
| **session-end** | En fin de session — met à jour mémoire, synthèse et index |

## Intégration tl;dv (optionnel mais recommandé)

Ce plugin se connecte à tl;dv pour récupérer automatiquement les transcriptions
de vos workshops et générer les CRs sans avoir à prendre de notes.

### Prérequis
- Compte tl;dv Business ou Enterprise
- Clé API : https://tldv.io/app/settings/personal-settings/api-keys

### Configuration
Ajoutez la variable d'environnement dans les réglages de Cowork :

```
TLDV_API_KEY=votre_clé_api
```

Une fois configuré, le skill `workshop-debrief` détecte automatiquement tl;dv,
liste vos réunions récentes, et récupère la transcription complète avant de
rédiger le CR.

### Sans tl;dv
Le plugin fonctionne sans tl;dv — le skill `workshop-debrief` travaille alors
sur les notes brutes que vous collez dans la conversation.

## Démarrage rapide

1. Installez ce plugin dans Cowork
2. Ouvrez un dossier de travail pour votre mission
3. `"Nouvelle mission pour [NomClient], je m'appelle [prénom]"` → workspace créé
4. Faites votre kick-off, collez vos notes → mémoire et synthèse projet générées

Pour chaque workshop :
- Avant : `"Prépare le workshop N sur [sujet]"` → trame avec timing et questions
- Après : `"Je rentre du workshop"` → Claude récupère la transcription tl;dv et rédige le CR

En fin de session : `"On s'arrête là"` → mémoire, synthèse, SESSIONS_INDEX et INDEX mis à jour automatiquement

## Philosophie

**Claude produit, le PM valide et décide.**
Aucun document ne quitte le dossier local sans validation explicite du PM.

## Basé sur

Mission WiiM (Capsens, Fév–Mai 2026) — 10 semaines de conception, 15 briefs fonctionnels,
prototype React, 24 templates email, brief exécutif complet.
Voir le document de méthodologie : `Capsens_Claude_Kit_Mission_Conception.docx`
