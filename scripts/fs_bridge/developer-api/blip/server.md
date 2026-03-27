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

This page documents the public server-side Blip API.

## FWB.Blip

### Blip Runtime

<details>
<summary><strong>Create Blip</strong></summary>

Short description: Create a server-managed static blip for one player, many players, or everyone.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Blip options table |
| `options.source` | `number|table|string` | Target source, target source list, or `-1` for everyone |
| `options.target` | `number|table|string` | Supported alias for `options.source` |
| `options.targets` | `table` | Supported alias for `options.source` |
| `options.handle` | `string` | Optional custom runtime handle |
| `options.coords` | `vector3|vector4|table` | Required blip coordinates |
| `options.title` | `string` | Optional display title |
| `options.id` | `number` | Optional sprite id |
| `options.scale` | `number` | Optional scale |
| `options.color` | `number` | Optional color id |
| `options.radius` | `number` | Optional radius circle size |
| `options.job` | `string|table` | Optional job filter |
| `options.jobs` | `string|table` | Optional multi-job filter |
| `options.grade` | `number` | Optional minimum grade |
| `options.whitelist` | `table` | Optional permission whitelist table |

Returns:

- `string, table` runtime handle and runtime entry
- `nil` when creation fails

How to write it as function:

```lua
local handle, entry = FWB.Blip.Create(options)
```

How to write it as export:

```lua
local handle, entry = exports['fs_bridge']:CreateBlip(options)
```

Example as function:

```lua
local handle, entry = FWB.Blip.Create({
    source = -1,
    coords = vec3(-267.0, -959.0, 31.2),
    title = 'Public Garage',
    id = 357,
    scale = 0.8,
    color = 2
})
```

Example as export:

```lua
local handle, entry = exports['fs_bridge']:CreateBlip({
    source = -1,
    coords = vec3(-267.0, -959.0, 31.2),
    title = 'Public Garage',
    id = 357,
    scale = 0.8,
    color = 2
})
```

</details>

<details>
<summary><strong>Create Moving Blip</strong></summary>

Short description: Create a server-managed moving blip that tracks a source, entity, or net id.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Moving blip options table |
| `options.source` | `number|table|string` | Target source, target source list, or `-1` for everyone |
| `options.trackSource` | `number` | Player source to track |
| `options.playerSource` | `number` | Supported alias for `trackSource` |
| `options.trackPlayer` | `number` | Supported alias for `trackSource` |
| `options.entity` | `number` | Optional entity handle to track |
| `options.netId` | `number` | Optional network id to track |
| `options.title` | `string` | Optional display title |
| `options.id` | `number` | Optional sprite id |
| `options.color` | `number` | Optional color id |
| `options.radius` | `number` | Optional radius circle size |
| `options.updateTime` | `number` | Update interval in milliseconds. Minimum `5000` |

Returns:

- `string, table` runtime handle and runtime entry
- `nil` when creation fails

How to write it as function:

```lua
local handle, entry = FWB.Blip.CreateMoving(options)
```

How to write it as export:

```lua
local handle, entry = exports['fs_bridge']:CreateMovingBlip(options)
```

Example as function:

```lua
local handle, entry = FWB.Blip.CreateMoving({
    source = -1,
    trackSource = source,
    title = 'Tracked Player',
    id = 1,
    color = 1,
    updateTime = 5000
})
```

Example as export:

```lua
local handle, entry = exports['fs_bridge']:CreateMovingBlip({
    source = -1,
    trackSource = source,
    title = 'Tracked Player',
    id = 1,
    color = 1,
    updateTime = 5000
})
```

</details>

<details>
<summary><strong>Update Blip</strong></summary>

Short description: Update one tracked server blip entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime blip handle |
| `updates` | `table` | Partial update table |

Returns:

- `string, table` runtime handle and updated entry
- `nil, nil` when the blip cannot be resolved

How to write it as function:

```lua
local resolvedHandle, entry = FWB.Blip.Update(handle, updates)
```

How to write it as export:

```lua
local resolvedHandle, entry = exports['fs_bridge']:UpdateBlip(handle, updates)
```

Example as function:

```lua
local resolvedHandle, entry = FWB.Blip.Update(handle, {
    color = 2,
    title = 'Mission Updated',
    radius = 150.0
})
```

Example as export:

```lua
local resolvedHandle, entry = exports['fs_bridge']:UpdateBlip(handle, {
    color = 2,
    title = 'Mission Updated',
    radius = 150.0
})
```

</details>

<details>
<summary><strong>Toggle Blip</strong></summary>

Short description: Hide or show a tracked server blip without deleting its runtime entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime blip handle |
| `enabled` | `boolean` | Set `false` to hide or `true` to show. Leave empty to invert the current state |

Returns:

- `boolean`

How to write it as function:

```lua
local success = FWB.Blip.Toggle(handle, enabled)
```

How to write it as export:

```lua
local success = exports['fs_bridge']:ToggleBlip(handle, enabled)
```

Example as function:

```lua
FWB.Blip.Toggle(handle, false)
```

Example as export:

```lua
exports['fs_bridge']:ToggleBlip(handle, false)
```

</details>

<details>
<summary><strong>Remove Blip</strong></summary>

Short description: Remove one tracked server blip.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime blip handle |

Returns:

- `boolean`

How to write it as function:

```lua
local success = FWB.Blip.Remove(handle)
```

How to write it as export:

```lua
local success = exports['fs_bridge']:RemoveBlip(handle)
```

Example as function:

```lua
FWB.Blip.Remove(handle)
```

Example as export:

```lua
exports['fs_bridge']:RemoveBlip(handle)
```

</details>

<details>
<summary><strong>Get Blip</strong></summary>

Short description: Read one tracked server blip entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime blip handle |

Returns:

- `table` blip entry
- `nil` when the blip cannot be resolved

How to write it as function:

```lua
local entry = FWB.Blip.Get(handle)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetBlip(handle)
```

Example as function:

```lua
local entry = FWB.Blip.Get(handle)
print(entry and entry.handle)
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetBlip(handle)
print(entry and entry.handle)
```

</details>

<details>
<summary><strong>Get All Blips</strong></summary>

Short description: Read the full server blip registry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` blip entries keyed by handle

How to write it as function:

```lua
local blips = FWB.Blip.GetAll()
```

How to write it as export:

```lua
local blips = exports['fs_bridge']:GetAllBlips()
```

Example as function:

```lua
local blips = FWB.Blip.GetAll()
print(blips)
```

Example as export:

```lua
local blips = exports['fs_bridge']:GetAllBlips()
print(blips)
```

</details>

<details>
<summary><strong>Clear Blips</strong></summary>

Short description: Remove server blips owned by one resource, or clear all tracked server blips.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Optional resource owner filter |

Returns:

- `nil`

How to write it as function:

```lua
FWB.Blip.Clear(resource)
```

How to write it as export:

```lua
exports['fs_bridge']:ClearBlips(resource)
```

Example as function:

```lua
FWB.Blip.Clear(GetCurrentResourceName())
```

Example as export:

```lua
exports['fs_bridge']:ClearBlips(GetCurrentResourceName())
```

</details>
