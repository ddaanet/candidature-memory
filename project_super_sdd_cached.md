---
name: Plugin super-sdd-cached
description: Plugin Claude Code dérivé de superpowers SDD avec réutilisation d'agents nommés, en cours d'évaluation A/B
type: project
originSessionId: ccae90d5-48a6-4d8e-b627-b0389b926f45
---
Plugin développé en parallèle de candidature à
`/Users/david/code/super-sdd-cached/`. Spec validée le 2026-04-24,
fichier `docs/superpowers/specs/2026-04-24-plugin-design.md` (commit
498bf14 sur `main` du nouveau dépôt git local, pas encore poussé).

Why: La skill `superpowers:subagent-driven-development` dispatche un
subagent frais par tâche et par review. Le pattern SendMessage
(feedback_reuse_agents) s'applique aux trois rôles SDD (`impl`,
`spec-reviewer`, `quality-reviewer`) et permet de bénéficier du cache
Anthropic. À tester empiriquement avant PR upstream.

How to apply: Après écriture du plan via writing-plans, livrer dans
l'ordre : plugin (skill + 3 prompts), analyseur de logs `analyze.py`,
deux worktrees `eval/sdd-vanilla` et `eval/sdd-cached` sur candidature
au HEAD de `dev` (619152d). L'opérateur lance les deux runs SDD
manuellement dans deux terminaux. `analyze.py` parse les JSONL des deux
sessions et produit un comparatif markdown (coût, taux de cache,
wall-clock par tâche, boucles de review). Si l'éval valide
l'hypothèse, PR sur upstream superpowers, pas publication marketplace
ddaanet.

Évaluation cible : exécution du plan candidature
`docs/superpowers/plans/2026-04-24-plugin-claude-code.md` sur les deux
worktrees. Plan candidature mis en pause avant dispatch Task 1.
