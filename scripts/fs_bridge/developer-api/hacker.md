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
# Hacker

This page documents the public server-side `FWB.Hacker` helpers.

## Public Calls

```lua
FWB.Hacker.Kick(source, reason)
FWB.Hacker.Ban(source, reason)

exports['fs_bridge']:KickPlayer(source, reason)
exports['fs_bridge']:Ban(source, reason)
```

## Notes

- This module is server-side only.
- `FWB.Kick` and `FWB.Ban` still exist only as deprecated compatibility aliases.
- Ban and kick are expected to be overridden or handled by your framework/integration layer.

## Example

```lua
FWB.Hacker.Kick(source, 'Unauthorized event')
FWB.Hacker.Ban(source, 'Exploit detected')
```

