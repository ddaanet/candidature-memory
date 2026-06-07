---
name: Pas de 2>/dev/null sans justification
description: Ne jamais rediriger stderr vers /dev/null sans raison documentée. Les erreurs sont toujours importantes.
type: feedback
---

Ne jamais utiliser `2>/dev/null` sans une justification précise et documentée.

**Why:** Les redirections stderr masquent des erreurs réelles. Le cas concret : un `grep -oP` cassé sur GNU grep 3.11 était silencieusement ignoré, rendant un scan de références inopérant.

**How to apply:** Si une commande peut échouer, gérer l'erreur explicitement (test d'existence, code retour, message). Si stderr est bruyant mais inoffensif, documenter pourquoi dans un commentaire à côté de la redirection.
