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
# Points

This page documents the public `FWB.Points` helpers from `import.lua`.

## Public Calls

```lua
FWB.Points.new(data)
FWB.Points.new(coords, distance, data)
FWB.Points.getAllPoints()
FWB.Points.getNearbyPoints()
FWB.Points.getClosestPoint()
```

## Point Data

Common point fields:

- `coords`
- `distance`
- `onEnter(self)`
- `onExit(self)`
- `nearby(self)`

Returned point objects include:

- `id`
- `coords`
- `distance`
- `currentDistance`
- `isClosest`
- `remove()`

## Notes

- This module is client-side.
- `nearby(self)` runs repeatedly while the player stays inside the point distance.
- `onEnter(self)` runs once when the player enters.
- `onExit(self)` runs once when the player leaves.

## Example

```lua
local point = FWB.Points.new({
    coords = vec3(441.2, -981.9, 30.7),
    distance = 2.0,
    onEnter = function(self)
        print('entered', self.id)
    end,
    onExit = function(self)
        print('left', self.id)
    end,
    nearby = function(self)
        print('inside', self.currentDistance)
    end
})
```

