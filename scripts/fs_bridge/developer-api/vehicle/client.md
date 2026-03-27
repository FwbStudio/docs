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

It covers player vehicle helpers, vehicle keys, fuel helpers, and the runtime `FWB.Vehicle` namespace.

## FWB.Player.Vehicle

### Player Vehicle

<details>
<summary><strong>Nearby Vehicles</strong></summary>

Short description: Get nearby vehicle entries around any coordinate set by using one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.model` | `string|number` | Optional vehicle model name or model hash filter |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.sortedByDistance` | `boolean` | Sort results from nearest to farthest. Defaults to `true` |
| `extras.includePlayerVehicle` | `boolean` | Set `true` to include the player vehicle in the result. Defaults to `false` |
| `extras.maxCount` | `number` | Optional maximum amount of results to keep |

Returns:

- `table[]` list of entries with `vehicle`, `coords`, `distance`, `model`, and `plate`
- empty table when nothing is found

How to write it as function:

```lua
local nearbyVehicles = FWB.Vehicle.Nearby(extras)
```

How to write it as export:

```lua
local nearbyVehicles = exports['fs_bridge']:GetNearbyVehicles(extras)
```

Example as function:

```lua
local nearbyVehicles = FWB.Vehicle.Nearby({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

Example as export:

```lua
local nearbyVehicles = exports['fs_bridge']:GetNearbyVehicles({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

<details>
<summary><strong>Closest Vehicle</strong></summary>

Short description: Get the closest vehicle entity around any coordinate set by using one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.model` | `string|number` | Optional vehicle model name or model hash filter |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.sortedByDistance` | `boolean` | Sort results from nearest to farthest. Bridge forces this to `true` here |
| `extras.includePlayerVehicle` | `boolean` | Set `true` to include the player vehicle in the result. Defaults to `false` |
| `extras.maxCount` | `number` | Optional value accepted, but Bridge internally forces this call to one result |

Returns:

- `number` vehicle entity handle
- `nil` when nothing is found

How to write it as function:

```lua
local vehicle = FWB.Vehicle.Closest(extras)
```

How to write it as export:

```lua
local vehicle = exports['fs_bridge']:GetClosestVehicle(extras)
```

Example as function:

```lua
local vehicle = FWB.Vehicle.Closest({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

Example as export:

```lua
local vehicle = exports['fs_bridge']:GetClosestVehicle({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

## FWB.Player.Vehicle.Keys

### Vehicle Keys

<details>
<summary><strong>Give Keys</strong></summary>

Short description: Give vehicle keys to the local player through the currently detected vehicle keys integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
```

Example as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(vehicle)
```

</details>

<details>
<summary><strong>Remove Keys</strong></summary>

Short description: Remove vehicle keys from the local player through the currently detected vehicle keys integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Remove(vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveCarKeyPlayer(vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Remove(vehicle)
```

Example as export:

```lua
exports['fs_bridge']:RemoveCarKeyPlayer(vehicle)
```

</details>

## FWB.Vehicle.Keys

### Vehicle Keys Resource

<details>
<summary><strong>Keys Resource Name</strong></summary>

Short description: Get the detected vehicle keys resource name that Bridge is currently using.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `string` resource name
- `nil` when no compatible keys resource is active

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

### Fuel

<details>
<summary><strong>Set Fuel</strong></summary>

Short description: Set the vehicle fuel level through the currently detected fuel resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |
| `value` | `number` | Fuel level to apply. Defaults to `100.0` when omitted |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Vehicle.Fuel.Set(vehicle, value)
```

How to write it as export:

```lua
exports['fs_bridge']:SetFuel(vehicle, value)
```

Example as function:

```lua
FWB.Vehicle.Fuel.Set(vehicle, 75.0)
```

Example as export:

```lua
exports['fs_bridge']:SetFuel(vehicle, 75.0)
```

</details>

<details>
<summary><strong>Get Fuel</strong></summary>

Short description: Read the current vehicle fuel level through the active fuel integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- `number` fuel value
- `0.0` when the active integration returns nothing

How to write it as function:

```lua
local fuel = FWB.Vehicle.Fuel.Get(vehicle)
```

How to write it as export:

```lua
local fuel = exports['fs_bridge']:GetFuel(vehicle)
```

Example as function:

```lua
print(FWB.Vehicle.Fuel.Get(vehicle))
```

Example as export:

```lua
print(exports['fs_bridge']:GetFuel(vehicle))
```

</details>

<details>
<summary><strong>Fuel Resource Name</strong></summary>

Short description: Get the detected fuel resource name that Bridge is currently using.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `string` resource name
- `nil` when no compatible fuel resource is active

How to write it as function:

```lua
local resourceName = FWB.Vehicle.Fuel.ResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetFuelResourceName()
```

Example as function:

```lua
print(FWB.Vehicle.Fuel.ResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetFuelResourceName())
```

</details>

## FWB.Vehicle

### Plate

<details>
<summary><strong>Generate Plate</strong></summary>

Short description: Generate a vehicle plate through the Bridge runtime callback.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `string` generated plate
- `nil` when generation fails

How to write it as function:

```lua
local plate = FWB.Vehicle.GeneratePlate()
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

### Properties

<details>
<summary><strong>Get Vehicle Properties</strong></summary>

Short description: Read the current framework vehicle properties table for a client vehicle entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- `table` vehicle properties
- empty table when the core property helper is unavailable

How to write it as function:

```lua
local props = FWB.Vehicle.Props.Get(vehicle)
```

How to write it as export:

```lua
local props = exports['fs_bridge']:GetVehicleProperties(vehicle)
```

Example as function:

```lua
local props = FWB.Vehicle.Props.Get(vehicle)
print(props)
```

Example as export:

```lua
local props = exports['fs_bridge']:GetVehicleProperties(vehicle)
print(props)
```

</details>

<details>
<summary><strong>Set Vehicle Properties</strong></summary>

Short description: Apply a framework vehicle properties table to a client vehicle entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |
| `properties` | `table` | Vehicle properties table to apply |

Returns:

- framework-specific result
- `false` when the core property helper is unavailable

How to write it as function:

```lua
local ok = FWB.Vehicle.Props.Set(vehicle, properties)
```

How to write it as export:

```lua
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

### Labels

<details>
<summary><strong>Vehicle Label By Model</strong></summary>

Short description: Get the display label for a vehicle model name or model hash.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `model` | `string|number` | Vehicle model name or model hash |

Returns:

- `string` label text
- `nil` when Bridge cannot resolve the model label

How to write it as function:

```lua
local label = FWB.Vehicle.LabelByModel(model)
```

How to write it as export:

```lua
local label = exports['fs_bridge']:GetVehicleLabelByModel(model)
```

Example as function:

```lua
print(FWB.Vehicle.LabelByModel('adder'))
```

Example as export:

```lua
print(exports['fs_bridge']:GetVehicleLabelByModel('adder'))
```

</details>

<details>
<summary><strong>Vehicle Label By Entity</strong></summary>

Short description: Get the display label for an existing vehicle entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `entity` | `number` | Vehicle entity handle |

Returns:

- `string` label text
- `nil` when the entity is invalid or Bridge cannot resolve the model label

How to write it as function:

```lua
local label = FWB.Vehicle.LabelByEntity(entity)
```

How to write it as export:

```lua
local label = exports['fs_bridge']:GetVehicleLabelByEntity(entity)
```

Example as function:

```lua
print(FWB.Vehicle.LabelByEntity(vehicle))
```

Example as export:

```lua
print(exports['fs_bridge']:GetVehicleLabelByEntity(vehicle))
```

</details>

### Vehicle Lookup

<details>
<summary><strong>Vehicle By Plate</strong></summary>

Short description: Find a spawned client vehicle entity by plate text.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `plate` | `string` | Vehicle plate text. Bridge trims surrounding spaces before matching |

Returns:

- `number` vehicle entity handle
- `nil` when no spawned vehicle matches the plate

How to write it as function:

```lua
local vehicle = FWB.Vehicle.GetByPlate(plate)
```

How to write it as export:

```lua
local vehicle = exports['fs_bridge']:GetVehicleByPlate(plate)
```

Example as function:

```lua
local vehicle = FWB.Vehicle.GetByPlate('ABC123')
```

Example as export:

```lua
local vehicle = exports['fs_bridge']:GetVehicleByPlate('ABC123')
```

</details>

<details>
<summary><strong>Nearby Vehicles</strong></summary>

Short description: Get nearby vehicle entries around any coordinate set by using one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.model` | `string|number` | Optional vehicle model name or model hash filter |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.sortedByDistance` | `boolean` | Sort results from nearest to farthest. Defaults to `true` |
| `extras.includePlayerVehicle` | `boolean` | Set `true` to include the player vehicle in the result. Defaults to `false` |
| `extras.maxCount` | `number` | Optional maximum amount of results to keep |

Returns:

- `table[]` list of entries with `vehicle`, `coords`, `distance`, `model`, and `plate`
- empty table when nothing is found

How to write it as function:

```lua
local nearbyVehicles = FWB.Vehicle.Nearby(extras)
```

How to write it as export:

```lua
local nearbyVehicles = exports['fs_bridge']:GetNearbyVehicles(extras)
```

Example as function:

```lua
local nearbyVehicles = FWB.Vehicle.Nearby({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

Example as export:

```lua
local nearbyVehicles = exports['fs_bridge']:GetNearbyVehicles({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

<details>
<summary><strong>Closest Vehicle</strong></summary>

Short description: Get the closest vehicle entity around any coordinate set by using one extras table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Search options table |
| `extras.coords` | `vector3|vector4|table` | Optional search center |
| `extras.model` | `string|number` | Optional vehicle model name or model hash filter |
| `extras.maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `extras.sortedByDistance` | `boolean` | Sort results from nearest to farthest. Bridge forces this to `true` here |
| `extras.includePlayerVehicle` | `boolean` | Set `true` to include the player vehicle in the result. Defaults to `false` |
| `extras.maxCount` | `number` | Optional value accepted, but Bridge internally forces this call to one result |

Returns:

- `number` vehicle entity handle
- `nil` when nothing is found

How to write it as function:

```lua
local vehicle = FWB.Vehicle.Closest(extras)
```

How to write it as export:

```lua
local vehicle = exports['fs_bridge']:GetClosestVehicle(extras)
```

Example as function:

```lua
local vehicle = FWB.Vehicle.Closest({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

Example as export:

```lua
local vehicle = exports['fs_bridge']:GetClosestVehicle({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

### Vehicle Runtime

<details>
<summary><strong>Create Vehicle</strong></summary>

Short description: Create and register a client runtime vehicle entry that Bridge can track and update later.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `spawnSource` | `number|vector3|vector4|nil` | Player ped entity, coordinates, or leave empty to use the local player ped |
| `model` | `string|number` | Vehicle model name or model hash |
| `options` | `table` | Vehicle creation options table |
| `options.handle` | `string` | Optional custom runtime handle |
| `options.resource` | `string` | Optional resource owner name. Defaults to the invoking resource |
| `options.coords` | `vector3|vector4|table` | Spawn position |
| `options.position` | `vector3|vector4|table` | Alias for `options.coords` |
| `options.location` | `vector3|vector4|table` | Alias for `options.coords` |
| `options.heading` | `number` | Spawn heading when your coordinates do not already include `w` |
| `options.giveKeys` | `boolean` | Give keys after spawn |
| `options.give_keys` | `boolean` | Alias for `options.giveKeys` |
| `options.keys` | `boolean` | Alias for `options.giveKeys` |
| `options.warp` | `boolean` | Warp the local player into the vehicle |
| `options.wrap` | `boolean` | Alias for `options.warp` |
| `options.seat` | `number` | Seat index used when `options.warp = true`. Defaults to `-1` |
| `options.putOnGround` | `boolean` | Put the vehicle on the ground after spawn |
| `options.on_ground` | `boolean` | Alias for `options.putOnGround` |
| `options.spawnclear` | `boolean` | Clear nearby vehicles before spawning |
| `options.clearArea` | `boolean` | Alias for `options.spawnclear` |
| `options.clearRadius` | `number` | Radius used when `options.spawnclear = true`. Defaults to `5.0` |
| `options.spawnClearRadius` | `number` | Alias for `options.clearRadius` |
| `options.timeout` | `number` | Model/entity wait timeout in milliseconds. Defaults to `10000` |
| `options.silent` | `boolean` | Set `true` to suppress Bridge request-model failure prints |
| `options.extras` | `table` | Vehicle extras map copied into `options.props.extras` when needed |
| `options.props` | `table` | Full vehicle properties table |
| `options.livery` | `number` | Livery value copied into `props.modLivery` when needed |
| `options.plate` | `string` | Custom plate text |
| `options.fuel` | `number` | Fuel level to apply after spawn |
| `options.engineOn` | `boolean` | Engine state after spawn |
| `options.engine` | `boolean` | Alias for `options.engineOn` |
| `options.locked` | `boolean|number` | Lock state after spawn |
| `options.lock` | `boolean|number` | Alias for `options.locked` |
| `options.freeze` | `boolean` | Freeze the vehicle position after spawn |
| `options.dirtLevel` | `number` | Dirt level value |
| `options.bodyHealth` | `number` | Body health value |
| `options.engineHealth` | `number` | Engine health value |
| `options.petrolTankHealth` | `number` | Petrol tank health value |

Returns:

- `table` runtime entry with `handle`, `resource`, `model`, `modelName`, `options`, `vehicle`, `netId`, `netid`, and `spawnSource`
- throws a Lua error when the model is invalid, the spawn source is invalid, or creation times out

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
    giveKeys = true,
    plate = FWB.Vehicle.GeneratePlate(),
    fuel = 80.0,
    engineOn = true
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(nil, 'adder', {
    warp = true,
    giveKeys = true,
    plate = exports['fs_bridge']:GenerateVehiclePlate(),
    fuel = 80.0,
    engineOn = true
})
```

</details>

<details>
<summary><strong>Update Vehicle</strong></summary>

Short description: Update one tracked runtime vehicle entry. If you change the model, Bridge recreates the vehicle and keeps the same runtime handle.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrEntry` | `string|number|table` | Runtime handle, runtime entry table, vehicle entity handle, or vehicle network id |
| `updates` | `table` | Partial update table |
| `updates.model` | `string|number` | New vehicle model. Changing this recreates the vehicle |
| `updates.resource` | `string` | Optional new resource owner name |
| `updates.coords` | `vector3|vector4|table` | New position |
| `updates.position` | `vector3|vector4|table` | Alias for `updates.coords` |
| `updates.location` | `vector3|vector4|table` | Alias for `updates.coords` |
| `updates.heading` | `number` | New heading |
| `updates.giveKeys` | `boolean` | Give keys after update |
| `updates.give_keys` | `boolean` | Alias for `updates.giveKeys` |
| `updates.keys` | `boolean` | Alias for `updates.giveKeys` |
| `updates.warp` | `boolean` | Warp the local player into the vehicle |
| `updates.wrap` | `boolean` | Alias for `updates.warp` |
| `updates.seat` | `number` | Seat index used when `updates.warp = true`. Defaults to `-1` |
| `updates.putOnGround` | `boolean` | Put the vehicle on the ground |
| `updates.on_ground` | `boolean` | Alias for `updates.putOnGround` |
| `updates.spawnclear` | `boolean` | Clear nearby vehicles before a recreate |
| `updates.clearArea` | `boolean` | Alias for `updates.spawnclear` |
| `updates.clearRadius` | `number` | Radius used when `updates.spawnclear = true` |
| `updates.spawnClearRadius` | `number` | Alias for `updates.clearRadius` |
| `updates.timeout` | `number` | Model/entity wait timeout in milliseconds |
| `updates.silent` | `boolean` | Set `true` to suppress Bridge request-model failure prints during recreate |
| `updates.extras` | `table` | Vehicle extras map copied into `updates.props.extras` when needed |
| `updates.props` | `table` | Full or partial vehicle properties table |
| `updates.livery` | `number` | Livery value copied into `props.modLivery` when needed |
| `updates.plate` | `string` | New plate text |
| `updates.fuel` | `number` | Fuel level to apply |
| `updates.engineOn` | `boolean` | Engine state |
| `updates.engine` | `boolean` | Alias for `updates.engineOn` |
| `updates.locked` | `boolean|number` | Lock state |
| `updates.lock` | `boolean|number` | Alias for `updates.locked` |
| `updates.freeze` | `boolean` | Freeze state |
| `updates.dirtLevel` | `number` | Dirt level value |
| `updates.bodyHealth` | `number` | Body health value |
| `updates.engineHealth` | `number` | Engine health value |
| `updates.petrolTankHealth` | `number` | Petrol tank health value |

Returns:

- `boolean, table` success flag and updated runtime entry
- `false, nil` when the runtime entry cannot be resolved

How to write it as function:

```lua
local success, entry = FWB.Vehicle.Update(handleOrEntry, updates)
```

How to write it as export:

```lua
local success, entry = exports['fs_bridge']:UpdateVehicle(handleOrEntry, updates)
```

Example as function:

```lua
local success, entry = FWB.Vehicle.Update(entry.handle, {
    fuel = 100.0,
    freeze = true,
    plate = 'FS100'
})
```

Example as export:

```lua
local success, entry = exports['fs_bridge']:UpdateVehicle(entry.handle, {
    fuel = 100.0,
    freeze = true,
    plate = 'FS100'
})
```

</details>

<details>
<summary><strong>Remove Vehicle</strong></summary>

Short description: Remove one tracked runtime vehicle entry and delete its spawned entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrEntry` | `string|number|table` | Runtime handle, runtime entry table, vehicle entity handle, or vehicle network id |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Vehicle.Remove(handleOrEntry)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RemoveVehicle(handleOrEntry)
```

Example as function:

```lua
local ok = FWB.Vehicle.Remove(entry.handle)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:RemoveVehicle(entry.handle)
print(ok)
```

</details>

<details>
<summary><strong>Get Vehicle</strong></summary>

Short description: Get one tracked runtime vehicle entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrEntry` | `string|number|table` | Runtime handle, runtime entry table, vehicle entity handle, or vehicle network id |

Returns:

- `table` runtime entry
- `nil` when the runtime entry cannot be resolved

How to write it as function:

```lua
local entry = FWB.Vehicle.Get(handleOrEntry)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetVehicle(handleOrEntry)
```

Example as function:

```lua
local entry = FWB.Vehicle.Get(entry.handle)
print(entry)
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetVehicle(entry.handle)
print(entry)
```

</details>

<details>
<summary><strong>Get All Vehicles</strong></summary>

Short description: Get the full client runtime vehicle table that Bridge is currently tracking.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `table` runtime entries keyed by handle

How to write it as function:

```lua
local vehicles = FWB.Vehicle.GetAll()
```

How to write it as export:

```lua
local vehicles = exports['fs_bridge']:GetAllVehicles()
```

Example as function:

```lua
local vehicles = FWB.Vehicle.GetAll()
print(vehicles)
```

Example as export:

```lua
local vehicles = exports['fs_bridge']:GetAllVehicles()
print(vehicles)
```

</details>

<details>
<summary><strong>Clear Vehicles</strong></summary>

Short description: Remove tracked runtime vehicle entries for one resource, or clear every tracked runtime vehicle when no resource is passed.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Optional resource owner name. Leave empty to clear every tracked runtime vehicle |

Returns:

- `number` amount of cleared runtime entries

How to write it as function:

```lua
local cleared = FWB.Vehicle.Clear(resource)
```

How to write it as export:

```lua
local cleared = exports['fs_bridge']:ClearVehicles(resource)
```

Example as function:

```lua
local cleared = FWB.Vehicle.Clear(GetCurrentResourceName())
print(cleared)
```

Example as export:

```lua
local cleared = exports['fs_bridge']:ClearVehicles(GetCurrentResourceName())
print(cleared)
```

</details>
