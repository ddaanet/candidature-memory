---
name: Projet candidature
description: Repo, version, contraintes de modèle, historique des refontes
type: reference
updated: 2026-04-03
---

# Projet candidature

Un skill Claude.ai pour la candidature assistée. Le contenu markdown est le produit. Public cible : non technique.

Repo GitHub public : https://github.com/ddaanet/candidature
Remote SSH : `git@github.com:ddaanet/candidature.git`

## Contrainte de modèle

SKILL.md, DESIGN.md, references/*.md : modifications uniquement en session Opus. Pas en Sonnet.

## Historique

- 2026-03-16 : premier commit, push SSH vers GitHub.
- 2026-03-16 au 2026-03-24 : développement du dispatcher, build system, références, versioning 0.1 à 0.3.2.
- 2026-03-24 : migration des plans vers Notion, config locale exclue du git.
- 2026-03-30 au 2026-03-31 : refonte v0.4. Extraction des phases en fichiers autonomes sous references/. Dispatcher promu SKILL.md à la racine. Fichiers renommés en français. Relecture structurée de tous les fichiers de contenu. Release v0.4.0 le 2026-03-31, merge dev vers main.
- 2026-04-03 : migration Notion. BDD Candidatures et Sites de candidature renommées avec préfixe "BDD". Candidatures extraites de la BDD comme sous-pages directes de "Recherche d'emploi" (propriétés migrées dans le corps). Suit modele-notion.md.
