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

This page documents the public server-side notification helper.

## FWB.Notify

### Notifications

<details>
<summary><strong>Notify</strong></summary>

Short description: Forward a notification from the server to one target client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `argument` | `table|string` | Notification payload, or a plain string that Bridge converts to `{ description = argument }` on the client |

Returns:

- `nil`

How to write it as function:

```lua
FWB.Notify(source, argument)
```

How to write it as export:

```lua
exports['fs_bridge']:Notify(source, argument)
```

Example as function:

```lua
FWB.Notify(source, {
    title = 'Bridge',
    description = 'Garage updated',
    type = 'inform'
})
```

Example as export:

```lua
exports['fs_bridge']:Notify(source, {
    title = 'Bridge',
    description = 'Garage updated',
    type = 'inform'
})
```

</details>
