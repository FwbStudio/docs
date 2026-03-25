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

This page documents the public client-side Vehicle API.

It includes player-scoped vehicle lookups, key helpers, fuel helpers, and the full runtime `FWB.Vehicle` namespace.
## FWB.Player.Vehicle
<details>
<summary><strong>Vehicle.NearBy(extras) / Vehicle.Closest(extras)</strong></summary>

Short description: Search nearby vehicles around the local player through the player-scoped vehicle helpers.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `maxDistance`, `maxCount`, or `includePlayerVehicle` |

Returns:

- nearby vehicle entries or one closest vehicle entry

How to write it as function:

```lua
local vehicles = FWB.Player.Vehicle.NearBy(extras)
local vehicle = FWB.Player.Vehicle.Closest(extras)
```

How to write it as export:

```lua
local vehicles = exports['fs_bridge']:GetPlayerNearbyVehicles(extras)
local vehicle = exports['fs_bridge']:GetPlayerClosestVehicle(extras)
```

Example as function:

```lua
local vehicles = FWB.Player.Vehicle.NearBy({ maxDistance = 12.0 })
local vehicle = FWB.Player.Vehicle.Closest({ maxDistance = 8.0 })
```

Example as export:

```lua
local vehicles = exports['fs_bridge']:GetPlayerNearbyVehicles({ maxDistance = 12.0 })
local vehicle = exports['fs_bridge']:GetPlayerClosestVehicle({ maxDistance = 8.0 })
```

</details>

## FWB.Player.Vehicle.Keys

<details>
<summary><strong>Give(vehicle) / Remove(vehicle)</strong></summary>

Short description: Give or remove vehicle keys for the local player through the active key system resolver.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- resource-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)
```

Example as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(vehicle)
```

</details>

## FWB.Vehicle.Keys

<details>
<summary><strong>ResourceName()</strong></summary>

Short description: Get the detected vehicle keys resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` resource name
- `nil` when nothing is active

How to write it as function:

```lua
local resourceName = FWB.Vehicle.Keys.ResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetVehicleKeysResourceName()
```

Example as function:

```lua
print(FWB.Vehicle.Keys.ResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetVehicleKeysResourceName())
```

</details>


## FWB.Vehicle.Fuel

<details>
<summary><strong>Set(vehicle, value) / Get(vehicle) / ResourceName()</strong></summary>

Short description: Set fuel, read fuel, or read the detected fuel resource name through Bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |
| `value` | `number` | Fuel value, defaults to `100.0` when omitted |

Returns:

- resource-specific result for `Set`
- `number` fuel value for `Get`
- `string` resource name for `ResourceName()`

How to write it as function:

```lua
FWB.Vehicle.Fuel.Set(vehicle, value)
local fuel = FWB.Vehicle.Fuel.Get(vehicle)
local resourceName = FWB.Vehicle.Fuel.ResourceName()
```

How to write it as export:

```lua
exports['fs_bridge']:SetFuel(vehicle, value)
local fuel = exports['fs_bridge']:GetFuel(vehicle)
local resourceName = exports['fs_bridge']:GetFuelResourceName()
```

Example as function:

```lua
FWB.Vehicle.Fuel.Set(vehicle, 75.0)
print(FWB.Vehicle.Fuel.Get(vehicle))
```

Example as export:

```lua
exports['fs_bridge']:SetFuel(vehicle, 75.0)
print(exports['fs_bridge']:GetFuel(vehicle))
```

</details>


## FWB.Vehicle

<details>
<summary><strong>GeneratePlate() / Plate.Generate()</strong></summary>

Short description: Generate a vehicle plate through the Bridge runtime callback.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` generated plate
- `nil` when generation fails

How to write it as function:

```lua
local plate = FWB.Vehicle.GeneratePlate()
local plate2 = FWB.Vehicle.Plate.Generate()
```

How to write it as export:

```lua
local plate = exports['fs_bridge']:GenerateVehiclePlate()
```

