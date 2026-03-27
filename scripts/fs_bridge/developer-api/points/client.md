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

This page documents the public client-side point helpers.

## FWB.Points

### Points

<details>
<summary><strong>Create Point</strong></summary>

Short description: Create a client point entry that can react to `onEnter`, `onExit`, and `nearby` callbacks.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `data` | `table` | Preferred point data table |
| `data.coords` | `vector3|vector4|table` | Required point coordinates |
| `data.distance` | `number` | Required point distance |
| `data.onEnter` | `function` | Optional enter callback |
| `data.onExit` | `function` | Optional exit callback |
| `data.nearby` | `function` | Optional nearby callback |
| `coords` | `vector3|vector4|table` | Positional compatibility input |
| `distance` | `number` | Positional compatibility distance |
| `extraData` | `table` | Optional extra fields merged into the point |

Returns:

- `table` point object with `id`, `coords`, `distance`, and `remove()`

How to write it as function:

```lua
local point = FWB.Points.new(data)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local point = FWB.Points.new({
    coords = vec3(441.2, -981.9, 30.7),
    distance = 2.0,
    onEnter = function(self)
        print('entered point', self.id)
    end,
    onExit = function(self)
        print('left point', self.id)
    end,
    nearby = function(self)
        if IsControlJustReleased(0, 38) then
            print('pressed at point', self.id)
        end
    end
})
```

Example as export:

```lua
-- Use FWB.Points.new(...) through import.lua.
```

</details>

<details>
<summary><strong>Get All Points</strong></summary>

Short description: Read the full point registry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` points keyed by id

How to write it as function:

```lua
local points = FWB.Points.getAllPoints()
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local points = FWB.Points.getAllPoints()
print(points)
```

Example as export:

```lua
-- Use FWB.Points.getAllPoints() through import.lua.
```

</details>

<details>
<summary><strong>Get Nearby Points</strong></summary>

Short description: Read the list of currently nearby points.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table[]` nearby point entries

How to write it as function:

```lua
local points = FWB.Points.getNearbyPoints()
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local points = FWB.Points.getNearbyPoints()
print(points)
```

Example as export:

```lua
-- Use FWB.Points.getNearbyPoints() through import.lua.
```

</details>

<details>
<summary><strong>Get Closest Point</strong></summary>

Short description: Read the closest active point entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` closest point entry
- `nil` when no point is active

How to write it as function:

```lua
local point = FWB.Points.getClosestPoint()
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local point = FWB.Points.getClosestPoint()
print(point and point.id)
```

Example as export:

```lua
-- Use FWB.Points.getClosestPoint() through import.lua.
```

</details>
