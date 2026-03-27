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
# Blip

This page documents the public `FWB.Blip` runtime.

## Public Calls

Client and server both expose:

```lua
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
```

## Notes

- `CreateBlip(options)` is used for static coordinate blips.
- `CreateMovingBlip(options)` is used for moving players, peds, vehicles, objects, or net ids.
- Server-side blips can target everyone with `source = -1` or one player with a player source.
- Moving blips clamp `updateTime` to at least `5000` milliseconds.
- Radius support is available on both static and moving blips.

## Example

```lua
local handle = exports['fs_bridge']:CreateBlip({
    coords = vec3(215.76, -810.12, 30.73),
    title = 'Garage',
    id = 357,
    scale = 0.9,
    color = 3,
    shortrange = false
})

local data = exports['fs_bridge']:GetBlip(handle)
print(data and data.handle)
```

