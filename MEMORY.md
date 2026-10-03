# Mémoire du projet candidature

Index des fichiers mémoire. Ne pas écrire de contenu ici — pointer vers les fichiers.

Dernière consolidation : 2026-06-16

## Index

- [project.md](project.md) — Repo, contraintes de modèle, historique (plugin Claude Code pur, fichiers locaux, reducer de contrôle de flux 12FA D-46, v0.7.0)
- [workflow.md](workflow.md) — Conventions git, build mono-cible (src/ → skills/), release via just release, check.sh, règles de prose
- [integrations.md](integrations.md) — Remote git SSH, contenu du .gitignore
- [feedback_scope.md](feedback_scope.md) — Ce repo = skill uniquement, la recherche d'emploi vit dans le repo Emploi
- [feedback_oqlf.md](feedback_oqlf.md) — OQLF comme arbitre des anglicismes + table des termes tranchés
- [feedback_corpus_context.md](feedback_corpus_context.md) — Tout texte dans le contexte contamine la sortie
- [feedback_tool_neutral_prose.md](feedback_tool_neutral_prose.md) — Contenu du skill en prose tool-neutre, pas de jargon claude.ai (bash_tool, view, web_search)
- [feedback_agent_reads_markdown.md](feedback_agent_reads_markdown.md) — L'agent lit du markdown ; JSON réservé aux entrées de script complexes
- [feedback_clipboard.md](feedback_clipboard.md) — Pas de clipboard (xclip/pbcopy), /dev/tty bloqué
- [feedback_no_stderr_redirect.md](feedback_no_stderr_redirect.md) — Jamais de 2>/dev/null sans justification documentée
- [feedback_sandbox_git_branch_ops.md](feedback_sandbox_git_branch_ops.md) — Ops git de branche écrivant un fichier deny-sandbox : « Device or resource busy », lancer sandbox off
- [feedback_replace_all.md](feedback_replace_all.md) — replace_all dangereux sur mots courts (sous-chaînes)
- [feedback_annotations.md](feedback_annotations.md) — Annotations [état]/[outil:...] fuient dans les messages candidat
- [feedback_review_before_commit.md](feedback_review_before_commit.md) — Relire DESIGN.md et vérifier cohérence avant tout commit
- [feedback_tdd_batch.md](feedback_tdd_batch.md) — TDD batch pour le scaffolding trivial, rouge-vert strict pour la vraie logique
- [feedback_reuse_agents.md](feedback_reuse_agents.md) — SendMessage vers un agent existant plutôt que relancer un nouveau
- [feedback_playwright_not_mcp.md](feedback_playwright_not_mcp.md) — Couche navigateur via harnais Playwright local + CDP, pas le MCP
- [feedback_claude_ai_camisole.md](feedback_claude_ai_camisole.md) — Compatibilité claude.ai = carcan dépassé, ne pas la réflexe-préserver
- [project_cc_plugin_migration.md](project_cc_plugin_migration.md) — Migration plugin Claude Code livrée en v0.5.0
- [project_super_sdd_cached.md](project_super_sdd_cached.md) — Plugin de réutilisation d'agents SDD, éval A/B en cours sur le plan candidature
- [project_emploi_usage_findings.md](project_emploi_usage_findings.md) — Retours d'usage Emploi : sentinelle absente, refus migrés sans canal/date, statut en texte libre
- [user_blog.md](user_blog.md) — Blog ddaa.net, contenu technique, sociologie des choix tech

## Faits clés en un coup d'œil

Repo : https://github.com/ddaanet/candidature (public, SSH)
Modèle requis pour SKILL.md / DESIGN.md / references : Opus uniquement
Version courante : 0.8.0 (plugin Claude Code pur `skills/candidature/`, stockage fichiers locaux, source unique `src/`). Contrôle de flux dans un reducer Python embarqué `src/scripts/dispatch.py` (D-46), pas dans l'inférence de l'agent. Notion et cible claude.ai abandonnés. Harnais de dev uv + pytest (`.venv`/`uv.lock` non versionnés), tests via `.venv/bin/pytest`
Édition du skill : modifier `src/`, jamais les artefacts `skills/`. Reconstruire (`./build/build.sh`) et committer, sinon `check.sh` signale la dérive
