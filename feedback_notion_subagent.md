---
name: feedback-notion-subagent
description: "Déléguer les opérations Notion à un sous-agent, pas la boucle principale"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 764ce0df-fef6-4621-a228-4383cd716188
---

Pour les opérations Notion du workflow candidature (lecture de structure,
création et mise à jour de pages, archivage de candidature, capture site),
passer par un sous-agent plutôt que d'appeler les outils `notion-*`
directement depuis la boucle principale. Demandé le 2026-06-16.

**Why:** les `notion-fetch` renvoient des pages entières et polluent le
contexte de la boucle principale. La boucle garde les décisions de contenu,
le sous-agent exécute la mécanique d'écriture et ne rend que les URLs et un
résumé.

**How to apply:** dispatcher un sous-agent general-purpose avec les
identifiants de page et le contenu exact à écrire. Lui imposer la discipline
`backend-write` (fetch de chaque cible avant d'écrire, ne rien écraser,
naviguer depuis les IDs et pas notion-search, voir [[feedback_notion_nav]]).
Pour un suivi dans la même session, réutiliser le sous-agent existant par
SendMessage plutôt que d'en relancer un, voir [[feedback_reuse_agents]].

Piège observé le 2026-06-16 : un sous-agent lancé en teammate de fond
exécute bien les écritures, mais sa réponse finale inline n'est pas livrée
au lead. Elle reste son tour de sortie, et le lead ne reçoit que des
notifications d'inactivité, jamais le compte rendu. Imposer au sous-agent de
terminer par un SendMessage explicite vers le lead (to: team-lead ou main)
contenant le compte rendu et les URLs des pages touchées. À défaut, ne pas
attendre, vérifier l'état directement dans Notion par notion-fetch.
