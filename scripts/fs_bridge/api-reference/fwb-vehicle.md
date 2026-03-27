# FWB.Vehicle

`FWB.Vehicle` is the public vehicle runtime for creation, updates, props, plate generation, nearby search, closest lookup, plate lookup, and owner workflows.

## Public Calls

```lua
FWB.Vehicle.Create(spawnSource, model, options)
FWB.Vehicle.Update(handleOrEntry, updates)
FWB.Vehicle.Remove(handleOrEntry)
FWB.Vehicle.Get(handleOrEntry)
FWB.Vehicle.GetAll()
FWB.Vehicle.Clear(resource)
FWB.Vehicle.GeneratePlate()
FWB.Vehicle.GetByPlate(plate)
FWB.Vehicle.Nearby(extras)
FWB.Vehicle.Closest(extras)
FWB.Vehicle.Props.Get(vehicle)
FWB.Vehicle.Props.Set(vehicle, props)
FWB.Vehicle.Owner.Update(oldOwner, newOwner, plate)
FWB.Vehicle.InsertNewOwnedVehicle(options)
FWB.Vehicle.LabelByModel(model)
FWB.Vehicle.LabelByEntity(entity)
```

## Common Rules

- `FWB.Vehicle.Nearby` uses one `extras` table only
- `FWB.Vehicle.Closest` uses one `extras` table only
- `extras.includePlayerVehicle` is the supported key
- the old `coordsOrExtras, extras` contract is removed from the new API docs
- `FWB.Vehicle.GeneratePlate()` is the public plate generate helper
- `FWB.Vehicle.GetByPlate(plate)` is the public plate lookup helper
- `FWB.Vehicle.Plate.Generate()` and `FWB.Vehicle.FromPlate(plate)` are not part of the current public API docs

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

Notes:

- nearby entries include `vehicle`, `coords`, `distance`, `model`, and `plate`

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

Notes:

- this returns a vehicle entity handle, not the full nearby entry table

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

Notes:

- use this instead of old plate aliases

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

Notes:

- use this instead of old plate lookup aliases

</details>
