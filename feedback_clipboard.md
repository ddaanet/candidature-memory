---
name: Pas de clipboard depuis le sandbox
description: xclip/pbcopy nécessitent /dev/tty, bloqué par le sandbox. Ne pas essayer.
type: feedback
---

Ne pas essayer de copier dans le presse-papier (xclip, pbcopy, xsel). Ces
outils nécessitent /dev/tty qui est bloqué par le sandbox.

**Why:** Le sandbox bloque l'accès à /dev/tty. Les commandes échouent
systématiquement.

**How to apply:** Si l'utilisateur demande de copier quelque chose, afficher
le contenu directement pour qu'il puisse le copier lui-même.