Example as function:

```lua
local plate = FWB.Vehicle.GeneratePlate()
print(plate)
```

Example as export:

```lua
local plate = exports['fs_bridge']:GenerateVehiclePlate()
print(plate)
```

</details>

<details>
<summary><strong>Props.Get(vehicle) / Props.Set(vehicle, properties)</strong></summary>

Short description: Read or apply vehicle properties through the active framework core implementation.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |
| `properties` | `table` | Vehicle properties table for `Props.Set` |

Returns:

- props table for `Props.Get`
- boolean or framework-specific result for `Props.Set`

How to write it as function:

```lua
local props = FWB.Vehicle.Props.Get(vehicle)
local ok = FWB.Vehicle.Props.Set(vehicle, properties)
```

How to write it as export:

```lua
local props = exports['fs_bridge']:GetVehicleProperties(vehicle)
local ok = exports['fs_bridge']:SetVehicleProperties(vehicle, properties)
```

Example as function:

```lua
local props = FWB.Vehicle.Props.Get(vehicle)
props.modEngine = 2
FWB.Vehicle.Props.Set(vehicle, props)
```

Example as export:

```lua
local props = exports['fs_bridge']:GetVehicleProperties(vehicle)
props.modEngine = 2
exports['fs_bridge']:SetVehicleProperties(vehicle, props)
```

</details>

<details>
<summary><strong>LabelByModel(model) / LabelByEntity(entity)</strong></summary>

