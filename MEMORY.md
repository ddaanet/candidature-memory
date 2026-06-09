# Mémoire du projet candidature

Index des fichiers mémoire. Ne pas écrire de contenu ici — pointer vers les fichiers.

Dernière consolidation : 2026-04-03

## Index

- [project.md](project.md) — Repo, contraintes de modèle, historique (v0.4.0 released, migration Notion 2026-04-03)
- [workflow.md](workflow.md) — Conventions git, build (SKILL.md à la racine), check.sh, règles de prose
- [integrations.md](integrations.md) — Notion MCP, CLAUDE.md comme ancrage, passation sous projet, remote git SSH
- [feedback_scope.md](feedback_scope.md) — Ce repo = skill uniquement, pas la recherche d'emploi
- [feedback_notion_skills.md](feedback_notion_skills.md) — Toujours utiliser les skills Notion, pas les outils MCP bruts
- [feedback_notion_nav.md](feedback_notion_nav.md) — Naviguer depuis CLAUDE.md Notion, pas notion-search
- [feedback_oqlf.md](feedback_oqlf.md) — OQLF comme arbitre des anglicismes + table des termes tranchés
- [feedback_corpus_context.md](feedback_corpus_context.md) — Tout texte dans le contexte contamine la sortie
- [feedback_clipboard.md](feedback_clipboard.md) — Pas de clipboard (xclip/pbcopy), /dev/tty bloqué
- [feedback_no_stderr_redirect.md](feedback_no_stderr_redirect.md) — Jamais de 2>/dev/null sans justification documentée
- [feedback_git_status_unsandboxed.md](feedback_git_status_unsandboxed.md) — git status toujours hors sandbox (artefacts .claude sandbox)
- [feedback_replace_all.md](feedback_replace_all.md) — replace_all dangereux sur mots courts (sous-chaînes)
- [feedback_annotations.md](feedback_annotations.md) — Annotations [état]/[outil:...] fuient dans les messages candidat
- [feedback_notion_destructive.md](feedback_notion_destructive.md) — Énumérer toutes les entrées BDD avant DROP COLUMN
- [feedback_review_before_commit.md](feedback_review_before_commit.md) — Relire DESIGN.md et vérifier cohérence avant tout commit
- [feedback_reuse_agents.md](feedback_reuse_agents.md) — SendMessage vers un agent existant plutôt que relancer un nouveau
- [feedback_playwright_not_mcp.md](feedback_playwright_not_mcp.md) — Couche navigateur via scripts Playwright Bash, pas le MCP
- [project_cc_plugin_migration.md](project_cc_plugin_migration.md) — Spec plugin Claude Code approuvée 2026-04-24, cible v0.5.0
- [project_super_sdd_cached.md](project_super_sdd_cached.md) — Plugin de réutilisation d'agents SDD, éval A/B en cours sur le plan candidature
- [project_linkedin_walker.md](project_linkedin_walker.md) — Parcours de cartes LinkedIn (FR-3) implémenté et vérifié sur dev (2026-06-09)
- [feedback_harness_sandbox.md](feedback_harness_sandbox.md) — Harnais navigateur et Notion REST hors sandbox (isolation PID/réseau du serveur)
- [feedback_12factor.md](feedback_12factor.md) — Boucles agentiques selon 12-factor-agents, flux de contrôle dans le code
- [user_blog.md](user_blog.md) — Blog ddaa.net, contenu technique, sociologie des choix tech

## Faits clés en un coup d'œil

Repo : https://github.com/ddaanet/candidature (public, SSH)
Notion MCP : actif, auth via claude.ai (pas de clé API locale pour le skill)
Harnais LinkedIn : écriture Notion par jeton d'intégration REST (NOTION_TOKEN ou ~/.config/candidature/notion.env), distinct du MCP
Config Notion : page CLAUDE.md dans Notion (330ec6ce-9801-81e4-a49f-de2583fef716) + `CLAUDE.local.md` (exclu du git)
Modèle requis pour SKILL.md / DESIGN.md / references : Opus uniquement
