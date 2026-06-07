---
name: replace_all dangereux sur mots courts
description: Ne pas utiliser replace_all sur des mots courts qui peuvent être sous-chaînes d'autres mots
type: feedback
---

Ne pas utiliser Edit replace_all sur des mots courts sans vérifier les sous-chaînes.

**Why:** Remplacement de "item" par "point" a cassé "explicitement" → "explicpointent" et "l'item" → "l'point" (contraction grammaticale incorrecte). Le remplacement aveugle sur un mot de 4 lettres touche des mots composés.

**How to apply:** Pour les remplacements globaux de mots courts, utiliser grep pour lister toutes les occurrences d'abord, vérifier les faux positifs (sous-chaînes, contractions), puis faire des Edit ciblés ou ajouter des bornes de mot au pattern.
