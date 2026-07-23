---
name: init-mission
description: >
  Initialise le workspace d'une nouvelle mission de conception Capsens. Crée l'arborescence
  standard, les fichiers mémoire, l'index et le prompt de brief fonctionnel.
  Déclencher quand le PM dit : "nouvelle mission", "init mission", "démarre le projet",
  "crée le dossier projet", "kick-off [client]", "commence la mission pour [client]",
  "on démarre [nom projet]", ou équivalent.
---

# Init Mission

Initialise le workspace complet d'une nouvelle mission de conception Capsens.

## Ce que tu dois faire

1. **Demande les informations manquantes** si elles ne sont pas dans la requête :
   - Nom du projet (ex : "WIIM", "MonClient")
   - Nom du client (ex : "Florent Albero")
   - Nom du PM (ex : "Tatiana")
   - Y a-t-il des emails transactionnels dans le scope ? (pour créer 03_Emails/)

2. **Crée l'arborescence standard** dans le dossier de travail :
   ```
   NOMPROJET/
   ├── 00_Reference/
   ├── 01_Briefs_Fonctionnels/
   ├── 02_Technique/
   ├── 03_Emails/          ← uniquement si emails dans scope
   ├── 04_Workshops/
   │   ├── CR/
   │   └── Trames/
   ├── 05_UX_Design/
   └── _Archive/
   ```

3. **Crée les fichiers de démarrage** :

   **INDEX.md** — table des matières vide avec structure type :
   ```
   # [PROJET] — Index des fichiers
   Mis à jour : [date]

   ## Par question fréquente
   | Je cherche… | Fichier |
   |-------------|---------|
   | Vue d'ensemble du projet | 00_Reference/[PROJET]_Synthese.md |
   | Toutes les décisions | 00_Reference/[PROJET]_Memoire.md |

   ## Par dossier
   ### 00_Reference/ — Mémoire & contexte
   | Fichier | Contenu | Statut |
   ```

   **SESSIONS_INDEX.md** — index des conversations :
   ```
   # [PROJET] — Index des conversations Claude
   Mis à jour : [date]
   Total : 1 conversation

   ## En cours
   | Session | Sujet | Statut |

   ## Par thème
   ### Briefs fonctionnels
   | Session | Produit | Fichier(s) |
   ### Workshops
   | Session | Produit | Fichier(s) |

   ## Chronologie
   [Session init] → Workspace créé
   ```

   **00_Reference/[PROJET]_Synthese.md** — synthèse vide :
   ```
   # [PROJET] — Synthèse Projet
   Mis à jour : [date]
   Statut : Semaine 1 — Kick-off à faire

   ## En une phrase
   [À compléter après le kick-off]

   ## Contexte
   ## Équipe
   - Client : [NOM CLIENT]
   - PM Capsens : [NOM PM]

   ## État d'avancement
   - [ ] Phase 1 — Cadrage
   - [ ] Phase 2 — Discovery
   - [ ] Phase 3 — Conception
   - [ ] Phase 4 — Validation
   - [ ] Phase 5 — Finalisation

   ## Ce qui est acté
   [Rien pour l'instant]

   ## Ce qui reste à décider
   [Tout — mission non démarrée]

   ## Stack technique
   [À définir]
   ```

   **00_Reference/[PROJET]_Memoire.md** — mémoire vide :
   ```
   # [PROJET] — Mémoire Projet
   Mis à jour : [date]
   Source de vérité : toutes les décisions de la mission.

   ## Contexte & vision produit
   [À compléter après kick-off]

   ## Personas & utilisateurs
   [À compléter]

   ## Pipeline / Processus métier
   [À compléter]

   ## Décisions produit
   ### Pré-mission
   - Démarrage de la mission le [date]

   ## Stack technique
   [À définir]

   ## Points ouverts
   [À alimenter]

   ## Décisions abandonnées
   [Vide — mission non démarrée]
   ```

   **00_Reference/[PROJET]_Notes_Internes.md** — notes confidentielles :
   ```
   # [PROJET] — Notes Internes Capsens
   🔒 CONFIDENTIEL — Ne jamais partager avec le client.

   ## Observations sur le client
   ## Risques identifiés
   ## Hypothèses non vérifiées
   ## Points de vigilance
   ```

   **00_Reference/[PROJET]_Prompt_Brief_Fonctionnel.md** — prompt réutilisable :
   Crée ce fichier en adaptant le template de la référence `prompt-brief-template.md`
   avec le nom du projet et du client.

4. **Confirme la création** en listant les fichiers créés et en donnant la commande SESSION START pour la prochaine conversation.

## Important
- Utilise le nom du projet en MAJUSCULES pour le préfixe des fichiers (ex : WIIM_, CLIENT_)
- Le dossier 03_Emails/ n'est créé que si le PM confirme que des emails sont dans le scope
- Notes_Internes.md doit toujours inclure l'avertissement CONFIDENTIEL
- Termine en expliquant comment démarrer la prochaine session avec le Protocole SESSION START
