# FWB.Entity

`FWB.Entity` is the clean public surface for nearby lookups and front-coords helpers.

## Public Calls

```lua
FWB.Entity.Object.Nearby(extras)
FWB.Entity.Object.Closest(extras)
FWB.Entity.Player.Nearby(extras)
FWB.Entity.Player.Closest(extras)
FWB.Entity.Ped.Nearby(extras)
FWB.Entity.Ped.Closest(extras)
FWB.Entity.Vehicle.Nearby(extras)
FWB.Entity.Vehicle.Closest(extras)
FWB.Entity.GetFrontCoords(extras)
FWB.Entity.FrontCoords(extras)
FWB.Player.GetFrontCoords(extras)
```

## Common Extras Shape

```lua
{
    coords = GetEntityCoords(Cache.Ped),
    source = nil,
    maxDistance = 5.0,
    maxCount = 10,
    sortedByDistance = true,
    requireClearLos = false,
    model = `prop_bin_01a`,
    models = { `prop_bin_01a`, `prop_atm_01` },
    excludeModels = { `prop_rub_binbag_01` }
}
```

<details>
<summary><strong>Nearby Objects</strong></summary>

Short description: Find nearby props or world objects.

Signature:

```lua
FWB.Entity.Object.Nearby(extras)
FWB.Entity.Object.Closest(extras)
exports.fs_bridge:GetNearbyObjects(extras)
exports.fs_bridge:GetClosestObject(extras)
```

Returns:

- list of entries or one closest entry

Example usage:

```lua
local atm = FWB.Entity.Object.Closest({
    coords = GetEntityCoords(Cache.Ped),
    maxDistance = 3.0,
    model = `prop_atm_01`
})
```

Notes:

- object entries include `entity`, `coords`, `distance`, and `model`

</details>

<details>
<summary><strong>Nearby Players</strong></summary>

Short description: Find nearby players for menus, interactions, or checks.

Signature:

```lua
FWB.Entity.Player.Nearby(extras)
FWB.Entity.Player.Closest(extras)
```

Returns:

- list of nearby player entries or the closest player entry

Example usage:

```lua
local player = FWB.Entity.Player.Closest({
    maxDistance = 2.5,
    selfInclude = false
})
```

Notes:

- entries include `id`, `ped`, `coords`, and `distance`

</details>

<details>
<summary><strong>Nearby Peds And Vehicles</strong></summary>

Short description: Find nearby peds or vehicles with optional filtering.

Signature:

```lua
FWB.Entity.Ped.Nearby(extras)
FWB.Entity.Ped.Closest(extras)
FWB.Entity.Vehicle.Nearby(extras)
FWB.Entity.Vehicle.Closest(extras)
```

Returns:

- nearby entry list or one closest entry

Example usage:

```lua
local vehicle = FWB.Entity.Vehicle.Closest({
    maxDistance = 8.0,
    includePlayerVehicle = false
})
```

Notes:

- vehicle entries include `plate`
- ped entries support `aliveOnly` and `includeMissionPeds`

</details>

<details>
<summary><strong>Front Coords</strong></summary>

Short description: Get a point directly in front of a ped or heading.

Signature:

```lua
FWB.Player.GetFrontCoords(extras)
FWB.Entity.GetFrontCoords(extras)
FWB.Entity.FrontCoords(extras)
exports.fs_bridge:GetFrontCoords(extras)
```

Common extras:

| Key | Type | Notes |
|---|---|---|
| `distance` | `number` | Default `1.0` |
| `verticalOffset` | `number` | Default `-0.7` |
| `ped` | `number` | Optional ped |
| `coords` | `vector3` | Optional override coords |
| `heading` | `number` | Optional override heading |

Returns:

- `vector3`

Example usage:

```lua
local frontCoords = FWB.Player.GetFrontCoords({
    distance = 2.0,
    verticalOffset = -0.7
})
```

Notes:

- ideal for placing props, markers, or interaction checks

</details>
