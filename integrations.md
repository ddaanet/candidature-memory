---
name: Intégrations et configuration locale
description: Notion MCP, config CLAUDE.local.md, remote git SSH
type: reference
updated: 2026-04-03
---

# Intégrations et configuration locale

## Notion

Notion MCP (claude.ai Notion) gère l'authentification, pas de clé API locale.

La page Notion "CLAUDE.md" (330ec6ce-9801-81e4-a49f-de2583fef716) contient les liens vers les pages et BDD Notion partagées entre skills. Chargée en début de session via notion-fetch (pas notion-search). Le fichier `CLAUDE.local.md` (racine du repo, exclu du git) pointe vers cette page et documente les conventions Notion.

Protocole de session : charger la passation Notion en début de session, créer une passation en fin de session. Passations créées en sous-page de "Passations [projet]" sous le projet concerné. Projet "Recherche d'emploi" pour les candidatures (pas "/candidature" = le skill).

## Remote git

SSH uniquement : `git@github.com:ddaanet/candidature.git`.

## Sandbox et gitignore

Le `.gitignore` inclut `CLAUDE.local.md`, `dist/`, les fichiers datés `2026-*.md`, et `.DS_Store`.
