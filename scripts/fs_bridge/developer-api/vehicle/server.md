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

This page documents the public server-side Vehicle API.

It covers target-player vehicle keys, vehicle ownership helpers, and the server runtime `FWB.Vehicle` namespace.

## FWB.Player.Vehicle.Keys

### Vehicle Keys

<details>
<summary><strong>Give Keys</strong></summary>

Short description: Give vehicle keys to a target player through the currently detected vehicle keys integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(source, vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
```

Example as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(source, vehicle)
```

</details>

<details>
<summary><strong>Remove Keys</strong></summary>

Short description: Remove vehicle keys from a target player through the currently detected vehicle keys integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveCarKeyPlayer(source, vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
```

Example as export:

```lua
exports['fs_bridge']:RemoveCarKeyPlayer(source, vehicle)
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

## FWB.Vehicle

### Plate

<details>
<summary><strong>Generate Plate</strong></summary>

Short description: Generate a vehicle plate on the server through the active framework bridge.

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
<summary><strong>Set Vehicle Properties</strong></summary>

Short description: Apply vehicle properties from the server by routing the request through the owner client callback.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Owner player source that has the vehicle client-side |
| `vehicleNetId` | `number` | Vehicle network id |
| `properties` | `table` | Vehicle properties table to apply |

Returns:

- callback result from the owner client
- `false` when the target client callback is unavailable or times out

How to write it as function:

```lua
local ok = FWB.Vehicle.Props.Set(source, vehicleNetId, properties)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:SetVehicleProps(source, vehicleNetId, properties)
```

Example as function:

```lua
local ok = FWB.Vehicle.Props.Set(source, vehicleNetId, {
    plate = 'FS100'
})
```

Example as export:

```lua
local ok = exports['fs_bridge']:SetVehicleProps(source, vehicleNetId, {
    plate = 'FS100'
})
```

</details>

### Vehicle Ownership

<details>
<summary><strong>Update Vehicle Owner</strong></summary>

Short description: Update the owner of an existing owned vehicle record through the active framework bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `oldOwner` | `string|number` | Previous owner identifier or source, depending on your framework flow |
| `newOwner` | `string|number` | New owner identifier or source, depending on your framework flow |
| `plate` | `string` | Vehicle plate text. Bridge trims surrounding spaces before updating |

Returns:

- `boolean, any` framework result on success
- `false, string` error code such as `invalid_plate` or `unsupported_framework`

How to write it as function:

```lua
local ok, result = FWB.Vehicle.Owner.Update(oldOwner, newOwner, plate)
```

How to write it as export:

```lua
local ok, result = exports['fs_bridge']:UpdateVehicleOwner(oldOwner, newOwner, plate)
```

Example as function:

```lua
local ok, result = FWB.Vehicle.Owner.Update('license:old', 'license:new', 'ABC123')
print(ok, result)
```

Example as export:

```lua
local ok, result = exports['fs_bridge']:UpdateVehicleOwner('license:old', 'license:new', 'ABC123')
print(ok, result)
```

</details>

<details>
<summary><strong>Insert New Owned Vehicle</strong></summary>

Short description: Insert a new owned vehicle record through the active framework bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Insert options table |
| `options.owner` | `number` | Online owner source. Bridge resolves and validates this player |
| `options.source` | `number` | Alias for `options.owner` |
| `options.plate` | `string` | Vehicle plate text. Bridge trims surrounding spaces before inserting |
| `options.model` | `string|number` | Vehicle model name or model hash |
| `options.props` | `table` | Vehicle properties table stored with the owned vehicle record |

Returns:

- `boolean, any` framework result on success
- `false, string` error code such as `invalid_arguments`, `invalid_plate`, `invalid_owner`, `owner_not_found`, `invalid_model`, `invalid_props`, or `unsupported_framework`

How to write it as function:

```lua
local ok, result = FWB.Vehicle.InsertNewOwnedVehicle(options)
```

How to write it as export:

```lua
local ok, result = exports['fs_bridge']:InsertNewOwnedVehicle(options)
```

Example as function:

```lua
local ok, result = FWB.Vehicle.InsertNewOwnedVehicle({
    owner = source,
    plate = 'ABC123',
    model = 'adder',
    props = {}
})
print(ok, result)
```

Example as export:

```lua
local ok, result = exports['fs_bridge']:InsertNewOwnedVehicle({
    owner = source,
    plate = 'ABC123',
    model = 'adder',
    props = {}
})
print(ok, result)
```

</details>

<details>
<summary><strong>Get Owned Vehicles List</strong></summary>

Short description: Read the framework owned vehicle list helper exposed by the active framework bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `table` owned vehicles list
- `nil` when the active framework does not provide data

How to write it as function:

```lua
local ownedVehicles = FWB.Vehicle.GetOwnedList()
```

How to write it as export:

```lua
local ownedVehicles = exports['fs_bridge']:GetOwnedVehiclesList()
```

Example as function:

```lua
local ownedVehicles = FWB.Vehicle.GetOwnedList()
print(ownedVehicles)
```

Example as export:

```lua
local ownedVehicles = exports['fs_bridge']:GetOwnedVehiclesList()
print(ownedVehicles)
```

</details>

<details>
<summary><strong>Vehicle Detail By Plate</strong></summary>

Short description: Read one framework owned vehicle record by plate through the active framework bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `plate` | `string` | Vehicle plate text |

Returns:

- `table` owned vehicle detail
- `nil` when the plate cannot be found

How to write it as function:

```lua
local detail = FWB.Vehicle.GetDetailFromPlate(plate)
```

How to write it as export:

```lua
local detail = exports['fs_bridge']:GetVehicleDetailFromPlate(plate)
```

Example as function:

```lua
local detail = FWB.Vehicle.GetDetailFromPlate('ABC123')
print(detail)
```

Example as export:

```lua
local detail = exports['fs_bridge']:GetVehicleDetailFromPlate('ABC123')
print(detail)
```

</details>

### Vehicle Runtime

<details>
<summary><strong>Create Vehicle</strong></summary>

Short description: Create and register a server runtime vehicle entry that Bridge can track and update later.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `spawnSource` | `number|vector3|vector4` | Player source, ped entity, or coordinates. When using coordinates only, you can still set `options.source` |
| `model` | `string|number` | Vehicle model name or model hash |
| `options` | `table` | Vehicle creation options table |
| `options.resource` | `string` | Optional resource owner name. Defaults to the invoking resource |
| `options.source` | `number` | Owner player source used for props sync and client updates |
| `options.playerSource` | `number` | Alias for `options.source` |
| `options.ownerSource` | `number` | Alias for `options.source` |
| `options.coords` | `vector3|vector4|table` | Spawn position |
| `options.position` | `vector3|vector4|table` | Alias for `options.coords` |
| `options.heading` | `number` | Spawn heading when your coordinates do not already include `w` |
| `options.spawnclear` | `boolean` | Clear nearby vehicles before spawning |
| `options.clearRadius` | `number` | Radius used when `options.spawnclear = true`. Defaults to `5.0` |
| `options.plate` | `string` | Custom plate text |
| `options.fuel` | `number` | Fuel level sent to the owner client |
| `options.props` | `table` | Full vehicle properties table |
| `options.extras` | `table` | Vehicle extras map copied into `options.props.extras` when needed |
| `options.livery` | `number` | Livery value copied into `props.modLivery` when needed |
| `options.putOnGround` | `boolean` | Ask the owner client to place the vehicle on the ground |
| `options.freeze` | `boolean` | Freeze the vehicle position |
| `options.engineOn` | `boolean` | Engine state sent to the owner client |
| `options.locked` | `boolean|number` | Lock state sent to the owner client |
| `options.dirtLevel` | `number` | Dirt level value sent to the owner client |
| `options.bodyHealth` | `number` | Body health value sent to the owner client |
| `options.engineHealth` | `number` | Engine health value sent to the owner client |
| `options.petrolTankHealth` | `number` | Petrol tank health value sent to the owner client |
| `options.timeout` | `number` | Entity or owner wait timeout in milliseconds. Defaults to `10000` |
| `options.rbucket` | `number` | Routing bucket applied to the spawned vehicle |
| `options.vehicleType` | `string` | Optional explicit vehicle type. Leave empty to let Bridge resolve it |
| `options.removeOnDisconnect` | `boolean` | Remove the runtime vehicle automatically when the owner disconnects |
| `options.removeOnLogout` | `boolean` | Remove the runtime vehicle automatically when the owner logs out |

Returns:

- `table` runtime entry with `handle`, `resource`, `model`, `modelName`, `options`, `vehicle`, `netId`, `spawnSource`, and `ownerSource`
- throws a Lua error when the model is invalid, the spawn source is invalid, the vehicle type cannot be resolved, or creation times out

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
local entry = FWB.Vehicle.Create(source, 'adder', {
    source = source,
    rbucket = 1,
    plate = FWB.Vehicle.GeneratePlate(),
    fuel = 80.0,
    props = {
        bodyHealth = 1000.0,
        engineHealth = 1000.0
    }
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(source, 'adder', {
    source = source,
    rbucket = 1,
    plate = exports['fs_bridge']:GenerateVehiclePlate(),
    fuel = 80.0,
    props = {
        bodyHealth = 1000.0,
        engineHealth = 1000.0
    }
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
| `updates.source` | `number` | Owner player source used for props sync and client updates |
| `updates.playerSource` | `number` | Alias for `updates.source` |
| `updates.ownerSource` | `number` | Alias for `updates.source` |
| `updates.coords` | `vector3|vector4|table` | New position |
| `updates.position` | `vector3|vector4|table` | Alias for `updates.coords` |
| `updates.heading` | `number` | New heading |
| `updates.spawnclear` | `boolean` | Clear nearby vehicles before a recreate |
| `updates.clearRadius` | `number` | Radius used when `updates.spawnclear = true` |
| `updates.plate` | `string` | New plate text |
| `updates.fuel` | `number` | Fuel level sent to the owner client |
| `updates.props` | `table` | Full or partial vehicle properties table |
| `updates.extras` | `table` | Vehicle extras map copied into `updates.props.extras` when needed |
| `updates.livery` | `number` | Livery value copied into `props.modLivery` when needed |
| `updates.putOnGround` | `boolean` | Ask the owner client to place the vehicle on the ground |
| `updates.freeze` | `boolean` | Freeze state |
| `updates.engineOn` | `boolean` | Engine state sent to the owner client |
| `updates.locked` | `boolean|number` | Lock state sent to the owner client |
| `updates.dirtLevel` | `number` | Dirt level value sent to the owner client |
| `updates.bodyHealth` | `number` | Body health value sent to the owner client |
| `updates.engineHealth` | `number` | Engine health value sent to the owner client |
| `updates.petrolTankHealth` | `number` | Petrol tank health value sent to the owner client |
| `updates.timeout` | `number` | Entity or owner wait timeout in milliseconds. Defaults to `10000` |
| `updates.rbucket` | `number` | Routing bucket applied to the vehicle |
| `updates.vehicleType` | `string` | Optional explicit vehicle type used during recreate |
| `updates.removeOnDisconnect` | `boolean` | Remove the runtime vehicle automatically when the owner disconnects |
| `updates.removeOnLogout` | `boolean` | Remove the runtime vehicle automatically when the owner logs out |

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
    source = source,
    fuel = 90.0,
    freeze = true,
    removeOnLogout = true
})
```

Example as export:

```lua
local success, entry = exports['fs_bridge']:UpdateVehicle(entry.handle, {
    source = source,
    fuel = 90.0,
    freeze = true,
    removeOnLogout = true
})
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

Short description: Get the full server runtime vehicle table that Bridge is currently tracking.

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
