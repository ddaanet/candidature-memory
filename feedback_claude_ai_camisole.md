---
name: feedback_claude_ai_camisole
description: "La compatibilité claude.ai est un carcan que le skill candidature dépasse, pas une contrainte dure"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 789db2c7-9ba1-4737-b23f-798685c43718
---

L'utilisateur voit la compatibilité claude.ai comme une camisole, pas une
contrainte sacrée. Le skill s'en éloigne déjà en s'appuyant sur Notion requis
(D-25), le plugin Claude Code (D-33/D-34) et le harnais navigateur Playwright
(D-35), tous spécifiques à Claude Code et absents de claude.ai. NFR-5
(portabilité multi-plateforme) décrit une hypothèse d'origine dépassée.

Why: deux dérives de raisonnement à éviter. Ne pas bloquer une feature au
nom de la compatibilité claude.ai. Et ne pas transformer un constat de
l'utilisateur (« s'éloigne de la compatibilité ») en prescription inventée
(« doit rester compatible ») ni y ajouter un rationale qu'il n'a pas posé.

How to apply: quand une feature touche le handoff, la mémoire native, ou une
mécanique propre à Claude Code, ne pas réflexe-préserver claude.ai. Demander
si la portabilité compte encore pour ce point précis. Voir [[feedback_scope]].
