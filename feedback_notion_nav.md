---
name: Navigation Notion depuis CLAUDE.md, pas notion-search
description: Ne pas utiliser notion-search pour naviguer entre pages Notion. Naviguer depuis la page CLAUDE.md comme point d'ancrage.
type: feedback
---

Ne pas utiliser notion-search pour naviguer entre les pages Notion. Naviguer depuis la page CLAUDE.md (330ec6ce-9801-81e4-a49f-de2583fef716) qui référence les pages et BDD.

**Why:** notion-search est une recherche sémantique, pas un annuaire fiable. Elle peut renvoyer des résultats dans le désordre, manquer des pages, ou mélanger les projets. Le cas concret : chercher "Correctifs candidature" renvoyait le bon résultat, mais chercher "dernière passation" renvoyait des passations anciennes.

**How to apply:** En début de session, charger la page CLAUDE.md Notion via notion-fetch. Naviguer ensuite via les liens qu'elle contient (mention-page, database). Pour trouver une page spécifique sous un projet, fetch le projet puis naviguer dans ses enfants. Réserver notion-search aux cas où on cherche du contenu (pas de la structure).
