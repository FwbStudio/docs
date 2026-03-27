# FWB.Player.Request

`FWB.Player.Request` groups the client-side asset request helpers for animation dictionaries, models, animation sets, clip sets, particle assets, and weapon assets.

## Public Calls

```lua
FWB.Player.Request.AnimDict(options)
FWB.Player.Request.Model(options)
FWB.Player.Request.AnimSet(options)
FWB.Player.Request.ClipSet(options)
FWB.Player.Request.NamedPtfxAsset(options)
FWB.Player.Request.WeaponAsset(options)
```

## Common Rules

- all request helpers return `true` on success and `false` on failure
- `FWB.Player.Request.*` uses one options table only
- the extra second `timeout` argument is not part of the new request contract
- default `timeout` is `10000`
- `silent = true` disables failure prints
- `keepLoaded = true` keeps the asset loaded after a successful request
- deprecated compatibility is still kept for `FWB.RequestAnimDict(dict, timeout)` and `FWB.RequestModel(model, timeout)`

<details>
<summary><strong>Request Anim Dict</strong></summary>

Short description: Load an animation dictionary before playing an animation.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `dict` | `string` | Required animation dictionary |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

How to write it:

```lua
local ok = FWB.Player.Request.AnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000,
    silent = false,
    keepLoaded = true
})
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestAnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000,
    silent = false,
    keepLoaded = true
})
```

Example usage:

```lua
local ok = FWB.Player.Request.AnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000
})

if ok then
    print('Anim dict loaded')
end
```

Notes:

- use this before `TaskPlayAnim`

</details>

<details>
<summary><strong>Request Model</strong></summary>

Short description: Load a model before creating a ped, prop, or vehicle.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `model` | `string|number` | Required model name or hash |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |
| `requireValid` | `boolean` | Default `true` |

Returns:

- `boolean`

How to write it:

```lua
local ok = FWB.Player.Request.Model({
    model = 'adder',
    timeout = 5000,
    keepLoaded = true,
    requireValid = true
})
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestModel({
    model = 'adder',
    timeout = 5000,
    keepLoaded = true,
    requireValid = true
})
```

Example usage:

```lua
local ok = FWB.Player.Request.Model({
    model = 'adder',
    timeout = 5000,
    keepLoaded = true,
    requireValid = true
})

if ok then
    print('Model loaded')
end
```

Notes:

- this helper is also used internally by other runtime helpers that need a loaded model

</details>

<details>
<summary><strong>Request Anim Set</strong></summary>

Short description: Load an animation set before applying it to a ped.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `animSet` | `string` | Required animation set name |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

How to write it:

```lua
local ok = FWB.Player.Request.AnimSet({
    animSet = 'move_m@drunk@slightlydrunk',
    timeout = 5000
})
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestAnimSet({
    animSet = 'move_m@drunk@slightlydrunk',
    timeout = 5000
})
```

Example usage:

```lua
FWB.Player.Request.AnimSet({
    animSet = 'move_m@drunk@slightlydrunk',
    timeout = 5000
})
```

Notes:

- use this before applying a movement set

</details>

<details>
<summary><strong>Request Clip Set</strong></summary>

Short description: Load a clip set before applying it to a ped.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `clipSet` | `string` | Required clip set name |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

How to write it:

```lua
local ok = FWB.Player.Request.ClipSet({
    clipSet = 'move_ped_crouched',
    timeout = 5000
})
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestClipSet({
    clipSet = 'move_ped_crouched',
    timeout = 5000
})
```

Example usage:

```lua
FWB.Player.Request.ClipSet({
    clipSet = 'move_ped_crouched',
    timeout = 5000
})
```

Notes:

- use this before applying a clip set

</details>

<details>
<summary><strong>Request Named Ptfx Asset</strong></summary>

Short description: Load a named particle asset before using particle effects.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `asset` | `string` | Required particle asset name |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

How to write it:

```lua
local ok = FWB.Player.Request.NamedPtfxAsset({
    asset = 'core',
    timeout = 5000
})
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestNamedPtfxAsset({
    asset = 'core',
    timeout = 5000
})
```

Example usage:

```lua
FWB.Player.Request.NamedPtfxAsset({
    asset = 'core',
    timeout = 5000
})
```

Notes:

- use this before starting named particle effects

</details>

<details>
<summary><strong>Request Weapon Asset</strong></summary>

Short description: Load a weapon asset before using weapon-based effects or previews.

Arguments:

| Key | Type | Notes |
|---|---|---|
| `weapon` | `string|number` | Required weapon name or hash |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |
| `weaponRequestFlags` | `number` | Default `31` |
| `ammoType` | `number` | Default `0` |

Returns:

- `boolean`

How to write it:

```lua
local ok = FWB.Player.Request.WeaponAsset({
    weapon = 'WEAPON_PISTOL',
    timeout = 5000,
    weaponRequestFlags = 31,
    ammoType = 0
})
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestWeaponAsset({
    weapon = 'WEAPON_PISTOL',
    timeout = 5000,
    weaponRequestFlags = 31,
    ammoType = 0
})
```

Example usage:

```lua
FWB.Player.Request.WeaponAsset({
    weapon = 'WEAPON_PISTOL',
    timeout = 5000,
    weaponRequestFlags = 31,
    ammoType = 0
})
```

Notes:

- useful when your script works with weapon previews, effects, or weapon-specific assets

</details>
