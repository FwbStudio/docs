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

This page documents server-side notifications.

`lua
FWB.Notify(source, argument)
exports['fs_bridge']:Notify(source, argument)
` 

The server helper forwards the notification to the target client.

