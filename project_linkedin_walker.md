---
name: project-linkedin-walker
description: "Parcours de cartes LinkedIn, spec et plan d'implémentation prêts sur dev (2026-06-09)"
metadata: 
  node_type: memory
  type: project
  originSessionId: ce00b777-559a-4922-9f28-c0ffa57758ba
---

Le parcours de cartes LinkedIn (card-walker) réalise FR-3 du harnais
(`tools/linkedin-harness/`). Spec et plan committés sur `dev` le 2026-06-09 :
`docs/superpowers/specs/2026-06-09-linkedin-card-walker-design.md` et
`docs/superpowers/plans/2026-06-09-linkedin-card-walker.md`. Reste à exécuter
le plan, dix tâches, cœur pur en TDD puis adaptateurs Playwright et Notion
vérifiés en réel.

Décisions de conception arrêtées. Le flux de contrôle vit dans le driver
(`walk.mjs`), l'agent ne rend qu'une décision par carte parmi shortlist, reject,
stop (principe 12-factor-agents, voir [[feedback-12factor]]). Écriture Notion
directe par jeton d'intégration REST, pas le MCP. Une page candidature par offre
retenue, pas de page de session (déléguée au skill de passation). Un flux par
session, choisi à la main.

L'écriture Notion vise la page hub Recherche d'emploi
(`32fec6ce980181558099fd4f5ac9ed46`), qui est la racine candidature réelle.
Contrairement à ce qu'affirme `modele-notion.md`, cette page porte du contenu
propre (sections Situation et Candidatures, un résumé par offre). Correction de
`modele-notion.md` tracée dans `TODO.md`, à faire juste après le parcours.
