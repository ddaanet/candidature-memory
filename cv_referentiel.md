---
name: cv-referentiel
description: Emplacement et format du CV référentiel de David Allouche pour les candidatures
metadata: 
  node_type: memory
  type: reference
  originSessionId: 62425de3-9f37-44d7-88a6-2107678db851
---

Le CV référentiel est désormais en DOCX dans `/Users/david/code/Emploi/cv/` :
`David Allouche CV en.docx` et `David Allouche CV fr.docx`. Le DOCX est le
nouveau référentiel, édité avec LibreOffice (export Pages d'origine retouché).
C'est le format le plus simple pour laisser l'agent retoucher le CV. Les PDF
sous `/Users/david/code/ddaanet/src/` sont des exports du blog, pas la source
à éditer.

Sur Claude Code, ce répertoire n'est pas un working directory par défaut.
L'ajouter avec `/add-dir /Users/david/code/Emploi/` au besoin.

Le CV doit tenir sur une page. Le référentiel le fait pile, sans marge, donc
tout ajout net oblige à récupérer des lignes ailleurs.

Outillage installé : `defusedxml`, `lxml`, LibreOffice (`soffice`), poppler
(`pdftoppm`, `pdffonts`, `pdfinfo`). `pandoc` reste absent. Éditer le DOCX avec
le skill `document-skills:docx` (unpack XML, édition par Edit, repack).

Rendu fidèle, piège fontconfig : les fontes du CV sont Helvetica Neue (corps,
puces) et Century Gothic (titres), fontes Apple présentes dans
`/Users/david/code/devddaanet/fonts/` et enregistrées via la config fontconfig
de l'utilisateur. Convertir en PDF avec le vrai `HOME` et un profil isolé
(`-env:UserInstallation=file:///.../tmp/lo-profile`). Forcer `HOME=tmp` casse
la résolution des fontes, LibreOffice substitue par NotoSerif (métriques plus
larges) et la pagination devient fausse. Vérifier avec `pdffonts` que le PDF
embarque HelveticaNeue et CenturyGothic, pas NotoSerif.

Promotion 2026-06-14 : `David Allouche CV en.docx` porte l'entrée Agentic
enrichie (plugins Claude Code, guardrails, gitlore). L'ancienne version est
archivée dans `Ancien/David Allouche CV en 2026-06-14.docx`. Le `.pages` et le
FR ne sont pas mis à jour. Le PDF EN a été régénéré depuis le docx.

Promotion 2026-06-17 : corps EN enrichi (Intuition : « large Python platform
(200 klocs) with reusable libraries » ; Canonical : « Launchpad, a distributed
Python developer-collaboration platform, code review and CI »). Tient toujours
sur une page. PDF EN régénéré. `.pages` et FR non mis à jour.

Le répertoire `/Users/david/code/Emploi/cv/` est désormais un dépôt git qui
versionne l'**expansion XML** des docx (dossiers `cv-en/`, `cv-fr/`), pas les
docx en binaire. Les docx sont en `.gitignore` ; PDF, `.pages`, diplômes sont
versionnés en blob. Une version par commit (historique linéaire pour `cv-en/`).
Éditer via le skill `document-skills:docx` : unpack vers `cv-en/`, Edit du XML,
`pack.py` vers le docx. Convertir en PDF hors sandbox (soffice a besoin du pipe)
avec un profil isolé sous `tmp/`, et vérifier `pdffonts` (HelveticaNeue +
CenturyGothic, pas NotoSerif).

Voir [[feedback_scope.md]] pour le périmètre.
