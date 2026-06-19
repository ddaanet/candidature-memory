---
name: workflow-git-et-build
description: "Conventions git (branches, commits, merge), build system, règles de prose"
metadata: 
  node_type: memory
  type: reference
  updated: 2026-06-16
  originSessionId: 764ce0df-fef6-4621-a228-4383cd716188
---

# Workflow git et build

## Branches

`main` : livrables uniquement, pas de brouillons.
`dev` : travail en cours, explorations, plans.

Merge `dev` → `main` en `--no-ff` pour les livrables de plus d'un commit, avec message rédigé (pas le message par défaut).
Un commit unique peut aller directement sur `main`.

## Messages de commit

Préfixe gitmoji. Courts et denses, centrés sur le "pourquoi". Table des emojis dans CLAUDE.md.

Le hook commit-msg (`.git/hooks/gitmoji.sh` + `gitmoji.cfg`, non versionnés) n'accepte que 13 préfixes conventionnels qu'il réécrit en emoji : feat ✨, fix 🐛, docs 📝, style 🎨, refactor ♻️, perf ⚡️, test ✅, build 📦️, ci 👷, chore 🔧, revert ⏪️, hotfix 🚑️, release 🔖. Un message qui commence déjà par un de ces emoji passe tel quel. Tout le reste est rejeté, y compris 🔀 et 💡 que la table de CLAUDE.md liste pourtant. Le hook lit `$2` comme source-type pour sauter les merges, mais commit-msg ne reçoit pas ce second argument, donc même un commit de merge doit utiliser un préfixe ou emoji accepté (un merge de livrable se fait en ✨/feat, pas 🔀). Le repo Emploi a le même hook (le plan supposait à tort qu'il n'en avait pas).

Quirk sandbox : pendant un merge ou un changement de branche, l'écriture de `.claude/settings.json` échoue avec « Device or resource busy ». Lancer ces opérations git unsandboxed.

## Build

Source unique `src/` (SKILL.md, references/, scripts/, plugin.json.tmpl). `./build/build.sh` produit deux cibles via le préprocesseur awk (`build/preprocess.awk`, blocs `<!-- target: claude-ai|claude-code -->`, substitution `{{VERSION}}`).

Cible plugin Claude Code : `skills/candidature/` et `.claude-plugin/plugin.json`, générés et versionnés, lus tels quels depuis le cache plugin (pas de build au checkout). Cible Claude.ai : `dist/candidature.skill`, zip non versionné, seul artefact releasé. `dist/candidature-dev.skill` est le stub dev.

Toujours éditer `src/`, jamais les artefacts `skills/`. Après édition, reconstruire et committer src plus skills ensemble, sinon `check.sh` échoue sur la dérive.

`./build/build.sh --bump minor` : incrémente VERSION, commite, tague, release GitHub (candidature.skill seul).

## Qualité de prose (règles de contamination)

Tout le contenu du skill suit ces règles (violations = contamination du style de sortie). Pas de gras markdown. Pas de tirets cadratins ni demi-cadratins. Pas de fragments à puces sans sujet. Pas de points-virgules. Contenu en français naturel, anglicismes vérifiés via OQLF.

`check.sh` vérifie automatiquement la contamination de style, le préprocesseur, les références internes, le build, et la dérive des artefacts versionnés par rapport à `src/`.
