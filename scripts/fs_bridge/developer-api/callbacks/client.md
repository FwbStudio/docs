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

This page documents the public client-side callback API.

You can call these helpers through `FWB.CB.*` after `GetObject()` or `import.lua`, and through the exported callback helpers shown in each block.
## FWB.CB

<details>
<summary><strong>Await(eventName, ...)</strong></summary>

Short description: Trigger a registered server callback and wait for the return values on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Registered callback name |
| `...` | `any` | Optional payload passed through to the callback |

Returns:

- one or more callback return values
- `nil` when the callback returns nothing

How to write it as function:

```lua
local result = FWB.CB.Await(eventName, ...)
```

How to write it as export:

```lua
local result = exports['fs_bridge']:AwaitCallback(eventName, ...)
```

Example as function:

```lua
local vehicleLabel = FWB.CB.Await('garage:getLabel', 'ABC123')
```

Example as export:

```lua
local vehicleLabel = exports['fs_bridge']:AwaitCallback('garage:getLabel', 'ABC123')
```

Notes:

- Client callback waits up to roughly 15 seconds before timing out.

</details>

<details>
<summary><strong>Register(eventName, callback)</strong></summary>

Short description: Register a client callback that can be triggered from the server through Bridge callback routing.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Callback name to register |
| `callback` | `function` | Lua function that returns one or more values |

Returns:

- nothing

How to write it as function:

```lua
FWB.CB.Register(eventName, callback)
```

How to write it as export:

```lua
exports['fs_bridge']:RegisterCallback(eventName, callback)
```

Example as function:

```lua
FWB.CB.Register('garage:clientCanOpen', function(plate)
    return plate == 'ABC123'
end)
```

Example as export:

```lua
exports['fs_bridge']:RegisterCallback('garage:clientCanOpen', function(plate)
    return plate == 'ABC123'
end)
```

Notes:

- The callback can return one or more values back to the server.

</details>

<details>
<summary><strong>DoesRegistered(name)</strong></summary>

Short description: Check whether a server callback is currently registered and reachable through Bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `name` | `string` | Callback name to check |

Returns:

- `boolean`

How to write it as function:

```lua
local exists = FWB.CB.DoesRegistered(name)
```

How to write it as export:

```lua
local exists = exports['fs_bridge']:DoesServerCallbackRegistered(name)
```

Example as function:

```lua
local exists = FWB.CB.DoesRegistered('garage:getLabel')
```

Example as export:

```lua
local exists = exports['fs_bridge']:DoesServerCallbackRegistered('garage:getLabel')
```

Notes:

- This checks the server-side callback registry from the client.

</details>
