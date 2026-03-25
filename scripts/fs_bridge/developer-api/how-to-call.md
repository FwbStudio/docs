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
# How To Call

You can call the public Bridge API in three clean ways.

## 1. Get The Bridge Object With Exports

Use this when you want the full namespaced API in one local variable.

```lua
local FWB = exports['fs_bridge']:GetObject()

if FWB.Player.IsLoaded() then
    print(FWB.Player.Name())
end
```

This style works on both client and server.

## 2. Call Direct Exports

Use this when you only need one or two functions and do not want to keep a local Bridge object.

```lua
if exports['fs_bridge']:IsPlayerLoaded() then
    print(exports['fs_bridge']:GetPlayerName())
end

local canOpen = exports['fs_bridge']:AwaitCallback('garage:clientCanOpen', 'ABC123')
```

Direct exports are available only for functions that Bridge explicitly exports.

## 3. Use `import.lua`

Use this when you want `FWB` and `Cache` available directly in your script.

If your resource uses Bridge on both client and server, add this to your `fxmanifest.lua`:

```lua
shared_script '@fs_bridge/import.lua'
```

If you only need one side, you can load it on that side only:

```lua
client_script '@fs_bridge/import.lua'
server_script '@fs_bridge/import.lua'
```

After `import.lua` is loaded, you can call Bridge like this:

```lua
if FWB.Player.IsLoaded() then
    print(FWB.Player.Name())
end

print(Cache.Ped)
print(Cache.Vehicle)
```

## What `import.lua` Gives You

| Public helper | What it does |
|---|---|
| `FWB` | Public Bridge object |
| `Cache` | Public cache table and cache helper |
| `FWB.onCache` | Listen for cache updates |

## Which Style Should You Use?

- Use `GetObject()` when your file makes several Bridge calls.
- Use direct exports when you only need a small number of exported helpers.
- Use `import.lua` when you want the cleanest function-style API inside your own resource.