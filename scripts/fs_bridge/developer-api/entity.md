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
# Entity

This page documents the public entity search helpers.

## New Names

Use these names for new code:

```lua
FWB.Entity.Object.Nearby(extras)
FWB.Entity.Object.Closest(extras)
FWB.Entity.Player.Nearby(extras)
FWB.Entity.Player.Closest(extras)
FWB.Entity.Ped.Nearby(extras)
FWB.Entity.Ped.Closest(extras)
FWB.Entity.Vehicle.Nearby(extras)
FWB.Entity.Vehicle.Closest(extras)
```

## Direct Exports

```lua
exports['fs_bridge']:GetNearbyObjects(extras)
exports['fs_bridge']:GetClosestObject(extras)
exports['fs_bridge']:GetNearbyPlayers(extras)
exports['fs_bridge']:GetClosestPlayer(extras)
exports['fs_bridge']:GetNearbyPeds(extras)
exports['fs_bridge']:GetClosestPed(extras)
exports['fs_bridge']:GetNearbyVehicles(extras)
exports['fs_bridge']:GetClosestVehicle(extras)
```

## Common Extras

```lua
local extras = {
    coords = GetEntityCoords(Cache.Ped),
    source = nil,
    maxDistance = 5.0,
    maxCount = 10,
    sortedByDistance = true,
    requireClearLos = false,
    model = `prop_bin_01a`,
    models = { `prop_bin_01a`, `prop_atm_01` },
    excludeModels = { `prop_rub_binbag_01` },
}
```

## Notes

- All public exported helpers take one `extras` table.
- `coords` should be passed through `extras.coords`.
- On server side you can pass `extras.source` to use that player's ped location.
- `maxDistance` defaults to `2.0`.
- `sortedByDistance` defaults to `true`.
- Deprecated flat wrappers like `FWB.GetNearbyObjects(...)` still exist only for compatibility.

