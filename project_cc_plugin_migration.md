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

How to apply: Plan implémenté inline le 2026-06-10 sur dev (neuf
commits, e36352d..30a7c06, plus 55b54a5 dans claude-plugins pour
l'entrée marketplace). Source canonique sous src/, préprocesseur awk
build/preprocess.awk, build à deux cibles (skills/candidature versionné
pour Claude Code, dist/candidature.skill pour Claude.ai), garde-fou de
dérive dans check.sh (vert). La couche navigateur (spec §5) est
réconciliée avec le harnais réel tools/linkedin-harness/. Écart au plan
corrigé : la boucle de références internes de check.sh teste l'existence
sous src/ (les refs markdown restent runtime-relatives). Reste à faire,
manuel et hors sandbox : merge dev vers main en --no-ff puis
./build/build.sh --bump minor pour cuter v0.5.0 et synchroniser la
version de l'entrée marketplace (0.5.0 y est déjà inscrit, VERSION
encore à 0.4.0 jusqu'au bump). Les tâches qui touchent src/SKILL.md,
src/references/*.md et DESIGN.md exigent une session Opus. Le triage
d'offres en masse et les scripts Playwright réutilisables sont hors
périmètre v1.

Note : le plan porte la date 2026-06-10, pas 2026-04-24 comme le
référence [[project_super_sdd_cached]]. Ce pointeur d'éval A/B est à
corriger quand l'éval reprend.
