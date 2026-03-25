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
# Cache

This page documents the current public Bridge cache surface.

Important: in the current live build, the public cache helper is `Cache` after `import.lua` is loaded. There is not a separate public `FWB.Cache` table.

## Access Styles

| Style | Example |
|---|---|
| `import.lua` | `Cache.Ped` |
| direct export | `exports['fs_bridge']:Cache('Ped')` |
| cache listener | `FWB.onCache('fs_bridge_playerjob', function(value, oldValue) end)` |

## Protected Keys

These keys are maintained by Bridge and should be read, not overwritten.

| Key | Side |
|---|---|
| `Ped` | client |
| `Vehicle` | client |
| `Seat` | client |
| `Weapon` | client |
| `Ammo` | client |
| `Playerid` | client |
| `Serverid` | client |
| `Coords` | client |
| `fs_bridge_playerjob` | client |
| `IsServerSide` | client and server |
| `Resource` | client and server |
| `CacheReady` | client and server |

<details>
<summary><strong>Read cache after import.lua</strong></summary>

Use `Cache` directly after your resource loads `@fs_bridge/import.lua`.

```lua
print(Cache.Ped)
print(Cache.Vehicle)
print(Cache.CacheReady)
print(Cache.fs_bridge_playerjob)
```

Typical use:

```lua
if not Cache.CacheReady then return end

local ped = Cache.Ped
local vehicle = Cache.Vehicle
local job = Cache.fs_bridge_playerjob
```

</details>

<details>
<summary><strong>Read cache through exports</strong></summary>

Use the export when you do not want to load `import.lua`.

```lua
local ped = exports['fs_bridge']:Cache('Ped')
local coords = exports['fs_bridge']:Cache('Coords')
local ready = exports['fs_bridge']:Cache('fs_bridge', 'CacheReady')
```

Bridge reads the invoking resource bucket when you pass one key, or a specific bucket when you pass `resource, key`.

</details>

<details>
<summary><strong>Store your own cache values with Cache.Set</strong></summary>

`Cache.Set(key, value)` stores a value for your resource and syncs it through Bridge.

```lua
local changed = Cache.Set('garage_open', true)
print(changed)
```

Returns:

- `true` when the value changed
- `false` when the value did not change
- `false, 'protected_key'` when you try to overwrite a protected Bridge key

</details>

<details>
<summary><strong>Memoize values with Cache(key, resolver, timeout)</strong></summary>

`Cache(key, resolver, timeout)` lets you memoize a value for your resource and optionally expire it later.

```lua
local result = Cache('garage_label', function()
    return ('Garage %s'):format(GetCurrentResourceName())
end, 5000)
```

Arguments:

| Name | Type | Notes |
|---|---|---|
| `key` | `string` | Resource cache key |
| `resolver` | `function` | Called only when the key is missing |
| `timeout` | `number` | Optional timeout in milliseconds before Bridge clears the key |

Returns:

- current cached value for that key

</details>

<details>
<summary><strong>Listen for updates with FWB.onCache</strong></summary>

Use `FWB.onCache(key, cb)` to react when a cache value changes.

```lua
FWB.onCache('fs_bridge_playerjob', function(value, oldValue)
    print(value and value.name, oldValue and oldValue.name)
end)
```

Arguments:

| Name | Type | Notes |
|---|---|---|
| `key` | `string` | Cache key to watch |
| `cb` | `function` | Callback that receives `value, oldValue` |

Returns:

- nothing

Notes:

- If the value is already available, Bridge fires the callback immediately with the current value.
- This is the clean public way to react to protected cache updates like `fs_bridge_playerjob`.

</details>