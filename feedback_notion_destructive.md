---
name: Notion - opérations destructives sur BDD
description: Toujours énumérer toutes les entrées avant de modifier le schéma d'une BDD Notion. Ne jamais DROP COLUMN avant migration complète vérifiée.
type: feedback
---

Avant toute opération destructive sur une BDD Notion (DROP COLUMN, suppression de propriétés), énumérer exhaustivement toutes les entrées et vérifier que chaque entrée a été migrée.

**Why:** Session 2026-04-03, migration BDD Candidatures. Recherche limitée à 10 résultats, conclusion hâtive à 5 candidatures, DROP COLUMN exécuté. 11 candidatures restantes ont perdu leurs propriétés. Récupération via restauration manuelle par l'utilisateur dans l'UI Notion.

**How to apply:** Pour les migrations BDD Notion :
1. Paginer les recherches (page_size=25, relancer si résultats = max).
2. Distinguer entrées de premier niveau et sous-pages.
3. Écrire les données dans le corps AVANT de déplacer.
4. Déplacer TOUTES les entrées.
5. Vérifier que la BDD est vide (recherche retourne 0).
6. Seulement alors modifier le schéma.
