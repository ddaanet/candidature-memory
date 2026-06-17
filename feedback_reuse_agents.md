---
name: Réutiliser les sous-agents existants
description: Continuer un sous-agent via SendMessage plutôt que d'en lancer un nouveau quand il a déjà le contexte
type: feedback
originSessionId: ccae90d5-48a6-4d8e-b627-b0389b926f45
---
Quand un sous-agent vient de terminer une tâche et qu'on veut lui donner une tâche connexe, utiliser SendMessage pour le relancer avec son contexte intact plutôt que de créer un nouvel agent qui refait toutes les lectures.

Why: Un agent qui vient de lire 16 pages Notion a tout en mémoire. En lancer un nouveau force 16 appels API redondants. Le cache de prompts Anthropic récompense aussi la réutilisation.

How to apply: Après complétion d'un sous-agent, vérifier si la tâche suivante bénéficierait du contexte accumulé. Si oui, SendMessage vers l'agent existant.

Cas particulier SDD (subagent-driven-development) : la règle s'applique aux trois rôles, pas seulement à l'implementer. Réutiliser `impl`, `spec-reviewer`, `quality-reviewer` à travers les tâches d'un plan, jusqu'à un plafond de contexte (~150k tokens) avant respawn. L'ordre spec → quality reste séquentiel dans une tâche (les deux reviewers ne tournent jamais en parallèle sur le même diff). Hypothèse en cours d'évaluation par le plugin `super-sdd-cached`.

Le plafond de contexte ne se respecte pas tout seul. Observé le 2026-06-16 sur une longue tâche Notion mécanique : un sous-agent Sonnet à qui on dit « arrête-toi avant la limite » ne s'autolimite pas et crashe (un agent a explosé à 176k). Pour un travail long et répétitif, le lead doit borner la session par un nombre d'opérations explicite (par exemple huit écritures vérifiées), faire écrire l'état dans un fichier de reprise, puis relayer vers un agent frais. Ne pas confier au sous-agent le soin de juger sa propre charge de contexte. Voir [[notion-reorder-technique]].
