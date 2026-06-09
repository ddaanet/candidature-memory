---
name: project-linkedin-walker
description: "Parcours de cartes LinkedIn (FR-3) implémenté et vérifié en réel sur dev (2026-06-09)"
metadata: 
  node_type: memory
  type: project
  originSessionId: ce00b777-559a-4922-9f28-c0ffa57758ba
---

Le parcours de cartes LinkedIn (card-walker) réalise FR-3 du harnais
(`tools/linkedin-harness/`). Implémenté et vérifié en réel le 2026-06-09 sur
`dev`. Spec et plan dans `docs/superpowers/specs/` et `docs/superpowers/plans/`
du 2026-06-09.

Cœur pur en TDD (`lib/state.mjs`, `lib/record.mjs`, `lib/notion.mjs`), 21 tests,
`npm test` lance `node --test test/*.test.mjs` (le node 22 ne découvre pas un
répertoire nu). Adaptateurs `lib/stream-page.mjs` (Playwright) et `walk.mjs`
(CLI start, decide, status). Vérifié de bout en bout contre le flux recommended
et la racine Recherche d'emploi (`32fec6ce980181558099fd4f5ac9ed46`), page Notion
créée puis nettoyée, échappatoire stop confirmée.

Trois pièges du DOM vivant tranchés à l'essai. Le titre se lit sur le h1 du
détail scopé à `main`, le h1 de la bannière de confidentialité passait avant.
La bannière de consentement est refusée au chargement. L'avance se fait vers la
première carte dont le jobId n'est pas dans un ensemble `seen` porté par l'état,
parce que le clic sur un listitem nu ne navigue pas et qu'une carte écartée
reste en tête sous un état Undo.

Décisions arrêtées. Flux de contrôle dans le driver, agent réducteur sans état
(principe 12-factor-agents, voir [[feedback-12factor]]). Écriture Notion directe
par jeton REST, pas le MCP. Une page candidature par offre retenue, pas de page
de session. Un flux par session, choisi à la main. Exécution sur le serveur,
voir [[feedback-harness-sandbox]].

Suite immédiate, la tâche TODO de correction de `modele-notion.md` et
`notion-setup.md` (`TODO.md`), la racine porte du contenu propre, sections
Situation et Candidatures, et cinq sous-pages dont Passations, pas quatre.
