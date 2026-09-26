---
name: init-mission
description: >
  Initialise le workspace d'une nouvelle mission de conception Capsens. Crée l'arborescence
  standard, les fichiers mémoire, l'index, le CLAUDE.md projet et le prompt de brief fonctionnel.
  Déclencher quand le CDP dit : "nouvelle mission", "init mission", "démarre le projet",
  "crée le dossier projet", "kick-off [client]", "commence la mission pour [client]",
  "on démarre [nom projet]", ou équivalent.
---

# Init Mission

Initialise le workspace complet d'une nouvelle mission de conception Capsens.

## Ce que tu dois faire

1. **Demande les informations manquantes** si elles ne sont pas dans la requête :
   - Nom du projet (ex : "ACME", "MonClient")
   - Nom du client (société)
   - Nom du CDP Capsens
   - Verticale du projet (ex : fintech, proptech, autre)
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
   ├── _Archive/
   ├── CLAUDE.md
   ├── INDEX.md
   └── SESSIONS_INDEX.md
   ```

3. **Crée les fichiers de démarrage** :

   **CLAUDE.md** — règles projet chargées à chaque conversation :
   ```
   # [PROJET] — Règles projet

   Projet : [PROJET] · Client : [CLIENT] · CDP : [NOM CDP] · Verticale : [VERTICALE]

   ## Règles de travail
   - Toujours répondre et rédiger en français.
   - Claude rédige, le CDP valide : rien n'est publié (Slite, Notion, email, client)
     sans validation explicite du CDP. Sauvegarder localement → présenter → attendre.
   - Rôles uniquement, jamais de prénoms, dans tous les livrables.
   - V1 uniquement : tout ce qui relève d'une phase ultérieure va en "Hors scope V1".
   - Pas de design ni de technique dans les briefs fonctionnels.
   - Pas d'invention : une règle absente de la mémoire devient une question ouverte.
   - Le `.md` est la source de vérité ; un `.docx` / PDF n'est qu'un export.
   - On ne supprime jamais un fichier : un document remplacé part dans `_Archive/`.
   - `[PROJET]_Notes_Internes.md` est confidentiel : jamais cité dans un livrable.

   ## Conventions
   - Préfixe `[PROJET]_` sur tous les fichiers.
   - Dates dans le contenu : JJ/MM/AAAA. Dates dans les noms de fichiers : AAAA-MM-DD.
   - Workshops : `W[N]` = numéro de workshop (jamais un numéro de semaine).
   - Décisions : `Dn` (numérotation continue sur toute la mission).
   - Questions ouvertes : `Qn` (numérotation continue, identique mémoire ↔ briefs).
   - Briefs fonctionnels (= PRD) : `BF-01`, `BF-02`…, suivis dans `[PROJET]_Plan_Briefs.md`.
   - Features d'un brief : `001`, `002`… ; citées hors du brief sous la forme `BF-02 / 003`.
   - Statuts de document : 🔴 Draft / 🟡 En validation / 🟢 Validé.
   - Point tranché : jamais supprimé, barré → `~~Q3 — …~~ → tranché le JJ/MM/AAAA (D12)`.
   - Cases à cocher : `- [ ]`.
   ```

   **INDEX.md** — table des matières :
   ```
   # [PROJET] — Index des fichiers
   Mis à jour : [JJ/MM/AAAA]

   ## Par question fréquente
   | Je cherche… | Fichier |
   |-------------|---------|
   | Vue d'ensemble du projet | 00_Reference/[PROJET]_Synthese.md |
   | Toutes les décisions | 00_Reference/[PROJET]_Memoire.md |
   | Le périmètre de la mission | 01_Briefs_Fonctionnels/[PROJET]_Brief_Projet.md |
   | L'état des briefs | 01_Briefs_Fonctionnels/[PROJET]_Plan_Briefs.md |

   ## Par dossier
   ### 00_Reference/ — Mémoire & contexte
   | Fichier | Contenu | Statut |
   |---------|---------|--------|

   ### 01_Briefs_Fonctionnels/
   | Fichier | Contenu | Statut |
   |---------|---------|--------|

   ### 04_Workshops/
   | Fichier | Contenu | Statut |
   |---------|---------|--------|

   ## Archive
   | Fichier | Raison d'archivage | Date |
   |---------|--------------------|------|

   ## ⚠️ Points ouverts avant go-dev
   | # | Point | Bloque |
   |---|-------|--------|
   ```

   **SESSIONS_INDEX.md** — index des conversations :
   ```
   # [PROJET] — Index des conversations Claude
   Mis à jour : [JJ/MM/AAAA]
   Total : 1 conversation

   ## En cours
   | Session | Sujet | Statut |
   |---------|-------|--------|

   ## Par thème
   ### Briefs fonctionnels
   | Session | Produit | Fichier(s) |
   |---------|---------|------------|
   ### Workshops
   | Session | Produit | Fichier(s) |
   |---------|---------|------------|

   ## À reprendre
   | Sujet | Où on s'est arrêté | Session d'origine |
   |-------|--------------------|-------------------|

   ## Chronologie
   [S1 — JJ/MM/AAAA] → Workspace créé
   ```

   **00_Reference/[PROJET]_Synthese.md** — synthèse :
   ```
   # [PROJET] — Synthèse Projet
   Mis à jour : [JJ/MM/AAAA]
   Statut : Semaine 1 — Kick-off à faire
   Verticale : [VERTICALE]

   ## En une phrase
   [À compléter après le kick-off]

   ## Contexte
   ## Équipe
   - Client : [CLIENT]
   - CDP Capsens : [NOM CDP]

   ## État d'avancement
   - [ ] Phase 1 — Cadrage
   - [ ] Phase 2 — Discovery
   - [ ] Phase 3 — Conception
   - [ ] Phase 4 — Validation
   - [ ] Phase 5 — Finalisation

   ## Ce qui est acté
   [Rien pour l'instant]

   ## Prochaine étape
   [Kick-off]

   ## Ce qui reste à décider
   [Tout — mission non démarrée]

   ## Stack technique
   [À définir]
   ```

   **00_Reference/[PROJET]_Memoire.md** — mémoire :
   ```
   # [PROJET] — Mémoire Projet
   Mis à jour : [JJ/MM/AAAA]
   Source de vérité : toutes les décisions de la mission.

   ## Contexte & vision produit
   [À compléter après kick-off]

   ## Personas & utilisateurs
   [À compléter]

   ## Pipeline / Processus métier
   [À compléter]

   ## Décisions produit
   Format de chaque décision :
   ### Dn — [Titre] (JJ/MM/AAAA, W[N] ou session)
   - **Décision** : [ce qui est acté]
   - **Raison** : [pourquoi]
   - **Conséquence** : [ce que ça implique pour les features]
   - **Ce qui reste** : [éventuel reliquat → Qn]

   ### D1 — Démarrage de la mission ([JJ/MM/AAAA])
   - **Décision** : mission lancée.

   ## Stack technique
   [À définir]

   ## Points ouverts
   | # | Question | Impact | Décideur (rôle) | Statut |
   |---|----------|--------|-----------------|--------|

   ## Hors scope V1
   [Vide]

   ## Décisions abandonnées
   [Vide — chaque entrée : ~~Dn — titre~~ + raison de l'abandon + date]
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

4. **Confirme la création** en listant les fichiers créés, puis indique comment reprendre
   à la prochaine conversation : dire "reprends le projet [PROJET]" (skill `session-start`).
   Propose ensuite l'étape suivante : kick-off, puis brief projet et plan des briefs
   (skill `write-project-brief`).

## Important
- Utilise le nom du projet en MAJUSCULES pour le préfixe des fichiers (ex : ACME_, MON_CLIENT_)
- Le dossier 03_Emails/ n'est créé que si le CDP confirme que des emails sont dans le scope
- Notes_Internes.md doit toujours inclure l'avertissement CONFIDENTIEL
- La verticale est inscrite dans CLAUDE.md et dans la Synthèse ; si elle est inconnue, écris "non précisée"
