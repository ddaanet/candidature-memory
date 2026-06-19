# Mémoire du projet candidature

Index des fichiers mémoire. Ne pas écrire de contenu ici — pointer vers les fichiers.

Dernière consolidation : 2026-06-16

## Index

- [project.md](project.md) — Repo, contraintes de modèle, historique (Phase 2 pivot livré sur main, plugin Claude Code pur, fichiers locaux, v0.5.1)
- [workflow.md](workflow.md) — Conventions git, build (source src/ → skills/ + .skill), check.sh, règles de prose
- [integrations.md](integrations.md) — Notion MCP, CLAUDE.md comme ancrage, passation sous projet, remote git SSH
- [feedback_scope.md](feedback_scope.md) — Ce repo = skill uniquement, pas la recherche d'emploi
- [feedback_notion_skills.md](feedback_notion_skills.md) — Skills Notion vs MCP brut (limite : candidature Claude Code utilise MCP)
- [feedback_notion_nav.md](feedback_notion_nav.md) — Naviguer depuis CLAUDE.md Notion, pas notion-search
- [feedback_notion_subagent.md](feedback_notion_subagent.md) — Déléguer les opérations Notion à un sous-agent
- [notion_reorder_technique.md](notion_reorder_technique.md) — Réordonner des sous-pages Notion par réécriture en petits groupes (le MCP ne déplace pas dans le parent)
- [feedback_oqlf.md](feedback_oqlf.md) — OQLF comme arbitre des anglicismes + table des termes tranchés
- [feedback_corpus_context.md](feedback_corpus_context.md) — Tout texte dans le contexte contamine la sortie
- [feedback_clipboard.md](feedback_clipboard.md) — Pas de clipboard (xclip/pbcopy), /dev/tty bloqué
- [feedback_no_stderr_redirect.md](feedback_no_stderr_redirect.md) — Jamais de 2>/dev/null sans justification documentée
- [feedback_sandbox_git_branch_ops.md](feedback_sandbox_git_branch_ops.md) — Ops git de branche écrivant un fichier deny-sandbox : « Device or resource busy », lancer sandbox off
- [feedback_replace_all.md](feedback_replace_all.md) — replace_all dangereux sur mots courts (sous-chaînes)
- [feedback_annotations.md](feedback_annotations.md) — Annotations [état]/[outil:...] fuient dans les messages candidat
- [feedback_notion_destructive.md](feedback_notion_destructive.md) — Énumérer toutes les entrées BDD avant DROP COLUMN
- [feedback_review_before_commit.md](feedback_review_before_commit.md) — Relire DESIGN.md et vérifier cohérence avant tout commit
- [feedback_tdd_batch.md](feedback_tdd_batch.md) — TDD batch pour le scaffolding trivial, rouge-vert strict pour la vraie logique
- [feedback_reuse_agents.md](feedback_reuse_agents.md) — SendMessage vers un agent existant plutôt que relancer un nouveau
- [feedback_playwright_not_mcp.md](feedback_playwright_not_mcp.md) — Couche navigateur via harnais Playwright local + CDP, pas le MCP
- [feedback_claude_ai_camisole.md](feedback_claude_ai_camisole.md) — Compatibilité claude.ai = carcan dépassé, ne pas la réflexe-préserver
- [project_cc_plugin_migration.md](project_cc_plugin_migration.md) — Migration plugin Claude Code livrée en v0.5.0
- [project_super_sdd_cached.md](project_super_sdd_cached.md) — Plugin de réutilisation d'agents SDD, éval A/B en cours sur le plan candidature
- [user_blog.md](user_blog.md) — Blog ddaa.net, contenu technique, sociologie des choix tech

## Faits clés en un coup d'œil

Repo : https://github.com/ddaanet/candidature (public, SSH)
Notion MCP : actif, auth via claude.ai (pas de clé API locale)
Config Notion : page CLAUDE.md dans Notion (330ec6ce-9801-81e4-a49f-de2583fef716) + `CLAUDE.local.md` (exclu du git)
Modèle requis pour SKILL.md / DESIGN.md / references : Opus uniquement
Version courante : 0.5.1 (plugin Claude Code pur `skills/candidature/`, stockage fichiers locaux, source unique `src/`). Pivot Phase 2 livré sur main (2e77bc3). Notion et cible claude.ai abandonnés
Édition du skill : modifier `src/`, jamais les artefacts `skills/`. Reconstruire (`./build/build.sh`) et committer, sinon `check.sh` signale la dérive
