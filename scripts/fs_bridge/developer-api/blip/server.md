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

This page documents the server-side FWB.Blip runtime.

`lua
FWB.Blip.Create(options)
FWB.Blip.CreateMoving(options)
FWB.Blip.Update(handle, updates)
FWB.Blip.Toggle(handle, enabled)
FWB.Blip.Remove(handle)
FWB.Blip.Get(handle)
FWB.Blip.GetAll()
FWB.Blip.Clear(resource)

exports['fs_bridge']:CreateBlip(options)
exports['fs_bridge']:CreateMovingBlip(options)
exports['fs_bridge']:UpdateBlip(handle, updates)
exports['fs_bridge']:ToggleBlip(handle, enabled)
exports['fs_bridge']:RemoveBlip(handle)
exports['fs_bridge']:GetBlip(handle)
exports['fs_bridge']:GetAllBlips()
exports['fs_bridge']:ClearBlips(resource)
` 

Use source = -1 for everyone or a player source for one target client. Server moving blips can track sources, entities, vehicles, objects, and net ids.

