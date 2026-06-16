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

How to apply: la couche est réalisée. Le harnais LinkedIn vit dans
tools/linkedin-harness/ (Node, playwright-core, pas de navigateur bundlé).
Pour les autres sites, écrire un script .mjs ad hoc dans tmp/, l'exécuter
hors sandbox, lire stdout et les captures, itérer. Importer playwright-core
en export par défaut (module CommonJS, `import pkg from '.../playwright-core';
const { chromium } = pkg`), puis connectOverCDP sur http://127.0.0.1:9222.
Lancer le chromium visible via tools/linkedin-harness/launch.sh (profil
persistant, port CDP, écran :0), qui réutilise la session ouverte. Un
lancement en tête par le launcher Playwright échoue (Missing X server) même
avec DISPLAY=:0, passer par launch.sh. Pour une simple lecture, un chromium
headless avec executablePath /usr/bin/chromium suffit. Les pages rendues en
JavaScript (Gem) demandent d'attendre l'apparition du contenu, pas seulement
networkidle. references/site-ouverture.md reste MCP pour la cible Claude.ai
seulement. Voir DESIGN D-35.
