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

# 🧩 Manual Compatibility

Use manual compatibility when your setup needs custom behavior that is not already covered by supported integrations.

## 📍 Where Manual Compatibility Code Goes

Client side:

```lua
unlocked/client.lua
```

Server side:

```lua
unlocked/server.lua
```

## Overrides

Below is a sample override entry so the rest of the manual compatibility docs can follow the same format.

<details>
<summary><strong>Hunger</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your own status system

Override code:

```lua
function Override.AddHunger(value)
    TriggerEvent('my_status:add', 'hunger', value)
end

function Override.RemoveHunger(value)
    TriggerEvent('my_status:remove', 'hunger', value)
end
```

Notes:

- this is client-side
- replace the event names with the ones from your own status system

</details>