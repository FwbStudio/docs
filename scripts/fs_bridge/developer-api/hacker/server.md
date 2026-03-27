---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
---
# Server

This page documents the server-side hacker helpers.

`lua
FWB.Hacker.Kick(source, reason)
FWB.Hacker.Ban(source, reason)
exports['fs_bridge']:KickPlayer(source, reason)
exports['fs_bridge']:Ban(source, reason)
` 

Deprecated FWB.Kick and FWB.Ban still exist only for compatibility.

