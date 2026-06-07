---
name: Utiliser les skills Notion proactivement
description: Toujours utiliser les skills Notion (database-query, find, create-page, etc.) plutôt que les outils MCP bruts pour les opérations Notion.
type: feedback
---

Utiliser les skills Notion (Notion:database-query, Notion:find, Notion:search, etc.) dès le premier appel, pas les outils MCP bruts.

**Why:** Les skills encapsulent la procédure (fetch schéma, tri, choix d'outil). Les outils MCP bruts demandent plusieurs allers-retours et du tâtonnement. L'utilisateur ne voit pas la liste des skills disponibles, c'est à l'agent de les connaître et de les invoquer proactivement.

**How to apply:** Pour toute opération Notion (lecture, requête, création, recherche), vérifier d'abord si un skill Notion existe avant de toucher aux outils MCP. Le skill database-query gère le tri et le filtrage proprement. Pour une recherche par titre exact (notion-search), utiliser `page_size: 1` : les résultats suivants sont du bruit.
