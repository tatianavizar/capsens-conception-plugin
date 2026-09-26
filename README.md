# Capsens × Claude — Kit Mission de Conception

Plugin Cowork pour mener des missions de conception produit avec Claude comme co-PM.

## Skills disponibles

| Skill | Quand l'utiliser |
|-------|-----------------|
| **init-mission** | En tout début de mission — crée tout le workspace |
| **session-start** | Au début de chaque conversation Claude sur le projet |
| **workshop-prep** | 24-48h avant chaque atelier client |
| **workshop-debrief** | Juste après chaque atelier — transcription tl;dv ou notes brutes → CR + mémoire |
| **fetch-transcript** | Récupérer une transcription tl;dv brute (appelé par workshop-debrief) |
| **write-project-brief** | Après le kick-off — brief projet + plan des briefs (BF-01, BF-02…) |
| **write-brief** | Pour chaque brief fonctionnel — PRD au format Capsens, dev-ready |
| **consistency-check** | Tous les 3-4 workshops + avant le chiffrage |
| **session-end** | En fin de session — met à jour mémoire, synthèse et index |
| **verticale-metier** | Chargé automatiquement si le projet a une verticale (ex : fintech) — vocabulaire, règles récurrentes, risques types |

## Conventions

Les conventions (nommage, numérotation `Dn` / `Qn` / `BF-NN`, statuts, dates) sont
écrites dans le `CLAUDE.md` que `init-mission` génère à la racine de chaque projet.

## Intégration tl;dv (optionnel mais recommandé)

Ce plugin se connecte à tl;dv pour récupérer automatiquement les transcriptions
de vos workshops et générer les CRs sans avoir à prendre de notes.

### Configuration
Activez le connecteur **tl;dv** dans les connecteurs claude.ai. Le plugin n'embarque aucun
serveur MCP tiers.

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
5. `"Rédige le brief projet"` → brief projet + plan des briefs
6. `"Prochain brief"` → brief fonctionnel suivant du plan

Pour chaque workshop :
- Avant : `"Prépare le workshop N sur [sujet]"` → trame avec timing et questions
- Après : `"Je rentre du workshop"` → Claude récupère la transcription tl;dv et rédige le CR

En fin de session : `"On s'arrête là"` → mémoire, synthèse, SESSIONS_INDEX et INDEX mis à jour automatiquement

## Philosophie

**Claude produit, le CDP valide et décide.**
Aucun document ne quitte le dossier local sans validation explicite du CDP.

## Basé sur

Une mission de conception Capsens de 10 semaines (15 briefs fonctionnels, prototype React,
24 templates email, brief exécutif complet), puis consolidé sur les missions suivantes (v1.2.0).
