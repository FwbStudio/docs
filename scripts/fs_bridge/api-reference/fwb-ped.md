# FWB.Ped

`FWB.Ped` is the handle-based ped runtime for both local and server-managed peds.

## Public Calls

```lua
FWB.Ped.Create(options)
FWB.Ped.Update(handle, updates)
FWB.Ped.Remove(handle)
FWB.Ped.Get(handle)
FWB.Ped.GetAll()
FWB.Ped.Clear(resource)
```

<details>
<summary><strong>Create A Ped</strong></summary>

Short description: Spawn a ped with runtime options such as freeze, combat, point, target, and blip support.

Signature:

```lua
FWB.Ped.Create(options)
exports.fs_bridge:CreatePed(options)
```

Common options:

| Key | Type | Notes |
|---|---|---|
| `model` | `string` or `number` | Required ped model |
| `coords` | `vector4` | Spawn location |
| `freeze` | `boolean` | Freeze ped |
| `invincible` | `boolean` | God mode |
| `blockEvents` | `boolean` | Ignore ambient events |
| `weapon` | `string` | Optional weapon |
| `ammo` | `number` | Weapon ammo |
| `combat` | `table` | Guard or aggression options |
| `attachments` | `table` | Attached props |
| `target` | `table` | Target integration options |
| `point` | `table` | Point interaction |
| `blip` | `table` | Attached blip options |
| `source` | `number` | Server-side player target |

Returns:

- `handle`
- `netId`
- `ped`

Example usage:

```lua
local handle, netId, ped = FWB.Ped.Create({
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true,
    invincible = true
})
```

Notes:

- server-created peds should be managed from the server

</details>

<details>
<summary><strong>Update A Ped</strong></summary>

Short description: Update runtime fields or recreate the ped under the same handle when the model changes.

Signature:

```lua
FWB.Ped.Update(handle, updates)
exports.fs_bridge:UpdatePed(handle, updates)
```

Returns:

- `success`
- updated `entry`

Example usage:

```lua
local success, entry = FWB.Ped.Update(handle, {
    freeze = false,
    coords = vec4(450.0, -980.0, 30.7, 180.0)
})
```

Notes:

- model or ped-type changes trigger recreation under the same handle

</details>

<details>
<summary><strong>Remove A Ped</strong></summary>

Short description: Remove a runtime ped by handle.

Signature:

```lua
FWB.Ped.Remove(handle)
```

Returns:

- `success`

Example usage:

```lua
FWB.Ped.Remove(handle)
```

Notes:

- remove server-managed peds from server-side code

</details>

<details>
<summary><strong>Read Registry Data</strong></summary>

Short description: Read one ped entry, all ped entries, or clear by resource.

Signature:

```lua
FWB.Ped.Get(handle)
FWB.Ped.GetAll()
FWB.Ped.Clear(resource)
```

Returns:

- one ped entry
- all ped entries
- clear result

Example usage:

```lua
local entry = FWB.Ped.Get(handle)
local allPeds = FWB.Ped.GetAll()
```

Notes:

- entries commonly include `handle`, `netId`, `resource`, and `options`

</details>
