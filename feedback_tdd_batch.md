---
name: feedback_tdd_batch
description: "TDD batch pragmatique pour le scaffolding trivial, rouge-vert strict réservé à la vraie logique"
metadata: 
  node_type: memory
  type: feedback
  updated: 2026-06-19
  originSessionId: 1c5173bf-df99-4082-ad7d-4a7ecac1dec7
---

# TDD batch pour le scaffolding, strict pour la logique

Dans un plan d'implémentation, un script de scaffolding trivial peut grouper ses
assertions en un seul cycle (tous les tests écrits ensemble, un rouge contre le
module absent, une implémentation, tout vert). Pas besoin d'un cycle rouge-vert
par assertion quand elles testent une seule behavior.

Le rouge-vert strict est réservé à la seule pièce de vraie logique. Exemple vu :
l'idempotence d'un `init_repo`. Pour qu'un test d'idempotence soit un vrai cycle,
l'implémentation doit d'abord écrire sans garde, le test rougit parce que la
seconde passe écrase, puis on ajoute le garde `if not exists` et il passe au vert.
Si l'implémentation pose le garde d'emblée, le test ne rougit jamais : c'est un
test de caractérisation, à nommer comme tel dans le plan, pas un cycle TDD.

Why : l'enjeu d'un scaffolding trivial ne justifie pas la cérémonie d'un cycle
par test. Mais un test qui ne peut pas échouer contre le code visé n'apporte pas
la garantie d'un cycle TDD, et le dire honnêtement évite qu'une revue le prenne
pour un cycle manqué.

How to apply : grouper les tests d'une behavior unique en un cycle. Identifier la
pièce de vraie logique et lui donner son rouge franc, en partant d'une
implémentation naïve si nécessaire. Étiqueter les tests de caractérisation.
