# FWB.Player.Vehicle

`FWB.Player.Vehicle` groups the player-focused client vehicle helpers for nearby search, closest vehicle lookup, and vehicle key actions.

## Public Calls

```lua
FWB.Player.Vehicle.NearBy(extras)
FWB.Player.Vehicle.Closest(extras)
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)
```

<details>
<summary><strong>Nearby And Closest Vehicle</strong></summary>

Short description: Search nearby vehicles from the local player position without needing to pass the player coords yourself.

Signature:

```lua
FWB.Player.Vehicle.NearBy(extras)
FWB.Player.Vehicle.Closest(extras)

exports.fs_bridge:GetPlayerNearbyVehicles(extras)
exports.fs_bridge:GetPlayerClosestVehicle(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Trim result list for `NearBy` |
| `sortedByDistance` | `boolean` | Default `true` |
| `includePlayerVehicle` | `boolean` | Include the current player vehicle |
| `model` | `number|string` | Optional model filter |

Returns:

- `FWB.Player.Vehicle.NearBy(extras)` -> table of nearby vehicle entries
- `FWB.Player.Vehicle.Closest(extras)` -> vehicle entity id or `nil`

Example usage:

```lua
local nearby = FWB.Player.Vehicle.NearBy({
    maxDistance = 8.0,
    includePlayerVehicle = false
})

local closestVehicle = FWB.Player.Vehicle.Closest({
    maxDistance = 5.0
})

print(nearby[1] and nearby[1].plate, closestVehicle)
```

Notes:

- the public function name is `NearBy` with the current Bridge casing
- nearby entries include `vehicle`, `coords`, `distance`, `model`, and `plate`

</details>

<details>
<summary><strong>Give And Remove Vehicle Keys</strong></summary>

Short description: Give or remove keys for a vehicle through the active vehicle keys integration.

Signature:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)

exports.fs_bridge:GiveCarKeyPlayer(vehicle)
exports.fs_bridge:RemoveCarKeyPlayer(vehicle)
```

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity id |

Returns:

- compatibility-specific key result

Example usage:

```lua
local vehicle = FWB.Player.Vehicle.Closest({
    maxDistance = 5.0
})

if vehicle then
    FWB.Player.Vehicle.Keys.Give(vehicle)
end
```

Notes:

- this uses the active vehicle keys resource selected by Bridge
- if you need the active keys resource name, use `FWB.Vehicle.Keys.ResourceName()`

</details>
