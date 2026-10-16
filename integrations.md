---
name: int-grations-et-configuration-locale
description: "Remote git SSH, `.gitmodules` url https vs SSH, `Permission denied (publickey)` à `/plugin install`, candidature-memory public, contenu du .gitignore"
metadata:
  node_type: memory
  type: reference
  updated: 2026-04-03
  originSessionId: ce2e7c14-083e-4d0c-85b1-cd9166fb4f33
  modified: 2026-10-16T14:06:25.817Z
---

# Intégrations et configuration locale

## Remote git

SSH uniquement pour le remote local : `git@github.com:ddaanet/candidature.git`.

Le sous-module `memory` est déclaré en https dans `.gitmodules` (`https://github.com/ddaanet/candidature-memory.git`), pendant que `.git/config` garde l'url SSH pour les pushes. `/plugin install` clone avec `--recurse-submodules`, une url SSH dans `.gitmodules` fait échouer l'installation en `Permission denied (publickey)` chez un utilisateur sans clé GitHub. Le dépôt `candidature-memory` est public, et l'utilisateur a confirmé que c'est voulu. Ne pas remettre d'url SSH dans `.gitmodules`.

## Sandbox et gitignore

Le `.gitignore` inclut `CLAUDE.local.md`, `dist/`, les fichiers datés `2026-*.md`, et `.DS_Store`.
