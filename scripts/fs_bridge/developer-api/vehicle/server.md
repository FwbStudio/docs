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

It includes target-player key helpers, server runtime vehicle helpers, and the owned vehicle lookup helpers that Bridge exposes publicly.
## FWB.Player.Vehicle.Keys

<details>
<summary><strong>Give(source, vehicle) / Remove(source, vehicle)</strong></summary>

Short description: Give or remove vehicle keys for a target player through the active key system resolver.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- resource-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(source, vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(source, vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
```

Example as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(source, vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(source, vehicle)
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
- `nil` when unavailable

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

<details>
<summary><strong>GeneratePlate() / Plate.Generate()</strong></summary>

Short description: Generate a vehicle plate through the server Bridge runtime.

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
<summary><strong>Props.Set(source, vehicleNetId, properties)</strong></summary>

Short description: Apply vehicle properties from the server by routing the update through the owning client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Owning player source |
| `vehicleNetId` | `number` | Vehicle network id |
| `properties` | `table` | Vehicle properties table |

Returns:

- `boolean` or callback result

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
FWB.Vehicle.Props.Set(source, vehicleNetId, {
    plate = 'ABC123'
})
```

Example as export:

```lua
exports['fs_bridge']:SetVehicleProps(source, vehicleNetId, {
    plate = 'ABC123'
})
```

</details>

<details>
<summary><strong>Owner.Update(oldOwner, newOwner, plate) / InsertNewOwnedVehicle(options)</strong></summary>

Short description: Update an existing owned vehicle record or insert a new owned vehicle entry in the framework database.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `oldOwner` | `string|number` | Previous owner identifier or source |
| `newOwner` | `string|number` | New owner identifier or source |
| `plate` | `string` | Vehicle plate |
| `options` | `table` | Insert table with `owner/source`, `plate`, `model`, and `props` |

Returns:

- success and framework result or error text

How to write it as function:

```lua
local ok, result = FWB.Vehicle.Owner.Update(oldOwner, newOwner, plate)
local ok2, result2 = FWB.Vehicle.InsertNewOwnedVehicle(options)
```

How to write it as export:

```lua
local ok, result = exports['fs_bridge']:UpdateVehicleOwner(oldOwner, newOwner, plate)
local ok2, result2 = exports['fs_bridge']:InsertNewOwnedVehicle(options)
```

Example as function:

```lua
FWB.Vehicle.InsertNewOwnedVehicle({
    owner = source,
    plate = 'ABC123',
    model = 'adder',
    props = {}
})
```

Example as export:

```lua
exports['fs_bridge']:InsertNewOwnedVehicle({
    owner = source,
    plate = 'ABC123',
    model = 'adder',
    props = {}
})
```

</details>

<details>
<summary><strong>Create(spawnSource, model, options) / Update(handleOrEntry, updates) / Remove(handleOrEntry)</strong></summary>

Short description: Create, update, or remove server-managed vehicle entries.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `spawnSource` | `number|vector3|vector4|nil` | Player source, ped handle, coordinates, or omit when `options.coords` is provided |
| `model` | `string|number` | Vehicle model |
| `options` | `table` | Vehicle creation options table |
| `handleOrEntry` | `string|number|table` | Bridge handle, entity, net id, or entry table |
| `updates` | `table` | Partial updates table for `Update` |

Common option keys:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Spawn location |
| `heading` | `number` | Spawn heading |
| `source` | `number` | Owner source |
| `plate` | `string` | Custom plate |
| `fuel` | `number` | Initial fuel |
| `keys` | `boolean` | Give keys |
| `props` | `table` | Vehicle props |
| `rbucket` | `number` | Routing bucket |
| `freeze` | `boolean` | Freeze state |
| `warp` | `boolean` | Warp owner into vehicle |
| `spawnclear` | `boolean` | Clear nearby vehicles before spawning |
| `removeOnDisconnect` | `boolean` | Auto-remove if owner disconnects |
| `removeOnLogout` | `boolean` | Auto-remove if owner logs out |

Returns:

- entry table for `Create`
- success and updated entry for `Update`
- boolean for `Remove`

How to write it as function:

```lua
local entry = FWB.Vehicle.Create(spawnSource, model, options)
local success, updated = FWB.Vehicle.Update(handleOrEntry, updates)
local ok = FWB.Vehicle.Remove(handleOrEntry)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(spawnSource, model, options)
local success, updated = exports['fs_bridge']:UpdateVehicle(handleOrEntry, updates)
local ok = exports['fs_bridge']:RemoveVehicle(handleOrEntry)
```

Example as function:

```lua
local entry = FWB.Vehicle.Create(source, 'adder', {
    source = source,
    plate = FWB.Vehicle.GeneratePlate(),
    keys = true,
    warp = true
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(source, 'adder', {
    source = source,
    plate = exports['fs_bridge']:GenerateVehiclePlate(),
    keys = true,
    warp = true
})
```

</details>

<details>
<summary><strong>Get(handleOrEntry) / GetAll() / Clear(resource)</strong></summary>

Short description: Read one server vehicle entry, read all entries, or clear entries for a resource.

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

## Vehicle Ownership Helpers

<details>
<summary><strong>GetOwnedVehiclesList() / GetVehicleDetailFromPlate(plate)</strong></summary>

Short description: Read the framework-backed owned vehicle index or fetch one owned vehicle record by plate.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `plate` | `string` | Vehicle plate text for `GetVehicleDetailFromPlate(plate)` |

Returns:

- owned vehicle table for `GetOwnedVehiclesList()`
- vehicle detail table for `GetVehicleDetailFromPlate(plate)`
- `nil` when not found

How to write it as function:

```lua
local ownedVehicles = FWB.GetOwnedVehiclesList()
local detail = FWB.GetVehicleDetailFromPlate(plate)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local ownedVehicles = FWB.GetOwnedVehiclesList()
local detail = FWB.GetVehicleDetailFromPlate('ABC123')
```

Notes:

- These helpers read framework ownership data, not only the runtime vehicle list managed by `FWB.Vehicle`.

</details>
