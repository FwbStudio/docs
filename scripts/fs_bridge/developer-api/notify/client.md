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

This page documents the public client-side notification helper.

## FWB.Notify

### Notifications

<details>
<summary><strong>Notify</strong></summary>

Short description: Send a client notification through the active Bridge notification integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `argument` | `table|string` | Notification payload, or a plain string that Bridge converts to `{ description = argument }` |
| `argument.title` | `string` | Optional title |
| `argument.description` | `string` | Main notification text |
| `argument.type` | `string` | Optional type such as `inform`, `success`, `warning`, or `error` |
| `argument.position` | `string` | Optional position. Defaults to `top` |
| `argument.duration` | `number` | Optional duration in milliseconds. Defaults to `5000` |

Returns:

- integration-specific result
- `nil`

How to write it as function:

```lua
FWB.Notify(argument)
```

How to write it as export:

```lua
exports['fs_bridge']:Notify(argument)
```

Example as function:

```lua
FWB.Notify({
    title = 'Bridge',
    description = 'Vehicle created successfully',
    type = 'success',
    duration = 5000,
    position = 'top'
})
```

Example as export:

```lua
exports['fs_bridge']:Notify({
    title = 'Bridge',
    description = 'Vehicle created successfully',
    type = 'success',
    duration = 5000,
    position = 'top'
})
```

</details>
