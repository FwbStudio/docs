# FWB.Blip

`FWB.Blip` is the public blip runtime for both client and server use.

## Public Calls

```lua
FWB.Blip.Create(options)
FWB.Blip.CreateMoving(options)
FWB.Blip.Update(handle, updates)
FWB.Blip.Toggle(handle, enabled)
FWB.Blip.Remove(handle)
FWB.Blip.Get(handle)
FWB.Blip.GetAll()
FWB.Blip.Clear(resource)
```

Export equivalents are also available through `exports.fs_bridge:*`.

<details>
<summary><strong>Create A Static Blip</strong></summary>

Short description: Create a normal coordinates-based blip.

Signature:

```lua
FWB.Blip.Create(options)
exports.fs_bridge:CreateBlip(options)
```

Common options:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Required for static blips |
| `handle` | `string` | Optional custom handle |
| `title` | `string` | Blip label |
| `id` | `number` | Sprite id |
| `scale` | `number` | Blip scale |
| `color` | `number` | Blip color |
| `route` | `boolean` | Draw GPS route |
| `radius` | `number` | Optional radius zone |
| `source` | `number` | Server target audience |

Returns:

- created handle

Example usage:

```lua
local handle = FWB.Blip.Create({
    coords = vec3(215.76, -810.12, 30.73),
    title = 'Garage',
    id = 357,
    color = 3
})
```

Notes:

- client-created blips are local only
- server-created blips can target one player or everyone

</details>

<details>
<summary><strong>Create A Moving Blip</strong></summary>

Short description: Track a player, ped, vehicle, object, or net id over time.

Signature:

```lua
FWB.Blip.CreateMoving(options)
exports.fs_bridge:CreateMovingBlip(options)
```

Common options:

| Key | Type | Notes |
|---|---|---|
| `entity` | `number` | Track an entity |
| `player` | `number` | Track a client player id |
| `serverId` | `number` | Track a server id on client |
| `trackSource` | `number` | Track a player source on server |
| `updateTime` | `number` | Minimum `5000` ms |
| `title` | `string` | Label |
| `id` | `number` | Sprite id |
| `color` | `number` | Blip color |
| `radius` | `number` | Optional radius zone |

Returns:

- created handle

Example usage:

```lua
local handle = FWB.Blip.CreateMoving({
    source = -1,
    trackSource = source,
    title = 'Tracked Player',
    id = 1,
    color = 1,
    updateTime = 5000
})
```

Notes:

- values below `5000` ms are clamped to `5000`

</details>

<details>
<summary><strong>Update A Blip</strong></summary>

Short description: Change title, scale, color, coords, route, radius, or target audience.

Signature:

```lua
FWB.Blip.Update(handle, updates)
exports.fs_bridge:UpdateBlip(handle, updates)
```

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Blip handle |
| `updates` | `table` | Partial updates table |

Returns:

- framework-specific update result

Example usage:

```lua
FWB.Blip.Update(handle, {
    title = 'Garage Updated',
    color = 5,
    route = true
})
```

Notes:

- on server, `updates.source` can retarget the audience

</details>

<details>
<summary><strong>Toggle Or Remove A Blip</strong></summary>

Short description: Temporarily hide a blip or fully remove it.

Signature:

```lua
FWB.Blip.Toggle(handle, enabled)
FWB.Blip.Remove(handle)
```

Returns:

- toggle result or remove result

Example usage:

```lua
FWB.Blip.Toggle(handle, false)
FWB.Blip.Remove(handle)
```

Notes:

- `Toggle` keeps the stored record
- `Remove` deletes it

</details>

<details>
<summary><strong>Read Registry Data</strong></summary>

Short description: Read one blip, all blips, or clear by resource.

Signature:

```lua
FWB.Blip.Get(handle)
FWB.Blip.GetAll()
FWB.Blip.Clear(resource)
```

Returns:

- one entry table
- table of all entries
- clear result

Example usage:

```lua
local entry = FWB.Blip.Get(handle)
local allBlips = FWB.Blip.GetAll()
```

Notes:

- `Get(handle)` returns metadata such as `handle`, `resource`, and `options`

</details>
