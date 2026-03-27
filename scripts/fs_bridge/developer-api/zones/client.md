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

This page documents the public client-side zone helpers.

## FWB.zones

### Zones

<details>
<summary><strong>Create Poly Zone</strong></summary>

Short description: Create a polygon zone from a points table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `data` | `table` | Poly zone data table |
| `data.points` | `table` | Required zone points. Minimum `3` points |
| `data.thickness` | `number` | Optional zone thickness. Defaults to `4` |
| `data.onEnter` | `function` | Optional enter callback |
| `data.onExit` | `function` | Optional exit callback |
| `data.inside` | `function` | Optional inside callback |
| `data.debug` | `boolean` | Enable debug drawing |

Returns:

- `table` zone object

How to write it as function:

```lua
local zone = FWB.zones.poly(data)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local zone = FWB.zones.poly({
    points = {
        vec3(441.0, -982.0, 30.7),
        vec3(445.0, -982.0, 30.7),
        vec3(445.0, -978.0, 30.7),
        vec3(441.0, -978.0, 30.7)
    },
    thickness = 4,
    onEnter = function(self)
        print('entered zone', self.id)
    end
})
```

Example as export:

```lua
-- Use FWB.zones.poly(...) through import.lua.
```

</details>

<details>
<summary><strong>Create Box Zone</strong></summary>

Short description: Create a box zone from center coordinates and size.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `data` | `table` | Box zone data table |
| `data.coords` | `vector3|vector4|table` | Required zone center |
| `data.size` | `vector3|vector4|table` | Required zone size |
| `data.rotation` | `number` | Optional rotation |
| `data.onEnter` | `function` | Optional enter callback |
| `data.onExit` | `function` | Optional exit callback |
| `data.inside` | `function` | Optional inside callback |
| `data.debug` | `boolean` | Enable debug drawing |

Returns:

- `table` zone object

How to write it as function:

```lua
local zone = FWB.zones.box(data)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local zone = FWB.zones.box({
    coords = vec3(441.2, -981.9, 30.7),
    size = vec3(4.0, 4.0, 4.0),
    rotation = 90.0
})
```

Example as export:

```lua
-- Use FWB.zones.box(...) through import.lua.
```

</details>

<details>
<summary><strong>Create Sphere Zone</strong></summary>

Short description: Create a sphere zone from center coordinates and radius.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `data` | `table` | Sphere zone data table |
| `data.coords` | `vector3|vector4|table` | Required zone center |
| `data.radius` | `number` | Optional radius. Defaults to `2` |
| `data.onEnter` | `function` | Optional enter callback |
| `data.onExit` | `function` | Optional exit callback |
| `data.inside` | `function` | Optional inside callback |
| `data.debug` | `boolean` | Enable debug drawing |

Returns:

- `table` zone object

How to write it as function:

```lua
local zone = FWB.zones.sphere(data)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local zone = FWB.zones.sphere({
    coords = vec3(441.2, -981.9, 30.7),
    radius = 3.0
})
```

Example as export:

```lua
-- Use FWB.zones.sphere(...) through import.lua.
```

</details>

<details>
<summary><strong>Get All Zones</strong></summary>

Short description: Read the full zone registry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` all zones keyed by id

How to write it as function:

```lua
local zones = FWB.zones.getAllZones()
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local zones = FWB.zones.getAllZones()
print(zones)
```

Example as export:

```lua
-- Use FWB.zones.getAllZones() through import.lua.
```

</details>

<details>
<summary><strong>Get Current Zones</strong></summary>

Short description: Read the zones the local player is currently inside.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` current inside zones keyed by id

How to write it as function:

```lua
local zones = FWB.zones.getCurrentZones()
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local zones = FWB.zones.getCurrentZones()
print(zones)
```

Example as export:

```lua
-- Use FWB.zones.getCurrentZones() through import.lua.
```

</details>

<details>
<summary><strong>Get Nearby Zones</strong></summary>

Short description: Read the cached nearby zone list.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table[]` nearby zones

How to write it as function:

```lua
local zones = FWB.zones.getNearbyZones()
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local zones = FWB.zones.getNearbyZones()
print(zones)
```

Example as export:

```lua
-- Use FWB.zones.getNearbyZones() through import.lua.
```

</details>
