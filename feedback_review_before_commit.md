---
name: Relire avant de commiter
description: Ne jamais commiter sans avoir relu DESIGN.md et vérifié la cohérence des changements avec les décisions documentées
type: feedback
---

Ne pas commiter sans revue. Avant de proposer un commit, relire DESIGN.md et vérifier que les changements sont cohérents avec les décisions documentées. Les correctifs Notion ne sont pas une spécification suffisante : ils décrivent le quoi, DESIGN.md documente le pourquoi.

**Why:** L'utilisateur a constaté que les patches ont été appliqués mécaniquement depuis les correctifs sans vérifier la cohérence avec l'architecture documentée.

**How to apply:** Avant tout commit sur les fichiers du skill (SKILL.md, references/, DESIGN.md), relire DESIGN.md pour vérifier que les changements respectent les décisions existantes et identifier si de nouvelles décisions doivent être ajoutées.
