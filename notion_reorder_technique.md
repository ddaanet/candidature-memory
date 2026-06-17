---
name: notion-reorder-technique
description: "Réordonner des sous-pages Notion via réécriture de contenu par petits groupes, le MCP ne sait pas déplacer une page dans son parent"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 65a94fbe-f939-44f3-86c6-54642fedde16
---

Le MCP Notion n'a pas de primitive pour repositionner une page enfant dans
son parent. `notion-move-pages` vers le même parent est un no-op, et un
déplacement cross-parent ajoute toujours en fin. Pour réordonner des
sous-pages dans une page, il faut réécrire le contenu avec `update_content`.

Mécanique observée le 2026-06-16 (re-tri des conteneurs de passations et de
l'index des candidatures). Une entrée est un bloc lien `<page url="...">`
suivi d'un paragraphe de description séparé, les deux doivent se déplacer
ensemble. Le `<page url="...">` exact doit figurer dans le `new_str`, sinon
le garde-fou anti-suppression refuse l'édition.

Contrainte de fiabilité, démontrée : réécrire un gros groupe de blocs de
pages enfants (plus d'une vingtaine, ou tout groupe contenant une entrée
sans description) réapparie et orphelin les descriptions de façon non
déterministe. Réécrire de petits groupes où chaque entrée porte une
description est sûr. Astuce pour une entrée sans description : lui donner une
description provisoire le temps du tri, puis la retirer.

How to apply : trier par petits réordonnancements locaux (cinq entrées au
plus par écriture), diff minimal ancré sur les liens uniques juste avant et
juste après la fenêtre. Vérifier par re-fetch après chaque écriture
(nombre de pages inchangé, descriptions appariées, aucun orphelinage ni
doublon) et garder un point de restauration. Pièges de matching : les
apostrophes varient par entrée (U+2019 ou U+0027) et un NBSP U+00A0 se
confond avec un espace, copier le caractère exact du fetch, un échec
"different indentation" est presque toujours un mauvais caractère, pas une
vraie indentation. Déléguer à un sous-agent, voir [[feedback_notion_subagent]].

La convention d'ordre retenue évite tout cela pour les écritures courantes :
ajouter en fin, la plus récente en dernier, pas de repositionnement. Le
re-tri par réécriture ne sert qu'aux reprises ponctuelles d'un historique.
