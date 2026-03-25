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

This page documents the public server-side callback API.

You can call these helpers through `FWB.CB.*` after `GetObject()` or `import.lua`, and through the exported callback helpers shown in each block.
## FWB.CB

<details>
<summary><strong>Await(eventName, player, ...)</strong></summary>

Short description: Trigger a registered client callback on a target player and wait for the return values on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Registered callback name |
| `player` | `number` | Target player source |
| `...` | `any` | Optional payload passed through to the callback |

Returns:

- one or more callback return values
- `nil` when the callback returns nothing

How to write it as function:

```lua
local result = FWB.CB.Await(eventName, player, ...)
```

How to write it as export:

```lua
local result = exports['fs_bridge']:AwaitCallback(eventName, player, ...)
```

Example as function:

```lua
local canOpen = FWB.CB.Await('garage:clientCanOpen', source, 'ABC123')
```

Example as export:

```lua
local canOpen = exports['fs_bridge']:AwaitCallback('garage:clientCanOpen', source, 'ABC123')
```

</details>

<details>
<summary><strong>Register(eventName, callback)</strong></summary>

Short description: Register a server callback that can be triggered from client code through Bridge callback routing.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Callback name to register |
| `callback` | `function` | Lua function that receives `source` first and may return one or more values |

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
FWB.CB.Register('garage:getLabel', function(playerSource, plate)
    return ('Garage lookup for %s'):format(plate)
end)
```

Example as export:

```lua
exports['fs_bridge']:RegisterCallback('garage:getLabel', function(playerSource, plate)
    return ('Garage lookup for %s'):format(plate)
end)
```

</details>

<details>
<summary><strong>DoesRegistered(player, name)</strong></summary>

Short description: Check whether a client callback is currently registered on a target player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `player` | `number` | Target player source |
| `name` | `string` | Callback name to check |

Returns:

- `boolean`

How to write it as function:

```lua
local exists = FWB.CB.DoesRegistered(player, name)
```

How to write it as export:

```lua
local exists = exports['fs_bridge']:DoesClientCallbackRegistered(player, name)
```

Example as function:

```lua
local exists = FWB.CB.DoesRegistered(source, 'garage:clientCanOpen')
```

Example as export:

```lua
local exists = exports['fs_bridge']:DoesClientCallbackRegistered(source, 'garage:clientCanOpen')
```

</details>
