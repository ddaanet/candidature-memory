---
name: git status toujours hors sandbox
description: Appeler `git status` avec le sandbox désactivé. Cette règle ne concerne que git status, pas les autres commandes git.
type: feedback
---

Toujours exécuter `git status` avec `dangerouslyDisableSandbox: true`.

**Why:** Dans le sandbox, le répertoire `.claude` est monté avec des artefacts (fichiers de périphérique `agents`, `commands`, `hooks`, `skills` appartenant à `nobody:nogroup`) qui n'existent pas sur le système de fichiers réel. Sandboxé, `git status` les voit et pollue la sortie. Hors sandbox, ils disparaissent et le statut reflète le vrai dépôt. C'est aussi pourquoi le bloc « Artefacts sandbox » du `.gitignore` a été retiré : il ne servait qu'à masquer ces entrées dans un `git status` sandboxé.

**How to apply:** `git status` → toujours `dangerouslyDisableSandbox: true`. Les autres commandes git (`add`, `diff`, `commit`, `log`) restent sandboxées par défaut.
