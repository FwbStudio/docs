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
# Zones

This page documents the public `FWB.zones` helpers from `import.lua`.

## Public Calls

```lua
FWB.zones.poly(data)
FWB.zones.box(data)
FWB.zones.sphere(data)
FWB.zones.getAllZones()
FWB.zones.getCurrentZones()
FWB.zones.getNearbyZones()
```

## Zone Types

### Poly

```lua
local zone = FWB.zones.poly({
    points = {
        vec3(0.0, 0.0, 30.0),
        vec3(5.0, 0.0, 30.0),
        vec3(5.0, 5.0, 30.0),
    },
    thickness = 4
})
```

### Box

```lua
local zone = FWB.zones.box({
    coords = vec3(441.2, -981.9, 30.7),
    size = vec3(4.0, 4.0, 4.0),
    rotation = 90.0
})
```

### Sphere

```lua
local zone = FWB.zones.sphere({
    coords = vec3(441.2, -981.9, 30.7),
    radius = 2.0
})
```

## Notes

- This module is client-side.
- `poly` requires at least 3 points.
- `box` builds width, length, and thickness from the given size.
- `sphere` defaults to radius `2.0` when not provided.
- `getCurrentZones()` returns the zones the player is currently inside.
- `getNearbyZones()` returns nearby tracked zones.

