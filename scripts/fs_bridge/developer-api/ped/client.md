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

This page documents the public client-side Ped API.

## FWB.Ped

### Ped Runtime

<details>
<summary><strong>Create Ped</strong></summary>

Short description: Create a local client-side ped from one options table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Ped creation table |
| `options.model` | `string|number` | Ped model name or hash. Defaults to `a_m_m_business_01` |
| `options.coords` | `vector3|vector4|table` | Optional ped coordinates. When omitted, Bridge uses the local player position |
| `options.heading` | `number` | Optional heading |
| `options.handle` | `string` | Optional custom runtime handle |
| `options.pedType` | `number` | Optional ped type. Defaults to `4` |
| `options.freeze` | `boolean` | Freeze the ped after setup |
| `options.invincible` | `boolean` | Make the ped invincible |
| `options.blockEvents` | `boolean` | Block non-temporary events |
| `options.health` | `number` | Optional ped health |
| `options.maxHealth` | `number` | Optional max health |
| `options.armour` | `number` | Optional armour |
| `options.weapon` | `string|number|boolean` | Weapon name, weapon hash, or `false` to clear weapons |
| `options.ammo` | `number` | Optional weapon ammo |
| `options.scenario` | `string` | Optional scenario name |
| `options.animation` | `table` | Optional animation table with `dict`, `name`, `duration`, and flags |
| `options.voice` | `table|string` | Optional voice configuration |
| `options.speech` | `table|string` | Optional speech entries |
| `options.ambientSpeech` | `boolean` | Allow ambient speech |
| `options.proximitySpeech` | `table|number` | Optional proximity speech configuration |
| `options.combat` | `table|string|number` | Optional combat setup |
| `options.attachments` | `table[]` | Optional prop attachments |
| `options.target` | `table` | Optional target configuration |
| `options.point` | `table` | Optional interaction point configuration |
| `options.blip` | `table|boolean` | Optional blip configuration |
| `options.resource` | `string` | Optional resource owner name |
| `options.timeout` | `number` | Optional model request timeout |

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

Short description: Update one local ped entry. If `model` or `pedType` changes, Bridge recreates the ped under the same handle.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Runtime ped handle |
| `updates` | `table` | Partial update table using the same fields as create |

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

Short description: Remove one local client ped entry.

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

Short description: Read one local ped runtime entry.

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

Short description: Read the full local ped registry.

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

Short description: Remove local peds owned by one resource, or clear all local peds.

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
