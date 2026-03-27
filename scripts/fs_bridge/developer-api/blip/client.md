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

This page documents the public client-side Blip API.

## FWB.Blip

### Blip Runtime

<details>
<summary><strong>Create Blip</strong></summary>

Short description: Create a local static blip from one options table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Blip options table |
| `options.handle` | `string` | Optional custom runtime handle |
| `options.coords` | `vector3|vector4|table` | Required blip coordinates |
| `options.title` | `string` | Optional display title |
| `options.id` | `number` | Optional sprite id |
| `options.scale` | `number` | Optional scale. Defaults to `0.7` |
| `options.color` | `number` | Optional color id |
| `options.shortRange` | `boolean` | Optional short-range flag |
| `options.shortrange` | `boolean` | Supported alias for `shortRange` |
| `options.route` | `boolean` | Set `true` to enable GPS route |
| `options.routeColor` | `number` | Optional route color |
| `options.radius` | `number` | Optional radius circle size |
| `options.radiusColor` | `number` | Optional radius color |
| `options.radiusAlpha` | `number` | Optional radius alpha |
| `options.time` | `number` | Optional auto-remove time in milliseconds |
| `options.persist` | `boolean` | Keep the blip even when `time` is set |
| `options.permanent` | `boolean` | Supported alias for `persist` |

Returns:

- `string, table` runtime handle and runtime entry
- `nil, nil` when creation fails

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
    coords = vec3(215.76, -810.12, 30.73),
    title = 'Garage',
    id = 357,
    scale = 0.9,
    color = 3
})
```

Example as export:

```lua
local handle, entry = exports['fs_bridge']:CreateBlip({
    coords = vec3(215.76, -810.12, 30.73),
    title = 'Garage',
    id = 357,
    scale = 0.9,
    color = 3
})
```

</details>

<details>
<summary><strong>Create Moving Blip</strong></summary>

Short description: Create a local moving blip that tracks an entity, player, or network id.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Moving blip options table |
| `options.entity` | `number` | Optional entity handle to track |
| `options.ped` | `number` | Optional ped handle to track |
| `options.vehicle` | `number` | Optional vehicle handle to track |
| `options.object` | `number` | Optional object handle to track |
| `options.netId` | `number` | Optional network id to track |
| `options.player` | `number` | Optional client player id |
| `options.playerId` | `number` | Supported alias for `options.player` |
| `options.serverId` | `number` | Optional server player id |
| `options.title` | `string` | Optional display title |
| `options.id` | `number` | Optional sprite id |
| `options.color` | `number` | Optional color id |
| `options.updateTime` | `number` | Update interval in milliseconds. Minimum `5000` |
| `options.radius` | `number` | Optional radius circle size |
| `options.timeout` | `number` | Optional wait time used when resolving `netId` |

Returns:

- `string, table` runtime handle and runtime entry
- `nil, nil` when creation fails

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
    title = 'Tracked Ped',
    id = 1,
    color = 5,
    entity = PlayerPedId(),
    updateTime = 5000
})
```

Example as export:

```lua
local handle, entry = exports['fs_bridge']:CreateMovingBlip({
    title = 'Tracked Ped',
    id = 1,
    color = 5,
    entity = PlayerPedId(),
    updateTime = 5000
})
```

</details>

<details>
<summary><strong>Update Blip</strong></summary>

Short description: Update one tracked client blip entry by handle.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime handle, or a native blip id that Bridge can resolve |
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
    scale = 1.0,
    route = true
})
```

Example as export:

```lua
local resolvedHandle, entry = exports['fs_bridge']:UpdateBlip(handle, {
    color = 2,
    scale = 1.0,
    route = true
})
```

</details>

<details>
<summary><strong>Toggle Blip</strong></summary>

Short description: Hide or show a tracked client blip without removing its runtime entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime handle or native blip id |
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

Short description: Remove one tracked client blip.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime handle or native blip id |

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

Short description: Read one tracked client blip entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string|number` | Runtime handle or native blip id |

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

Short description: Read the full local blip registry.

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

Short description: Remove local blips owned by one resource, or clear all local non-server-managed blips.

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
