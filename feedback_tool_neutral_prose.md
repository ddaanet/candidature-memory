---
name: feedback_tool_neutral_prose
description: "Contenu du skill en prose tool-neutre, pas de noms d'outils claude.ai (bash_tool, view, web_search)"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 84bf4794-fa2c-4e30-b63a-e1f0bede7006
---

Le contenu livré du skill (SKILL.md, references/) ne nomme pas les outils en jargon claude.ai. Préférer la prose tool-neutre : « lancer python3 ... » plutôt que « dans bash_tool », « charger references/X.md » plutôt que « view references/X.md », « une recherche web » plutôt que « web_search »/« web_fetch ».

Why: l'agent Claude Code connaît déjà ses outils. Les nommer en jargon hérité de claude.ai n'aide pas l'exécution et lit comme un résidu dans un plugin Claude Code pur. Décision prise en traitant les findings Minor de la revue de branche (commit 35b3e9c).

How to apply: en éditant le contenu du skill, laisser la phrase porter le sens de l'action plutôt que nommer l'outil. Exception encadrée : les noms de la couche navigateur (open_url, form_input) relèvent de D-40, hors périmètre tant que Plan C n'est pas livré. Voir [[feedback_corpus_context.md]] pour la contamination de style plus large.
