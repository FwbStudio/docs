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
# Logger

This page documents the public server-side `FWB.Log` helper.

## Public Calls

```lua
FWB.Log.Create(source, event, message, ...)
exports['fs_bridge']:CreateLog(source, event, message, ...)
```

## Notes

- This module is server-side.
- `FWB.CreateLog(...)` still exists only as a deprecated compatibility alias.
- Bridge forwards log creation into the active logger integrations or override flow.

## Example

```lua
FWB.Log.Create(source, 'garage:create', 'Player created a vehicle', {
    plate = 'ABC123'
})
```

