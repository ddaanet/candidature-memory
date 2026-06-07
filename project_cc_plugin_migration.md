---
name: Migration plugin Claude Code
description: Spec approuvée pour livrer candidature comme plugin Claude Code en parallèle du .skill Claude.ai
type: project
originSessionId: 0113c2c2-ce23-48eb-86c2-7bd8eb3af807
---
Spec validée le 2026-04-24 dans
`docs/superpowers/specs/2026-04-24-plugin-claude-code-design.md`
(commit 619152d sur dev). Cible de livraison v0.5.0.

Why: La limite de tours de Claude.ai bloque les tâches longues (notamment
triage d'offres). Claude Code en local (poste ou droplet VNC) lève la
contrainte et ouvre la voie à des scripts Playwright personnalisés.

Décisions clés, résumé : (1) dépôt candidature restructuré, src/
canonique et skills/candidature/ généré + versionné ; (2) préprocesseur
awk avec blocs `<!-- target: claude-ai|claude-code -->` parce que le
cache plugin Claude Code est read-only, pas de lifecycle hook à
l'installation ; (3) racine Notion stockée dans CLAUDE.local.md sur
Claude Code (pattern déjà prévu par la spec 2026-03-30) ; (4) couche
navigateur scaffoldée Playwright, scripts incrémentaux ; (5) entrée
ajoutée dans `ddaanet/claude-plugins/.claude-plugin/marketplace.json`
à chaque release.

How to apply: Prochaine étape = writing-plans pour détailler
l'implémentation. Le triage d'offres en masse et les scripts Playwright
réutilisables sont hors périmètre v1.
