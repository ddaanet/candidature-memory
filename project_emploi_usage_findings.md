---
name: retours-d-usage-emploi-sur-le-skill
description: "Anomalies remontées par la première validation du skill sur les données réelles du repo Emploi (migration Notion vers fichiers), à traiter dans le skill."
metadata: 
  node_type: memory
  type: project
  updated: 2026-06-19
  originSessionId: 0d82c59a-a794-46bb-8fac-56af79d0a734
---

Le repo Emploi (`/Users/david/code/Emploi`) porte les données de candidature en fichiers depuis le pivot Phase 2. C'est le terrain d'usage réel du skill. Première session de validation, rapport du 2026-06-19, deux anomalies remontées :

1. Sentinelle `.candidature` (`format: 1`) absente à la racine d'Emploi. La structure existe (migration Notion en cours) mais le fichier manque, donc le skill ne reconnaît pas formellement le repo. La session Emploi n'a rien créé sans accord. Question ouverte : le skill doit-il créer la sentinelle automatiquement ou exiger l'accord ?

2. Anomalies de métadonnées du validateur : la plupart des anciens dossiers refus issus de la migration n'ont ni canal ni `date_reponse` ; le statut de symbiotic-security est en texte libre (« entretien recruteur passé, retour attendu ~2026-06-22 ») au lieu d'une valeur de l'ensemble reconnu.

**Why:** Ces remontées viennent d'un usage réel, pas d'un test. Elles posent des questions de conception du skill : tolérance du validateur aux données migrées, politique de création de la sentinelle.

**How to apply:** Traiter ces points comme des retours candidats pour le skill (validateur, sentinelle), pas comme du nettoyage de données dans Emploi (hors périmètre de ce repo, voir [[scope du projet candidature]]). Données Emploi à nettoyer côté session Emploi quand David le décidera.
