---
name: workflow-git-et-build
description: "Conventions git (branches, commits, merge), build system, règles de prose"
metadata: 
  node_type: memory
  type: reference
  updated: 2026-06-09
  originSessionId: b19e2ea4-d774-477a-992f-f5ec25680661
---

# Workflow git et build

## Branches

`main` : livrables uniquement, pas de brouillons.
`dev` : travail en cours, explorations, plans.

Merge `dev` → `main` en `--no-ff` pour les livrables de plus d'un commit, avec message rédigé (pas le message par défaut).
Un commit unique peut aller directement sur `main`.

## Messages de commit

Préfixe gitmoji. Courts et denses, centrés sur le "pourquoi". Table des emojis dans CLAUDE.md.

## Build

`SKILL.md` est le dispatcher à la racine. Le build copie SKILL.md avec substitution de `__VERSION__`. Le script `build/build.sh` produit deux artefacts dans `dist/`. Seul `candidature.skill` est releasé.

`./build/build.sh --bump minor` : incrémente VERSION, commite, tague, release GitHub.

## Handoffs versionnés

`.claude/handoff-task.md` est versionné (commité avec le travail en cours) : gitlore fournit le contexte qui le rend utile à travers les sessions. `.claude/handoff-session` est gitignoré, c'est un pointeur transitoire vers le transcript de session.

## Qualité de prose (règles de contamination)

Tout le contenu du skill suit ces règles (violations = contamination du style de sortie). Pas de gras markdown. Pas de tirets cadratins ni demi-cadratins. Pas de fragments à puces sans sujet. Pas de points-virgules. Contenu en français naturel, anglicismes vérifiés via OQLF.

`check.sh` vérifie automatiquement ces règles sur tous les fichiers de contenu et les références internes croisées.
