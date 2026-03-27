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

This page documents the server-side FWB.Ped runtime.

`lua
FWB.Ped.Create(options)
FWB.Ped.Update(handle, updates)
FWB.Ped.Remove(handle)
FWB.Ped.Get(handle)
FWB.Ped.GetAll()
FWB.Ped.Clear(resource)

exports['fs_bridge']:CreatePed(options)
exports['fs_bridge']:UpdatePed(handle, updates)
exports['fs_bridge']:RemovePed(handle)
exports['fs_bridge']:GetPed(handle)
exports['fs_bridge']:GetAllPeds()
exports['fs_bridge']:ClearPeds(resource)
` 

Server-created peds are server-managed. Important server-only options include source, spawnSource, and emoveOnDisconnect.

