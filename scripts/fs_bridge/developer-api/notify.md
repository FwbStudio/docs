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
# Notify

This page documents the public `FWB.Notify` helper.

## Client

```lua
FWB.Notify(argument)
exports['fs_bridge']:Notify(argument)
```

If `argument` is a string, Bridge converts it to:

```lua
{ description = argument }
```

Common client fields:

- `title`
- `description`
- `type`
- `position`
- `duration`

## Server

```lua
FWB.Notify(source, argument)
exports['fs_bridge']:Notify(source, argument)
```

The server helper forwards the notification to the target client.

## Example

```lua
FWB.Notify({
    title = 'Bridge',
    description = 'Vehicle created successfully',
    type = 'success',
    duration = 5000,
    position = 'top'
})
```

