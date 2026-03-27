# FWB.Vehicle

`FWB.Vehicle` is the public vehicle runtime for creation, updates, props, plate generation, nearby search, closest lookup, plate lookup, and owner workflows.

## Public Calls

```lua
FWB.Vehicle.Create(spawnSource, model, options)
FWB.Vehicle.Update(handleOrEntry, updates)
FWB.Vehicle.Get(handleOrEntry)
FWB.Vehicle.GetAll()
FWB.Vehicle.GeneratePlate()
FWB.Vehicle.GetByPlate(plate)
FWB.Vehicle.Nearby(extras)
FWB.Vehicle.Closest(extras)
FWB.Vehicle.Props.Get(vehicle)
FWB.Vehicle.Props.Set(vehicle, props)
FWB.Vehicle.Owner.Update(oldOwner, newOwner, plate)
FWB.Vehicle.GetOwnedList()
FWB.Vehicle.GetDetailFromPlate(plate)
FWB.Vehicle.InsertNewOwnedVehicle(options)
FWB.Vehicle.LabelByModel(model)
FWB.Vehicle.LabelByEntity(entity)
```

## Common Rules

- `FWB.Vehicle.Nearby` uses one `extras` table only
- `FWB.Vehicle.Closest` uses one `extras` table only
- `extras.includePlayerVehicle` is the supported key
- `FWB.Vehicle.GeneratePlate()` is the public plate generate helper
- `FWB.Vehicle.GetByPlate(plate)` is the public plate lookup helper
- runtime docs focus on create, update, get, and get-all
- `timeout` in runtime create and update defaults to `10000`

<details>
<summary><strong>Nearby Vehicles</strong></summary>

Short description: Get nearby vehicle entries by passing one search options table.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Optional search center |
| `model` | `string|number` | Optional vehicle model name or model hash filter |
| `maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `sortedByDistance` | `boolean` | Sort results from nearest to farthest. Defaults to `true` |
| `includePlayerVehicle` | `boolean` | Set `true` to include the player vehicle in the result. Defaults to `false` |
| `maxCount` | `number` | Optional maximum amount of results to keep |

Returns:

- `table[]`

Example usage:

```lua
local vehicles = FWB.Vehicle.Nearby({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

<details>
<summary><strong>Closest Vehicle</strong></summary>

Short description: Get the closest vehicle entity by passing one search options table.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Optional search center |
| `model` | `string|number` | Optional vehicle model name or model hash filter |
| `maxDistance` | `number` | Maximum search distance. Defaults to `2.0` |
| `sortedByDistance` | `boolean` | Bridge forces this to `true` for closest lookup |
| `includePlayerVehicle` | `boolean` | Set `true` to include the player vehicle in the result. Defaults to `false` |
| `maxCount` | `number` | Optional value accepted, but Bridge internally forces this call to one result |

Returns:

- `number`
- `nil`

Example usage:

```lua
local closestVehicle = FWB.Vehicle.Closest({
    coords = GetEntityCoords(PlayerPedId()),
    maxDistance = 5.0,
    includePlayerVehicle = false
})
```

</details>

<details>
<summary><strong>Generate Plate</strong></summary>

Short description: Generate a new plate through the Bridge runtime callback.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `string`
- `nil`

Example usage:

```lua
local plate = FWB.Vehicle.GeneratePlate()
print(plate)
```

</details>

<details>
<summary><strong>Vehicle By Plate</strong></summary>

Short description: Find a spawned vehicle entity by plate text.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `plate` | `string` | Vehicle plate text |

Returns:

- `number`
- `nil`

Example usage:

```lua
local vehicle = FWB.Vehicle.GetByPlate('ABC123')
```

</details>

<details>
<summary><strong>Owned Vehicle Helpers</strong></summary>

Short description: Read owned vehicle data through the active framework bridge on the server.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `plate` | `string` | Required only for `FWB.Vehicle.GetDetailFromPlate(plate)` |

Returns:

- `FWB.Vehicle.GetOwnedList()` -> owned vehicles table
- `FWB.Vehicle.GetDetailFromPlate(plate)` -> owned vehicle detail or `nil`

Example usage:

```lua
local owned = FWB.Vehicle.GetOwnedList()
print(owned['ABC123'] and owned['ABC123'].owner)

local detail = FWB.Vehicle.GetDetailFromPlate('ABC123')
print(detail and detail.firstname, detail and detail.plate)
```

</details>

<details>
<summary><strong>Create And Update Runtime Vehicles</strong></summary>

Short description: Create and update tracked runtime vehicles with the current public runtime options.

Common runtime options:

| Key | Type | Notes |
|---|---|---|
| `resource` | `string` | Optional resource owner name |
| `source` | `number` | Owner player source for server-side runtime sync |
| `coords` | `vector3|vector4|table` | Spawn or update position |
| `position` | `vector3|vector4|table` | Alias for `coords` |
| `heading` | `number` | Heading value |
| `spawnclear` | `boolean` | Clear nearby vehicles before create or recreate |
| `clearRadius` | `number` | Radius used with `spawnclear` |
| `plate` | `string` | Custom plate text |
| `fuel` | `number` | Fuel level |
| `props` | `table` | Vehicle properties table |
| `extras` | `table` | Vehicle extras map |
| `livery` | `number` | Livery value |
| `putOnGround` | `boolean` | Put vehicle on the ground |
| `freeze` | `boolean` | Freeze state |
| `engineOn` | `boolean` | Engine state |
| `locked` | `boolean|number` | Lock state |
| `dirtLevel` | `number` | Dirt level |
| `bodyHealth` | `number` | Body health |
| `engineHealth` | `number` | Engine health |
| `petrolTankHealth` | `number` | Petrol tank health |
| `timeout` | `number` | Wait timeout. Defaults to `10000` |

Example usage:

```lua
local created = FWB.Vehicle.Create(source, 'adder', {
    source = source,
    rbucket = 1,
    plate = FWB.Vehicle.GeneratePlate(),
    fuel = 80.0,
    props = {}
})

local success, updated = FWB.Vehicle.Update(created.handle, {
    fuel = 90.0,
    freeze = true
})

print(success, updated and updated.netId)
```

</details>
