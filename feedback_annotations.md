---
name: Annotations de section remontent dans les messages
description: Les tags [état], [outil:...], [choix], [prompt] dans les titres de section fuient dans les messages candidat
type: feedback
---

Les annotations entre crochets dans les titres de section (`[état]`, `[outil: notion-fetch]`, `[choix]`, `[prompt]`) remontent dans les messages visibles par le candidat. Ce n'est pas propre.

**Why:** L'agent reproduit les titres de section dans sa communication. Un titre "## 3.1 Orientation `[état]`" peut apparaître tel quel dans un message au candidat.

**How to apply:** Supprimer ces annotations des titres de section dans tous les fichiers de phase et de référence. Si l'information est nécessaire pour l'agent, la placer dans le corps de la section, pas dans le titre.
