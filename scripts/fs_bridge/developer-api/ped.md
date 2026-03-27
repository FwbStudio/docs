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
# Ped

This page documents the public `FWB.Ped` runtime.

## Public Calls

Client and server both expose:

```lua
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
```

## Return Values

- `CreatePed` returns `handle, netId, ped`
- `UpdatePed` returns `success, entry`
- `RemovePed` returns `success`

## Common Options

- `model`
- `coords`
- `heading`
- `pedType`
- `freeze`
- `invincible`
- `blockEvents`
- `health`
- `armour`
- `weapon`
- `ammo`
- `scenario`
- `animation`
- `voice`
- `combat`
- `attachments`
- `target`
- `point`
- `marker`
- `blip`
- `resource`

## Server-only Options

- `source`
- `spawnSource`
- `removeOnDisconnect`

## Example

```lua
local handle, netId, ped = exports['fs_bridge']:CreatePed({
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true,
    invincible = true,
    blockEvents = true,
    weapon = 'WEAPON_PISTOL',
    ammo = 120
})

print(handle, netId, ped)
```