Short description: Read a vehicle display label from a model or a spawned entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `model` | `string|number` | Vehicle model name or hash |
| `entity` | `number` | Vehicle entity handle |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local label = FWB.Vehicle.LabelByModel(model)
local label2 = FWB.Vehicle.LabelByEntity(entity)
```

How to write it as export:

```lua
local label = exports['fs_bridge']:GetVehicleLabelByModel(model)
local label2 = exports['fs_bridge']:GetVehicleLabelByEntity(entity)
```

Example as function:

```lua
print(FWB.Vehicle.LabelByModel('adder'))
print(FWB.Vehicle.LabelByEntity(vehicle))
```

Example as export:

```lua
print(exports['fs_bridge']:GetVehicleLabelByModel('adder'))
print(exports['fs_bridge']:GetVehicleLabelByEntity(vehicle))
```

</details>

<details>
<summary><strong>GetByPlate(plate) / FromPlate(plate)</strong></summary>

Short description: Find a spawned client vehicle by plate.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `plate` | `string` | Vehicle plate text |

Returns:

- vehicle entity handle
- `nil` when not found

How to write it as function:

```lua
local vehicle = FWB.Vehicle.GetByPlate(plate)
local vehicle2 = FWB.Vehicle.FromPlate(plate)
```

How to write it as export:

```lua
local vehicle = exports['fs_bridge']:GetVehicleByPlate(plate)
local vehicle2 = exports['fs_bridge']:GetVehicleFromPlate(plate)
```

Example as function:

```lua
local vehicle = FWB.Vehicle.FromPlate('ABC123')
```

Example as export:

```lua
local vehicle = exports['fs_bridge']:GetVehicleFromPlate('ABC123')
```

</details>

<details>
<summary><strong>Nearby(coords, extras) / Closest(coords, extras)</strong></summary>

Short description: Find nearby vehicles around coordinates or return the closest match.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Optional search coordinates |
| `extras` | `table` | Optional filters like `maxDistance`, `model`, `includePlayerVehicle`, and `maxCount` |

Returns:

- nearby vehicle entry table list for `Nearby`
- closest vehicle entity handle for `Closest`

How to write it as function:

```lua
local vehicles = FWB.Vehicle.Nearby(coords, extras)
local vehicle = FWB.Vehicle.Closest(coords, extras)
```

How to write it as export:

```lua
local vehicles = exports['fs_bridge']:GetNearbyVehicles(coords, extras)
local vehicle = exports['fs_bridge']:GetClosestVehicle(coords, extras)
```

Example as function:

```lua
local vehicles = FWB.Vehicle.Nearby(GetEntityCoords(PlayerPedId()), { maxDistance = 10.0 })
local vehicle = FWB.Vehicle.Closest(GetEntityCoords(PlayerPedId()), { maxDistance = 8.0 })
```

Example as export:

```lua
local vehicles = exports['fs_bridge']:GetNearbyVehicles(GetEntityCoords(PlayerPedId()), { maxDistance = 10.0 })
local vehicle = exports['fs_bridge']:GetClosestVehicle(GetEntityCoords(PlayerPedId()), { maxDistance = 8.0 })
```

</details>

<details>
<summary><strong>Create(spawnSource, model, options)</strong></summary>

Short description: Spawn and register a client-managed vehicle entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `spawnSource` | `number|vector3|vector4|nil` | Player ped, coordinates, or omit to use the local player |
| `model` | `string|number` | Vehicle model |
| `options` | `table` | Vehicle creation options table |

Returns:

- entry table

How to write it as function:

```lua
local entry = FWB.Vehicle.Create(spawnSource, model, options)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(spawnSource, model, options)
```

Example as function:

```lua
local entry = FWB.Vehicle.Create(nil, 'adder', {
    warp = true,
    plate = FWB.Vehicle.GeneratePlate(),
    fuel = 80.0,
    keys = true
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(nil, 'adder', {
    warp = true,
    plate = exports['fs_bridge']:GenerateVehiclePlate(),
    fuel = 80.0,
    keys = true
})
```

</details>

<details>
<summary><strong>Update(handleOrEntry, updates) / Remove(handleOrEntry)</strong></summary>

Short description: Update a client-managed vehicle entry or remove it from the Bridge runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrEntry` | `string|number|table` | Bridge handle, entity, net id, or entry table |
| `updates` | `table` | Partial updates table for `Update` |

Returns:

- success and updated entry for `Update`
- boolean for `Remove`

How to write it as function:

```lua
local success, entry = FWB.Vehicle.Update(handleOrEntry, updates)
local ok = FWB.Vehicle.Remove(handleOrEntry)
```

How to write it as export:

```lua
local success, entry = exports['fs_bridge']:UpdateVehicle(handleOrEntry, updates)
local ok = exports['fs_bridge']:RemoveVehicle(handleOrEntry)
```

Example as function:

```lua
FWB.Vehicle.Update(entry.handle, {
    fuel = 100.0,
    freeze = true
})
FWB.Vehicle.Remove(entry.handle)
```

Example as export:

```lua
exports['fs_bridge']:UpdateVehicle(entry.handle, {
    fuel = 100.0,
    freeze = true
})
exports['fs_bridge']:RemoveVehicle(entry.handle)
```

</details>

<details>
<summary><strong>Get(handleOrEntry) / GetAll() / Clear(resource)</strong></summary>

Short description: Read one vehicle entry, read all entries, or clear entries for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrEntry` | `string|number|table` | Bridge handle, entity, net id, or entry table |
| `resource` | `string` | Optional resource name when clearing |

Returns:

- one entry for `Get(handleOrEntry)`
- all entries for `GetAll()`
- cleared count for `Clear(resource)`

How to write it as function:

```lua
local entry = FWB.Vehicle.Get(handleOrEntry)
local allVehicles = FWB.Vehicle.GetAll()
local cleared = FWB.Vehicle.Clear(resource)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetVehicle(handleOrEntry)
local allVehicles = exports['fs_bridge']:GetAllVehicles()
local cleared = exports['fs_bridge']:ClearVehicles(resource)
```

Example as function:

```lua
local entry = FWB.Vehicle.Get(entry.handle)
local allVehicles = FWB.Vehicle.GetAll()
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetVehicle(entry.handle)
local allVehicles = exports['fs_bridge']:GetAllVehicles()
```

</details>
