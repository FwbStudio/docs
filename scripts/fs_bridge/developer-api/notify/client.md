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

This page documents client-side notifications.

`lua
FWB.Notify(argument)
exports['fs_bridge']:Notify(argument)
` 

If rgument is a string, Bridge converts it into { description = argument }. Common fields include 	itle, description, 	ype, position, and duration.

