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
# Client

This page documents the client-side clipboard helper.

`lua
FWB.SetClipBoard(text)
` 

Bridge currently uses ox_lib clipboard support when available. If the value is not a string, nothing happens.

