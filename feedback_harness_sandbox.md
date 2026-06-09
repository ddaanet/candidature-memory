---
name: feedback-harness-sandbox
description: Les commandes du harnais navigateur et les appels Notion REST doivent tourner hors sandbox sur le serveur
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 8534bebf-21de-4d15-8eec-559e5beaddd0
---

Sur le serveur DigitalOcean, lancer les commandes du harnais LinkedIn qui
attachent le navigateur (sonde, walk.mjs) et les appels REST Notion avec
`dangerouslyDisableSandbox: true`.

Why: Le sandbox des commandes Bash est isolé en espace de noms PID et réseau. Il
ne voit que quelques processus, jamais le chromium du serveur, et ne joint pas
`127.0.0.1:9222` ni `api.notion.com`. Le navigateur n'est pas lancé par
`launch.sh` mais par le service systemd utilisateur `chromium-playwright`
(DISPLAY :99, CDP 127.0.0.1:9222, profil `~/.config/chromium-playwright`), qui
dépend de KasmVNC. Provisionné par ansible (`devddaanet`, tags browser et vnc).

How to apply: Diagnostiquer avant de contourner. Un `ECONNREFUSED` sur 9222 peut
venir du sandbox ou d'un navigateur absent. Vérifier d'abord les processus et
ports visibles (`ps -e`, `ss -ltn`). Si seuls quelques processus apparaissent et
qu'aucun service hôte n'est visible, c'est l'isolation du sandbox, et le
contournement est justifié par cette preuve, pas par supposition. Voir
[[project-linkedin-walker]] et [[feedback-playwright-not-mcp]].
