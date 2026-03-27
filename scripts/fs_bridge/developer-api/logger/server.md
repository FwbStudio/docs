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

This page documents the public server-side logging helper.

## FWB.Log

### Logging

<details>
<summary><strong>Create Log</strong></summary>

Short description: Send a log event through the active Bridge logging integration or your override flow.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source related to the log |
| `event` | `string` | Event or category name |
| `message` | `string` | Main log text |
| `...` | `any` | Optional extra values passed through to the logger implementation |

Returns:

- `nil`

How to write it as function:

```lua
FWB.Log.Create(source, event, message, ...)
```

How to write it as export:

```lua
exports['fs_bridge']:CreateLog(source, event, message, ...)
```

Example as function:

```lua
FWB.Log.Create(source, 'garage:create', 'Vehicle created successfully', {
    plate = 'ABC123'
})
```

Example as export:

```lua
exports['fs_bridge']:CreateLog(source, 'garage:create', 'Vehicle created successfully', {
    plate = 'ABC123'
})
```

</details>
