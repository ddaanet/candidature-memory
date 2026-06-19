---
name: projet-candidature
description: "Repo, version, contraintes de modèle, historique des refontes"
metadata: 
  node_type: memory
  type: reference
  updated: 2026-06-19
  originSessionId: 764ce0df-fef6-4621-a228-4383cd716188
---

# Projet candidature

Un skill de candidature assistée. Le contenu markdown est le produit. Public cible : non technique. Livré en deux cibles depuis une source unique `src/` : un plugin Claude Code (`skills/candidature/`, généré et versionné) et un `.skill` Claude.ai (`dist/`, releasé). Voir [[project_cc_plugin_migration]].

Repo GitHub public : https://github.com/ddaanet/candidature
Remote SSH : `git@github.com:ddaanet/candidature.git`

## Contrainte de modèle

SKILL.md, DESIGN.md, references/*.md : modifications uniquement en session Opus. Pas en Sonnet.

## Historique

- 2026-03-16 : premier commit, push SSH vers GitHub.
- 2026-03-16 au 2026-03-24 : développement du dispatcher, build system, références, versioning 0.1 à 0.3.2.
- 2026-03-24 : migration des plans vers Notion, config locale exclue du git.
- 2026-03-30 au 2026-03-31 : refonte v0.4. Extraction des phases en fichiers autonomes sous references/. Dispatcher promu SKILL.md à la racine. Fichiers renommés en français. Relecture structurée de tous les fichiers de contenu. Release v0.4.0 le 2026-03-31, merge dev vers main.
- 2026-04-03 : migration Notion. BDD Candidatures et Sites de candidature renommées avec préfixe "BDD". Candidatures extraites de la BDD comme sous-pages directes de "Recherche d'emploi" (propriétés migrées dans le corps). Suit modele-notion.md.
- 2026-04-24 : spec migration plugin Claude Code approuvée (`docs/superpowers/specs/2026-04-24-plugin-claude-code-design.md`).
- 2026-06-09 : harnais LinkedIn Playwright livré (`tools/linkedin-harness/`, Node + playwright-core, chromium à profil persistant et port CDP).
- 2026-06 : release v0.5.0, migration vers plugin Claude Code. Source unique `src/`, artefacts `skills/candidature/` et `.claude-plugin/plugin.json` générés et versionnés, préprocesseur awk à blocs target, `check.sh` garde-fou de dérive.
- 2026-06-16 : flux formulaire-driven étendu, étape Axes retirée de la préparation, axes alignés chez leurs consommateurs (DESIGN D-37). Résidu pré-Notion `suivi-retours.md` supprimé, replié dans `suivi.md`.
- 2026-06-19 : Phase 2 du pivot conçue et planifiée. Décision tranchée : le skill abandonne la cible claude.ai et Notion, devient un plugin Claude Code pur, stockage en fichiers locaux du repo Emploi ancré sur cwd, sentinelle `.candidature` versionnée, validateur de métadonnées. Renverse D-25 (Notion requis) et l'universalité NFR-1. Spec `docs/superpowers/specs/2026-06-19-phase2-pivot-plugin-fichiers-design.md`. Découpé en trois plans : A outillage (`init_repo.py`, `validate.py`, plan écrit et en cours d'exécution subagent-driven), B réécriture du skill (Opus), C harnais LinkedIn. Voir [[feedback_claude_ai_camisole]].
