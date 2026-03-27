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

This page documents the public server-side Ped API.

## FWB.Ped

### Ped Runtime

<details>
<summary><strong>Create Ped</strong></summary>

Short description: Create a server-managed ped from one options table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Ped creation table |
| `options.source` | `number` | Optional player source used as spawn source when coords are not provided |
| `options.spawnSource` | `number` | Supported alias for `options.source` |
| `options.coords` | `vector3|vector4|table` | Ped coordinates. Required when no source is supplied |
| `options.model` | `string|number` | Ped model name or hash |
| `options.heading` | `number` | Optional heading |
| `options.handle` | `string` | Optional custom runtime handle |
| `options.pedType` | `number` | Optional ped type. Defaults to `4` |
| `options.freeze` | `boolean` | Freeze the ped after setup |
| `options.invincible` | `boolean` | Make the ped invincible |
| `options.blockEvents` | `boolean` | Block non-temporary events |
| `options.health` | `number` | Optional ped health |
| `options.armour` | `number` | Optional armour |
| `options.weapon` | `string|number|boolean` | Weapon name, weapon hash, or `false` to clear weapons |
| `options.ammo` | `number` | Optional weapon ammo |
| `options.removeOnDisconnect` | `boolean` | Remove the ped when the owning source disconnects |
| `options.blip` | `table|boolean` | Optional synced blip configuration |
| `options.resource` | `string` | Optional resource owner name |

Returns:

- `string, number, number` runtime handle, network id, and ped entity
- `nil, nil, nil` when creation fails

How to write it as function:

```lua
local handle, netId, ped = FWB.Ped.Create(options)
```

How to write it as export:

```lua
local handle, netId, ped = exports['fs_bridge']:CreatePed(options)
```

Example as function:

```lua
local handle, netId, ped = FWB.Ped.Create({
    source = source,
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true,
    invincible = true,
    blockEvents = true,
    weapon = 'WEAPON_PISTOL',
    ammo = 120,
    blip = {
        title = 'Guard',
        id = 1,
        color = 2
    }
})
```

Example as export:

```lua
local handle, netId, ped = exports['fs_bridge']:CreatePed({
    source = source,
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true,
    invincible = true,
    blockEvents = true,
    weapon = 'WEAPON_PISTOL',
    ammo = 120,
    blip = {
        title = 'Guard',
        id = 1,
        color = 2
    }
})
```

</details>

<details>
<summary><strong>Update Ped</strong></summary>

Short description: Update one server-managed ped. If `model` or `pedType` changes, Bridge recreates the ped under the same handle.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Runtime ped handle |
| `updates` | `table` | Partial update table using the same public fields as create |

Returns:

- `boolean, table` success flag and updated entry
- `false, table` when the entry cannot be updated

How to write it as function:

```lua
local success, entry = FWB.Ped.Update(handle, updates)
```

How to write it as export:

```lua
local success, entry = exports['fs_bridge']:UpdatePed(handle, updates)
```

Example as function:

```lua
local success, entry = FWB.Ped.Update(handle, {
    freeze = false,
    coords = vec4(450.0, -980.0, 30.7, 180.0),
    blip = {
        color = 3,
        scale = 0.9
    }
})
```

Example as export:

```lua
local success, entry = exports['fs_bridge']:UpdatePed(handle, {
    freeze = false,
    coords = vec4(450.0, -980.0, 30.7, 180.0),
    blip = {
        color = 3,
        scale = 0.9
    }
})
```

</details>

<details>
<summary><strong>Remove Ped</strong></summary>

Short description: Remove one server-managed ped.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Runtime ped handle |

Returns:

- `boolean`

How to write it as function:

```lua
local success = FWB.Ped.Remove(handle)
```

How to write it as export:

```lua
local success = exports['fs_bridge']:RemovePed(handle)
```

Example as function:

```lua
FWB.Ped.Remove(handle)
```

Example as export:

```lua
exports['fs_bridge']:RemovePed(handle)
```

</details>

<details>
<summary><strong>Get Ped</strong></summary>

Short description: Read one server ped runtime entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Runtime ped handle |

Returns:

- `table` ped entry
- `nil` when not found

How to write it as function:

```lua
local entry = FWB.Ped.Get(handle)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetPed(handle)
```

Example as function:

```lua
local entry = FWB.Ped.Get(handle)
print(entry and entry.netId)
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetPed(handle)
print(entry and entry.netId)
```

</details>

<details>
<summary><strong>Get All Peds</strong></summary>

Short description: Read the full server ped registry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` ped entries keyed by handle

How to write it as function:

```lua
local peds = FWB.Ped.GetAll()
```

How to write it as export:

```lua
local peds = exports['fs_bridge']:GetAllPeds()
```

Example as function:

```lua
local peds = FWB.Ped.GetAll()
print(peds)
```

Example as export:

```lua
local peds = exports['fs_bridge']:GetAllPeds()
print(peds)
```

</details>

<details>
<summary><strong>Clear Peds</strong></summary>

Short description: Remove server peds owned by one resource, or clear all server peds.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Optional resource owner filter |

Returns:

- `number` amount of removed entries

How to write it as function:

```lua
local count = FWB.Ped.Clear(resource)
```

How to write it as export:

```lua
local count = exports['fs_bridge']:ClearPeds(resource)
```

Example as function:

```lua
local count = FWB.Ped.Clear(GetCurrentResourceName())
print(count)
```

Example as export:

```lua
local count = exports['fs_bridge']:ClearPeds(GetCurrentResourceName())
print(count)
```

</details>
