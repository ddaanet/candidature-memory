---
name: utiliser-les-skills-notion-proactivement
description: "Préférence skills Notion vs MCP brut, et sa limite dans le workflow candidature Claude Code"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 764ce0df-fef6-4621-a228-4383cd716188
---

Pour les opérations Notion générales sur claude.ai, utiliser les skills Notion de gestion (database-query, find, search, create-page) dès le premier appel, pas les outils MCP bruts.

**Why:** les skills encapsulent la procédure (fetch du schéma, tri, choix d'outil). Les outils MCP bruts demandent plusieurs allers-retours et du tâtonnement.

**How to apply:** pour une opération Notion générale, vérifier d'abord si un skill de gestion existe. Pour une recherche par titre exact, `page_size: 1`, les résultats suivants sont du bruit.

Limite 2026-06-16 : ne s'applique pas tel quel au workflow candidature sur Claude Code. Le skill candidature prescrit les outils `notion-*` MCP directement (notion-fetch, notion-create-pages, notion-update-page) sur des pages imbriquées, sans base de données (D-25). Les opérations Notion du workflow passent par un sous-agent, voir [[feedback_notion_subagent]], et naviguent depuis les IDs connus plutôt que notion-search, voir [[feedback_notion_nav]].
