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

This page documents the server-side logger helper.

`lua
FWB.Log.Create(source, event, message, ...)
exports['fs_bridge']:CreateLog(source, event, message, ...)
` 

Bridge routes logs into the active logger integrations or your override flow.

