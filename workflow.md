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

Le hook commit-msg (`.git/hooks/gitmoji.sh` + `gitmoji.cfg`, non versionnés) n'accepte que 13 préfixes conventionnels qu'il réécrit en emoji : feat ✨, fix 🐛, docs 📝, style 🎨, refactor ♻️, perf ⚡️, test ✅, build 📦️, ci 👷, chore 🔧, revert ⏪️, hotfix 🚑️, release 🔖. Un message qui commence déjà par un de ces emoji passe tel quel. Tout le reste est rejeté, y compris 🔀 et 💡 que la table de CLAUDE.md liste pourtant. Le hook lit `$2` comme source-type pour sauter les merges, mais commit-msg ne reçoit pas ce second argument, donc même un commit de merge doit utiliser un préfixe ou emoji accepté. Le sujet d'un merge décrit son contenu réel avec le préfixe qui correspond (📝/docs pour un merge de correctifs de doc, ✨/feat pour une fonctionnalité), jamais un 🔀 vide qui ne dit rien de ce qui est livré. Le repo Emploi a le même hook (le plan supposait à tort qu'il n'en avait pas).

Quirk sandbox : pendant un merge ou un changement de branche, l'écriture de `.claude/settings.json` échoue avec « Device or resource busy ». Lancer ces opérations git unsandboxed.

## Build

Source unique `src/` (SKILL.md, references/, scripts/). `./build/build.sh` assemble une seule cible, le plugin Claude Code `skills/candidature/`, via le préprocesseur awk (`build/preprocess.awk`, substitution `{{VERSION}}`). La version est lue depuis `.claude-plugin/plugin.json`, la source de vérité. Le build ne génère plus le manifeste et ne tague plus. La cible claude.ai (`dist/*.skill`) est abandonnée, les fichiers restants sous `dist/` sont des reliques que le build ne reproduit plus.

`skills/candidature/` est versionné et lu tel quel depuis le cache plugin (pas de build au checkout). Toujours éditer `src/`, jamais l'artefact. Après édition, reconstruire et committer src plus skills ensemble, sinon `check.sh` échoue sur la dérive. Le manifeste `plugin.json` est une source éditée à la main, hors garde de dérive, mais son champ version est verrouillé par un hook version-guard : seul `just release` le bumpe.

Release via le toolkit `plugin-dev` (vendu en subtree, importé dans le `justfile`) : `just release {patch|minor|major}` reconstruit, vérifie via `just precommit`, bumpe la version, commite, tague, pousse, crée la release GitHub, puis répercute la version dans la marketplace `claude-plugins`.

Exécution réelle : la recette exige d'être sur `main`, un arbre propre, `plugin.json` égal au dernier tag, et un dépôt marketplace propre (`MARKETPLACE_DIR` dans `.envrc`, pointe sur `/Users/david/code/claude-plugins`). Elle demande une confirmation interactive via `read`, qui ne fonctionne pas dans Claude Code : passer `--yes` en second argument (`just release minor --yes`). Push et `gh` exigent le réseau hors sandbox. Après release, `main` porte le commit de bump que `dev` n'a pas : fast-forward `dev` sur `main` et pousser, sinon les branches divergent et le `plugin.json` de `dev` reste sur l'ancienne version.

## Qualité de prose (règles de contamination)

Tout le contenu du skill suit ces règles (violations = contamination du style de sortie). Pas de gras markdown. Pas de tirets cadratins ni demi-cadratins. Pas de fragments à puces sans sujet. Pas de points-virgules. Contenu en français naturel, anglicismes vérifiés via OQLF.

`check.sh` vérifie automatiquement la contamination de style, le préprocesseur, les références internes, le build, et la dérive des artefacts versionnés par rapport à `src/`.
