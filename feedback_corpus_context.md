---
name: Tout texte dans le contexte est un corpus
description: Les règles anti-contamination s'appliquent à tous les fichiers chargés, y compris le dispatcher et les fichiers techniques
type: feedback
---

Tout texte dans le contexte de l'agent est un corpus qui contamine la sortie. Les règles anti-contamination de CLAUDE.md (pas de gras, pas de fragments à puces, pas de tirets cadratins, pas de points-virgules) s'appliquent aussi au dispatcher et aux fichiers techniques, pas seulement aux fichiers de phase.

**Why:** L'agent ne distingue pas "instructions techniques" de "exemples de prose". Une liste numérotée dans le dispatcher peut se retroire reproduite dans un texte généré pour le candidat. Voir DESIGN.md D-32.

**How to apply:** Lors de la rédaction ou relecture de tout fichier chargé par le skill (dispatcher, phases, références), appliquer les mêmes règles de style que pour les fichiers de contenu. Préserver la lisibilité machine (Sonnet) par des phrases courtes avec une action par phrase, pas par de la structure à reproduire.
