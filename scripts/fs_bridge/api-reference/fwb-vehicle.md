# FWB.Vehicle

`FWB.Vehicle` is the public vehicle runtime for creation, updates, props, plate generation, and owner workflows.

## Public Calls

```lua
FWB.Vehicle.Create(spawnSource, model, options)
FWB.Vehicle.Update(handleOrEntry, updates)
FWB.Vehicle.Remove(handleOrEntry)
FWB.Vehicle.Get(handleOrEntry)
FWB.Vehicle.GetAll()
FWB.Vehicle.Clear(resource)
FWB.Vehicle.GeneratePlate()
FWB.Vehicle.Props.Get(vehicle)
FWB.Vehicle.Props.Set(vehicle, props)
FWB.Vehicle.Owner.Update(oldOwner, newOwner, plate)
FWB.Vehicle.InsertNewOwnedVehicle(options)
FWB.Vehicle.LabelByModel(model)
FWB.Vehicle.LabelByEntity(entity)
FWB.Vehicle.FromPlate(plate)
FWB.Vehicle.Nearby(coords, extras)
FWB.Vehicle.Closest(coords, extras)
```

<details>
<summary><strong>Create A Vehicle</strong></summary>

Short description: Spawn a vehicle and optionally apply props, keys, fuel, lock state, and routing bucket settings.

Signature:

```lua
FWB.Vehicle.Create(spawnSource, model, options)
exports.fs_bridge:CreateVehicle(spawnSource, model, options)
```

Common options:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3` or `vector4` | Spawn point |
| `warp` | `boolean` | Warp player into vehicle |
| `plate` | `string` | Custom plate |
| `fuel` | `number` | Initial fuel |
| `keys` | `boolean` | Give keys |
| `props` | `table` | Vehicle props |
| `extras` | `table` | Extra states |
| `freeze` | `boolean` | Freeze state |
| `lock` | `boolean` | Lock state |
| `rbucket` | `number` | Routing bucket |
| `source` | `number` | Owning player for server-created vehicles |

Returns:

- created entry table

Example usage:

```lua
local created = FWB.Vehicle.Create(source, 'adder', {
    source = source,
    warp = true,
    plate = FWB.Vehicle.GeneratePlate(),
    fuel = 80.0,
    keys = true
})
```

Notes:

- props still use the active framework vehicle property implementation

</details>

<details>
<summary><strong>Update Or Remove A Vehicle</strong></summary>

Short description: Update runtime fields or remove a vehicle from the bridge registry.

Signature:

```lua
FWB.Vehicle.Update(handleOrEntry, updates)
FWB.Vehicle.Remove(handleOrEntry)
```

Returns:

- update success and updated entry
- remove result

Example usage:

```lua
local ok = FWB.Vehicle.Update(created.handle, {
    fuel = 100.0,
    freeze = true
})

FWB.Vehicle.Remove(created.handle)
```

Notes:

- `handleOrEntry` can be a handle string, entry table, entity id, or net id

</details>

<details>
<summary><strong>Read Registry Data</strong></summary>

Short description: Read one vehicle entry, all entries, or clear by resource.

Signature:

```lua
FWB.Vehicle.Get(handleOrEntry)
FWB.Vehicle.GetAll()
FWB.Vehicle.Clear(resource)
```

Returns:

- one entry
- table of all entries
- clear result

Example usage:

```lua
local entry = FWB.Vehicle.Get(created.handle)
local vehicles = FWB.Vehicle.GetAll()
```

Notes:

- client and server both expose active registries

</details>

<details>
<summary><strong>Vehicle Props And Plates</strong></summary>

Short description: Generate a plate or get and set vehicle properties through the active framework.

Signature:

```lua
FWB.Vehicle.GeneratePlate()
FWB.Vehicle.Props.Get(vehicle)
FWB.Vehicle.Props.Set(vehicle, props)
```

Returns:

- string plate
- props table
- props set result

Example usage:

```lua
local plate = FWB.Vehicle.GeneratePlate()
local props = FWB.Vehicle.Props.Get(vehicle)
FWB.Vehicle.Props.Set(vehicle, props)
```

Notes:

- server prop updates are routed back through the owning client when needed

</details>

<details>
<summary><strong>Ownership Helpers</strong></summary>

Short description: Update an existing owned vehicle record or insert a new one.

Signature:

```lua
FWB.Vehicle.Owner.Update(oldOwner, newOwner, plate)
FWB.Vehicle.InsertNewOwnedVehicle(options)
```

Arguments for insert:

| Key | Type | Required |
|---|---|---|
| `owner` | `number` | Yes |
| `plate` | `string` | Yes |
| `model` | `string` or `number` | Yes |
| `props` | `table` | Yes |
| `type` | `string` | No |

Returns:

- success and result

Example usage:

```lua
FWB.Vehicle.Owner.Update(source, 'char1:NEWIDENTIFIER', 'ABC123')

FWB.Vehicle.InsertNewOwnedVehicle({
    owner = source,
    plate = 'ABC123',
    model = 'adder',
    props = {}
})
```

Notes:

- server-side only

</details>
