---
name: Workflow git et build
description: Conventions git (branches, commits, merge), build system, règles de prose
type: reference
updated: 2026-03-31
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

## Qualité de prose (règles de contamination)

Tout le contenu du skill suit ces règles (violations = contamination du style de sortie). Pas de gras markdown. Pas de tirets cadratins ni demi-cadratins. Pas de fragments à puces sans sujet. Pas de points-virgules. Contenu en français naturel, anglicismes vérifiés via OQLF.

`check.sh` vérifie automatiquement ces règles sur tous les fichiers de contenu et les références internes croisées.
