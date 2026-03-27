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

This page documents the public server-side Entity helpers.

## FWB.Entity.Object

### Object Search

<details>
<summary><strong>Nearby Objects</strong></summary>

Short description: Find nearby objects from one extras table on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.source` | `number` | Optional player source used for coords fallback |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.ped` | `number` | Optional ped used for coords fallback |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.maxCount` | `number` | Optional result limit |
| `extras.sortedByDistance` | `boolean` | Sort by distance. Defaults to `true` |
| `extras.model` | `string|number` | Optional single model filter |
| `extras.models` | `table` | Optional allow-list of models |
| `extras.excludeModels` | `table` | Optional block-list of models |

Returns:

- `table[]` entries with `object`, `entity`, `coords`, `distance`, and `model`
- empty table when nothing is found

How to write it as function:

```lua
local objects = FWB.Entity.Object.Nearby(extras)
```

How to write it as export:

```lua
local objects = exports['fs_bridge']:GetNearbyObjects(extras)
```

Example as function:

```lua
local objects = FWB.Entity.Object.Nearby({
    source = source,
    maxDistance = 3.0,
    model = `prop_atm_01`
})
```

Example as export:

```lua
local objects = exports['fs_bridge']:GetNearbyObjects({
    source = source,
    maxDistance = 3.0,
    model = `prop_atm_01`
})
```

</details>

<details>
<summary><strong>Closest Object</strong></summary>

Short description: Get the closest nearby object entry from one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Uses the same public fields as Nearby Objects |

Returns:

- `table` closest entry
- `nil` when nothing is found

How to write it as function:

```lua
local entry = FWB.Entity.Object.Closest(extras)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetClosestObject(extras)
```

Example as function:

```lua
local entry = FWB.Entity.Object.Closest({
    source = source,
    maxDistance = 3.0,
    model = `prop_atm_01`
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetClosestObject({
    source = source,
    maxDistance = 3.0,
    model = `prop_atm_01`
})
```

</details>

## FWB.Entity.Player

### Player Search

<details>
<summary><strong>Nearby Players</strong></summary>

Short description: Find nearby players from one extras table on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.source` | `number` | Optional player source used for coords fallback and self exclusion |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.ped` | `number` | Optional ped used for coords fallback |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.maxCount` | `number` | Optional result limit |
| `extras.sortedByDistance` | `boolean` | Sort by distance. Defaults to `true` |
| `extras.selfInclude` | `boolean` | Include the source player in results |

Returns:

- `table[]` entries with `source`, `id`, `serverId`, `ped`, `entity`, `coords`, and `distance`
- empty table when nothing is found

How to write it as function:

```lua
local players = FWB.Entity.Player.Nearby(extras)
```

How to write it as export:

```lua
local players = exports['fs_bridge']:GetNearbyPlayers(extras)
```

Example as function:

```lua
local players = FWB.Entity.Player.Nearby({
    source = source,
    maxDistance = 5.0,
    selfInclude = false
})
```

Example as export:

```lua
local players = exports['fs_bridge']:GetNearbyPlayers({
    source = source,
    maxDistance = 5.0,
    selfInclude = false
})
```

</details>

<details>
<summary><strong>Closest Player</strong></summary>

Short description: Get the closest nearby player entry from one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Uses the same public fields as Nearby Players |

Returns:

- `table` closest entry
- `nil` when nothing is found

How to write it as function:

```lua
local entry = FWB.Entity.Player.Closest(extras)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetClosestPlayer(extras)
```

Example as function:

```lua
local entry = FWB.Entity.Player.Closest({
    source = source,
    maxDistance = 5.0,
    selfInclude = false
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetClosestPlayer({
    source = source,
    maxDistance = 5.0,
    selfInclude = false
})
```

</details>

## FWB.Entity.Ped

### Ped Search

<details>
<summary><strong>Nearby Peds</strong></summary>

Short description: Find nearby peds from one extras table on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.source` | `number` | Optional player source used for coords fallback |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.ped` | `number` | Optional ped used for coords fallback |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.maxCount` | `number` | Optional result limit |
| `extras.sortedByDistance` | `boolean` | Sort by distance. Defaults to `true` |
| `extras.includePlayerPeds` | `boolean` | Include player peds in results |
| `extras.includeMissionPeds` | `boolean` | Include mission peds. Defaults to `true` |
| `extras.aliveOnly` | `boolean` | Keep only alive peds. Defaults to `true` |
| `extras.model` | `string|number` | Optional single model filter |
| `extras.models` | `table` | Optional allow-list of models |
| `extras.excludeModels` | `table` | Optional block-list of models |

Returns:

- `table[]` entries with `ped`, `entity`, `coords`, `distance`, and `model`
- empty table when nothing is found

How to write it as function:

```lua
local peds = FWB.Entity.Ped.Nearby(extras)
```

How to write it as export:

```lua
local peds = exports['fs_bridge']:GetNearbyPeds(extras)
```

Example as function:

```lua
local peds = FWB.Entity.Ped.Nearby({
    source = source,
    maxDistance = 10.0,
    includePlayerPeds = false,
    aliveOnly = true
})
```

Example as export:

```lua
local peds = exports['fs_bridge']:GetNearbyPeds({
    source = source,
    maxDistance = 10.0,
    includePlayerPeds = false,
    aliveOnly = true
})
```

</details>

<details>
<summary><strong>Closest Ped</strong></summary>

Short description: Get the closest nearby ped entry from one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Uses the same public fields as Nearby Peds |

Returns:

- `table` closest entry
- `nil` when nothing is found

How to write it as function:

```lua
local entry = FWB.Entity.Ped.Closest(extras)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetClosestPed(extras)
```

Example as function:

```lua
local entry = FWB.Entity.Ped.Closest({
    source = source,
    maxDistance = 10.0,
    includePlayerPeds = false,
    aliveOnly = true
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetClosestPed({
    source = source,
    maxDistance = 10.0,
    includePlayerPeds = false,
    aliveOnly = true
})
```

</details>

## FWB.Entity.Vehicle

### Vehicle Search

<details>
<summary><strong>Nearby Vehicles</strong></summary>

Short description: Find nearby vehicles from one extras table on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.source` | `number` | Optional player source used for coords fallback |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.ped` | `number` | Optional ped used for coords fallback |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.maxCount` | `number` | Optional result limit |
| `extras.sortedByDistance` | `boolean` | Sort by distance. Defaults to `true` |
| `extras.includePlayerVehicle` | `boolean` | Include the source player vehicle |
| `extras.model` | `string|number` | Optional single model filter |
| `extras.models` | `table` | Optional allow-list of models |
| `extras.excludeModels` | `table` | Optional block-list of models |

Returns:

- `table[]` entries with `vehicle`, `entity`, `coords`, `distance`, `model`, and `plate`
- empty table when nothing is found

How to write it as function:

```lua
local vehicles = FWB.Entity.Vehicle.Nearby(extras)
```

How to write it as export:

```lua
local vehicles = exports['fs_bridge']:GetNearbyVehicles(extras)
```

Example as function:

```lua
local vehicles = FWB.Entity.Vehicle.Nearby({
    source = source,
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

Example as export:

```lua
local vehicles = exports['fs_bridge']:GetNearbyVehicles({
    source = source,
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

<details>
<summary><strong>Closest Vehicle</strong></summary>

Short description: Get the closest nearby vehicle entry from one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Uses the same public fields as Nearby Vehicles |

Returns:

- `table` closest entry
- `nil` when nothing is found

How to write it as function:

```lua
local entry = FWB.Entity.Vehicle.Closest(extras)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetClosestVehicle(extras)
```

Example as function:

```lua
local entry = FWB.Entity.Vehicle.Closest({
    source = source,
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetClosestVehicle({
    source = source,
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

## FWB.Entity

### Position Helpers

<details>
<summary><strong>Front Coords</strong></summary>

Short description: Get a point in front of a server player or another ped source.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number|table` | Player source, or pass the extras table as the first argument |
| `extras` | `table` | Optional options table |
| `extras.source` | `number` | Optional source when you pass only one table argument |
| `extras.distance` | `number` | Forward distance. Defaults to `1.0` |
| `extras.verticalOffset` | `number` | Vertical offset. Defaults to `-0.7` |
| `extras.ped` | `number` | Optional ped used for coords and heading |
| `extras.coords` | `vector3|vector4|table` | Optional coords override |
| `extras.heading` | `number` | Optional heading override |

Returns:

- `vector3`

How to write it as function:

```lua
local coords = FWB.Entity.FrontCoords(source, extras)
```

How to write it as export:

```lua
local coords = exports['fs_bridge']:GetFrontCoords(source, extras)
```

Example as function:

```lua
local coords = FWB.Entity.FrontCoords(source, {
    distance = 2.0,
    verticalOffset = -0.7
})
```

Example as export:

```lua
local coords = exports['fs_bridge']:GetFrontCoords(source, {
    distance = 2.0,
    verticalOffset = -0.7
})
```

</details>
