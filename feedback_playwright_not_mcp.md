---
name: Playwright scripts, pas le MCP, pour le contrôle navigateur
description: Préférence pour Playwright via scripts Bash plutôt que via le MCP pour la couche navigateur du skill candidature
type: feedback
originSessionId: 0113c2c2-ce23-48eb-86c2-7bd8eb3af807
---
Pour la couche navigateur du skill candidature sur Claude Code, utiliser
des scripts Playwright lancés via `Bash`, pas le MCP Playwright. Le MCP
reste acceptable comme secours pour l'exploration initiale si les
scripts se révèlent trop lourds à écrire dans le flux d'itération.

Why: L'utilisateur préfère les scripts locaux pour la flexibilité et
l'efficacité sur les tâches longues. La migration de Claude.ai vers
Claude Code est notamment motivée par la levée de la limite de tours
pour le triage d'offres, tâche où les scripts sont naturels. L'usage
d'un MCP pour un pattern scripté répétitif est un surcoût.

How to apply: Quand on conçoit ou étend la couche navigateur
(references/site-ouverture-playwright.md, scripts/playwright-*.py), on
rédige en termes de "produire un script, l'exécuter via Bash, lire la
sortie, itérer". Pas d'appels MCP Playwright dans les instructions de
la cible Claude Code. Le fichier `references/site-ouverture.md` reste
MCP pour la cible Claude.ai seulement.
