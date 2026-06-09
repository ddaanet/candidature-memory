---
name: feedback-12factor
description: "Construire les boucles agentiques selon les 12-factor-agents, max de flux de contrôle dans le code"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: ce00b777-559a-4922-9f28-c0ffa57758ba
---

L'utilisateur construit les boucles agentiques selon les 12-factor-agents
(HumanLayer). Le principe central qu'il a invoqué : le maximum de flux de
contrôle va dans le script, pas dans le modèle. L'agent est un réducteur sans
état, il ne rend qu'une décision structurée par tour, le driver possède
l'avance, la pagination, le compte, l'arrêt et les effets.

Why: il l'a dit explicitement en concevant le parcours LinkedIn, et a corrigé
une formulation où je qualifiais le driver de réducteur (c'est l'agent qui
réduit, pas le driver).

How to apply: pour toute boucle pilotée par agent dans ce dépôt, mettre le flux
de contrôle déterministe dans le code et réduire le rôle du modèle à un jugement
structuré par item. Voir [[project-linkedin-walker]].
