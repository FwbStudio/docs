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
local ownedVehicles = FWB.GetOwnedVehiclesList()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local ownedVehicles = FWB.GetOwnedVehiclesList()
print(ownedVehicles)
```

Example as export:

- No direct export is provided for this helper.

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
local detail = FWB.GetVehicleDetailFromPlate(plate)
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local detail = FWB.GetVehicleDetailFromPlate('ABC123')
print(detail)
```

Example as export:

- No direct export is provided for this helper.

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
| `options.handle` | `string` | Optional custom runtime handle |
| `options.resource` | `string` | Optional resource owner name. Defaults to the invoking resource |
| `options.source` | `number` | Owner player source used for keys, props sync, and client updates |
| `options.playerSource` | `number` | Alias for `options.source` |
| `options.ownerSource` | `number` | Alias for `options.source` |
| `options.coords` | `vector3|vector4|table` | Spawn position |
| `options.position` | `vector3|vector4|table` | Alias for `options.coords` |
| `options.location` | `vector3|vector4|table` | Alias for `options.coords` |
| `options.heading` | `number` | Spawn heading when your coordinates do not already include `w` |
| `options.giveKeys` | `boolean` | Give keys after spawn |
| `options.give_keys` | `boolean` | Alias for `options.giveKeys` |
| `options.keys` | `boolean` | Alias for `options.giveKeys` |
| `options.warp` | `boolean` | Ask the owner client to warp into the vehicle |
| `options.wrap` | `boolean` | Alias for `options.warp` |
| `options.seat` | `number` | Seat index used when `options.warp = true`. Defaults to `-1` |
| `options.putOnGround` | `boolean` | Ask the owner client to place the vehicle on the ground |
| `options.on_ground` | `boolean` | Alias for `options.putOnGround` |
| `options.spawnclear` | `boolean` | Clear nearby vehicles before spawning |
| `options.clearArea` | `boolean` | Alias for `options.spawnclear` |
| `options.clearRadius` | `number` | Radius used when `options.spawnclear = true`. Defaults to `5.0` |
| `options.spawnClearRadius` | `number` | Alias for `options.clearRadius` |
| `options.timeout` | `number` | Entity/owner wait timeout in milliseconds. Defaults to `10000` |
| `options.rbucket` | `number` | Routing bucket applied to the spawned vehicle |
| `options.vehicleType` | `string` | Optional explicit vehicle type. Leave empty to let Bridge resolve it |
| `options.extras` | `table` | Vehicle extras map copied into `options.props.extras` when needed |
| `options.props` | `table` | Full vehicle properties table |
| `options.livery` | `number` | Livery value copied into `props.modLivery` when needed |
| `options.plate` | `string` | Custom plate text |
| `options.fuel` | `number` | Fuel level sent to the owner client |
| `options.engineOn` | `boolean` | Engine state sent to the owner client |
| `options.engine` | `boolean` | Alias for `options.engineOn` |
| `options.locked` | `boolean|number` | Lock state sent to the owner client |
| `options.lock` | `boolean|number` | Alias for `options.locked` |
| `options.freeze` | `boolean` | Freeze the vehicle position |
| `options.dirtLevel` | `number` | Dirt level value sent to the owner client |
| `options.bodyHealth` | `number` | Body health value sent to the owner client |
| `options.engineHealth` | `number` | Engine health value sent to the owner client |
| `options.petrolTankHealth` | `number` | Petrol tank health value sent to the owner client |
| `options.removeOnDisconnect` | `boolean` | Remove the runtime vehicle automatically when the owner disconnects |
| `options.removeOnLogout` | `boolean` | Remove the runtime vehicle automatically when the owner logs out |

Returns:

- `table` runtime entry with `handle`, `resource`, `model`, `modelName`, `options`, `vehicle`, `netId`, `netid`, `spawnSource`, and `ownerSource`
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
    giveKeys = true,
    warp = true,
    plate = FWB.Vehicle.GeneratePlate(),
    removeOnDisconnect = true
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(source, 'adder', {
    source = source,
    giveKeys = true,
    warp = true,
    plate = exports['fs_bridge']:GenerateVehiclePlate(),
    removeOnDisconnect = true
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
| `updates.source` | `number` | Owner player source used for keys, props sync, and client updates |
| `updates.playerSource` | `number` | Alias for `updates.source` |
| `updates.ownerSource` | `number` | Alias for `updates.source` |
| `updates.coords` | `vector3|vector4|table` | New position |
| `updates.position` | `vector3|vector4|table` | Alias for `updates.coords` |
| `updates.location` | `vector3|vector4|table` | Alias for `updates.coords` |
| `updates.heading` | `number` | New heading |
| `updates.giveKeys` | `boolean` | Give keys after update |
| `updates.give_keys` | `boolean` | Alias for `updates.giveKeys` |
| `updates.keys` | `boolean` | Alias for `updates.giveKeys` |
| `updates.warp` | `boolean` | Ask the owner client to warp into the vehicle |
| `updates.wrap` | `boolean` | Alias for `updates.warp` |
| `updates.seat` | `number` | Seat index used when `updates.warp = true`. Defaults to `-1` |
| `updates.putOnGround` | `boolean` | Ask the owner client to place the vehicle on the ground |
| `updates.on_ground` | `boolean` | Alias for `updates.putOnGround` |
| `updates.spawnclear` | `boolean` | Clear nearby vehicles before a recreate |
| `updates.clearArea` | `boolean` | Alias for `updates.spawnclear` |
| `updates.clearRadius` | `number` | Radius used when `updates.spawnclear = true` |
| `updates.spawnClearRadius` | `number` | Alias for `updates.clearRadius` |
| `updates.timeout` | `number` | Entity/owner wait timeout in milliseconds |
| `updates.rbucket` | `number` | Routing bucket applied to the vehicle |
| `updates.vehicleType` | `string` | Optional explicit vehicle type used during recreate |
| `updates.extras` | `table` | Vehicle extras map copied into `updates.props.extras` when needed |
| `updates.props` | `table` | Full or partial vehicle properties table |
| `updates.livery` | `number` | Livery value copied into `props.modLivery` when needed |
| `updates.plate` | `string` | New plate text |
| `updates.fuel` | `number` | Fuel level sent to the owner client |
| `updates.engineOn` | `boolean` | Engine state sent to the owner client |
| `updates.engine` | `boolean` | Alias for `updates.engineOn` |
| `updates.locked` | `boolean|number` | Lock state sent to the owner client |
| `updates.lock` | `boolean|number` | Alias for `updates.locked` |
| `updates.freeze` | `boolean` | Freeze state |
| `updates.dirtLevel` | `number` | Dirt level value sent to the owner client |
| `updates.bodyHealth` | `number` | Body health value sent to the owner client |
| `updates.engineHealth` | `number` | Engine health value sent to the owner client |
| `updates.petrolTankHealth` | `number` | Petrol tank health value sent to the owner client |
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
