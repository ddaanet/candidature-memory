---
name: feedback_agent_reads_markdown
description: "L'agent lit du markdown ; JSON réservé aux entrées de script complexes"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 5ed57be0-b771-41e5-9cd0-a131c920f9ca
---

Sauf exception, ce que l'agent consomme est du markdown. Une sortie de script
destinée à l'agent (stdout d'un reducer, instruction de routage, état de repo)
s'imprime en markdown, pas en JSON. Le JSON ne sert qu'en entrée de script
complexe, par exemple une liste structurée de champs de formulaire passée en
argument, jamais comme medium de lecture de l'agent.

Why: le markdown est le medium natif de l'agent (SKILL.md, fichiers de phase
sont déjà du markdown). Lui faire parser du JSON en sortie de script le force
dans un format étranger sans gain. Le harnais LinkedIn (walk.mjs) imprime du
JSON, c'est l'ancien réflexe ; la règle diverge de lui sur la sérialisation,
pas sur le patron d'interaction CLI.

How to apply: quand un script embarqué (dispatch.py, futurs reducers) renvoie
une décision ou un état que l'agent doit suivre, formater la sortie en markdown
(titre nommant l'action, corps portant les paramètres, tableau pour un index).
Réserver le JSON aux arguments d'entrée structurés et complexes. Voir
[[feedback_corpus_context]] et [[workflow]].
