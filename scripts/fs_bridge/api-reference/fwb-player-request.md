# FWB.Player.Request

`FWB.Player.Request` groups the client-side asset request helpers for animation dictionaries, models, animation sets, clip sets, particle assets, and weapon assets.

## Public Calls

```lua
FWB.Player.Request.AnimDict(extras)
FWB.Player.Request.Model(extras)
FWB.Player.Request.AnimSet(extras)
FWB.Player.Request.ClipSet(extras)
FWB.Player.Request.NamedPtfxAsset(extras)
FWB.Player.Request.WeaponAsset(extras)
```

## Common Rules

- all request helpers return `true` on success and `false` on failure
- all helpers support the `extras` table style
- default `timeout` is `10000`
- `silent = true` disables failure prints
- `keepLoaded = false` releases the asset after a successful load

<details>
<summary><strong>Request Anim Dict</strong></summary>

Short description: Load an animation dictionary before playing an animation.

Signature:

```lua
FWB.Player.Request.AnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000,
    silent = false,
    keepLoaded = true
})

exports.fs_bridge:RequestAnimDict(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `dict` | `string` | Required animation dictionary |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

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

Signature:

```lua
FWB.Player.Request.Model({
    model = `adder`,
    timeout = 5000,
    silent = false,
    keepLoaded = true,
    requireValid = true
})

exports.fs_bridge:RequestModel(extras)
```

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

Example usage:

```lua
local ok = FWB.Player.Request.Model({
    model = `adder`,
    timeout = 5000
})

if ok then
    print('Model loaded')
end
```

Notes:

- this helper is also used internally by other runtime helpers that need a loaded model

</details>

<details>
<summary><strong>Request Anim Set Or Clip Set</strong></summary>

Short description: Load movement sets and clip sets before applying them to a ped.

Signature:

```lua
FWB.Player.Request.AnimSet({
    animSet = 'move_m@drunk@slightlydrunk',
    timeout = 5000,
    keepLoaded = true
})

FWB.Player.Request.ClipSet({
    clipSet = 'move_ped_crouched',
    timeout = 5000,
    keepLoaded = true
})

exports.fs_bridge:RequestAnimSet(extras)
exports.fs_bridge:RequestClipSet(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `animSet` | `string` | Required for `AnimSet` |
| `clipSet` | `string` | Required for `ClipSet` |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

Example usage:

```lua
FWB.Player.Request.AnimSet({
    animSet = 'move_m@drunk@slightlydrunk'
})

FWB.Player.Request.ClipSet({
    clipSet = 'move_ped_crouched'
})
```

Notes:

- `AnimSet` and `ClipSet` share the same loading rules and return pattern

</details>

<details>
<summary><strong>Request Named Ptfx Asset</strong></summary>

Short description: Load a named particle asset before using particle effects.

Signature:

```lua
FWB.Player.Request.NamedPtfxAsset({
    asset = 'core',
    timeout = 5000,
    keepLoaded = true
})

exports.fs_bridge:RequestNamedPtfxAsset(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `asset` | `string` | Required particle asset name |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

Example usage:

```lua
FWB.Player.Request.NamedPtfxAsset({
    asset = 'core'
})
```

Notes:

- use this before starting named particle effects

</details>

<details>
<summary><strong>Request Weapon Asset</strong></summary>

Short description: Load a weapon asset before using weapon-based effects or previews.

Signature:

```lua
FWB.Player.Request.WeaponAsset({
    weapon = `WEAPON_PISTOL`,
    timeout = 5000,
    keepLoaded = true,
    weaponRequestFlags = 31,
    ammoType = 0
})

exports.fs_bridge:RequestWeaponAsset(extras)
```

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

Example usage:

```lua
FWB.Player.Request.WeaponAsset({
    weapon = `WEAPON_PISTOL`
})
```

Notes:

- useful when your script works with weapon previews, effects, or weapon-specific assets

</details>
