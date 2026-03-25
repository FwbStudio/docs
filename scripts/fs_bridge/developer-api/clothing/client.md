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

This page documents the public client-side Clothing API.

It covers local player clothing helpers, full ped native skin helpers, script skin save and reset helpers, and the detected clothing resource name.

## Native Skin Table

Bridge uses the same native clothing table shape for the public clothing helpers below.

| Key | Type | Notes |
|---|---|---|
| `hair_1` | `table` | Hair data with `drawable`, `texture`, `palette`, `color`, and `highlight` |
| `tshirt_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `torso_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `decals_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `pants_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `shoes_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `mask_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `bproof_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `chain_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `arms` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `bags_1` | `table` | Component data with `drawable`, `texture`, and `palette` |
| `helmet_1` | `table` | Prop data with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `glasses_1` | `table` | Prop data with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `ears_1` | `table` | Prop data with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `watches_1` | `table` | Prop data with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `bracelets_1` | `table` | Prop data with `drawable` and `texture`. Use `drawable = -1` to clear it |

## FWB.Player.Clothes

### Local Player Clothing

<details>
<summary><strong>Get Native Skin</strong></summary>

Short description: Read the current local player native clothing table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This local-player helper does not take any arguments |

Returns:

- `table` native clothing table that matches the Native Skin Table above

How to write it as function:

```lua
local clothes = FWB.Player.Clothes.GetNative()
```

How to write it as export:

```lua
local clothes = exports['fs_bridge']:GetPedCurrentNativeSkin()
```

Example as function:

```lua
local clothes = FWB.Player.Clothes.GetNative()
print(clothes)
```

Example as export:

```lua
local clothes = exports['fs_bridge']:GetPedCurrentNativeSkin()
print(clothes)
```

</details>

<details>
<summary><strong>Set Native Skin</strong></summary>

Short description: Apply a native clothing table to the local player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `clothes` | `table` | Native clothing table that matches the Native Skin Table above |
| `clothes.hair_1` | `table` | Optional hair entry with `drawable`, `texture`, `palette`, `color`, and `highlight` |
| `clothes.tshirt_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.torso_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.decals_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.pants_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.shoes_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.mask_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.bproof_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.chain_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.arms` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.bags_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.helmet_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.glasses_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.ears_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.watches_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.bracelets_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |

Returns:

- `nil` after applying the native skin table
- `false` when the passed value is not a valid clothes table

How to write it as function:

```lua
FWB.Player.Clothes.SetNative(clothes)
```

How to write it as export:

```lua
exports['fs_bridge']:SetPedCurrentNativeSkin(clothes)
```

Example as function:

```lua
FWB.Player.Clothes.SetNative({
    torso_1 = { drawable = 15, texture = 0, palette = 0 },
    tshirt_1 = { drawable = 15, texture = 0, palette = 0 },
    pants_1 = { drawable = 14, texture = 0, palette = 0 }
})
```

Example as export:

```lua
exports['fs_bridge']:SetPedCurrentNativeSkin({
    torso_1 = { drawable = 15, texture = 0, palette = 0 },
    tshirt_1 = { drawable = 15, texture = 0, palette = 0 },
    pants_1 = { drawable = 14, texture = 0, palette = 0 }
})
```

</details>

<details>
<summary><strong>Reset Script Skin</strong></summary>

Short description: Reset the local player to the last saved script skin through the active clothing resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This local-player helper does not take any arguments |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Clothes.Reset()
```

How to write it as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
```

Example as function:

```lua
FWB.Player.Clothes.Reset()
```

Example as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
```

</details>

<details>
<summary><strong>Save Script Skin</strong></summary>

Short description: Save the current local player script skin through the active clothing resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This local-player helper does not take any arguments |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Clothes.Save()
```

How to write it as export:

```lua
exports['fs_bridge']:SavePedCurrentScriptSkin()
```

Example as function:

```lua
FWB.Player.Clothes.Save()
```

Example as export:

```lua
exports['fs_bridge']:SavePedCurrentScriptSkin()
```

</details>

## FWB.Clothes

### Ped Native Clothing

<details>
<summary><strong>Get Ped Current Native Skin</strong></summary>

Short description: Read the native clothing table for a specific ped, or for the local player when no ped is passed.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `ped` | `number` | Optional ped entity handle. Leave empty to use the local player ped |

Returns:

- `table` native clothing table that matches the Native Skin Table above

How to write it as function:

```lua
local clothes = FWB.Clothes.GetPedCurrentNativeSkin(ped)
```

How to write it as export:

```lua
local clothes = exports['fs_bridge']:GetPedCurrentNativeSkin(ped)
```

Example as function:

```lua
local localClothes = FWB.Clothes.GetPedCurrentNativeSkin()
local pedClothes = FWB.Clothes.GetPedCurrentNativeSkin(PlayerPedId())
print(localClothes, pedClothes)
```

Example as export:

```lua
local localClothes = exports['fs_bridge']:GetPedCurrentNativeSkin()
local pedClothes = exports['fs_bridge']:GetPedCurrentNativeSkin(PlayerPedId())
print(localClothes, pedClothes)
```

</details>

<details>
<summary><strong>Set Ped Current Native Skin</strong></summary>

Short description: Apply a native clothing table to a specific ped, or pass the clothes table as the first argument to apply it to the local player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `pedOrClothes` | `number|table|nil` | Ped entity handle, or pass the native clothing table here to target the local player |
| `clothes` | `table` | Native clothing table when the first argument is a ped |
| `clothes.hair_1` | `table` | Optional hair entry with `drawable`, `texture`, `palette`, `color`, and `highlight` |
| `clothes.tshirt_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.torso_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.decals_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.pants_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.shoes_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.mask_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.bproof_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.chain_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.arms` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.bags_1` | `table` | Optional component entry with `drawable`, `texture`, and `palette` |
| `clothes.helmet_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.glasses_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.ears_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.watches_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |
| `clothes.bracelets_1` | `table` | Optional prop entry with `drawable` and `texture`. Use `drawable = -1` to clear it |

Returns:

- `nil` after applying the native skin table

How to write it as function:

```lua
FWB.Clothes.SetPedCurrentNativeSkin(pedOrClothes, clothes)
```

How to write it as export:

```lua
exports['fs_bridge']:SetPedCurrentNativeSkin(pedOrClothes, clothes)
```

Example as function:

```lua
FWB.Clothes.SetPedCurrentNativeSkin(PlayerPedId(), {
    mask_1 = { drawable = 5, texture = 0, palette = 0 },
    glasses_1 = { drawable = -1, texture = 0 }
})
```

Example as export:

```lua
exports['fs_bridge']:SetPedCurrentNativeSkin(PlayerPedId(), {
    mask_1 = { drawable = 5, texture = 0, palette = 0 },
    glasses_1 = { drawable = -1, texture = 0 }
})
```

</details>

### Script Skin

<details>
<summary><strong>Reset Ped Current Script Skin</strong></summary>

Short description: Reset the current script skin through the detected clothing resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Clothes.ResetPedCurrentScriptSkin()
```

How to write it as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
```

Example as function:

```lua
FWB.Clothes.ResetPedCurrentScriptSkin()
```

Example as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
```

</details>

<details>
<summary><strong>Save Ped Current Script Skin</strong></summary>

Short description: Save the current script skin through the detected clothing resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Clothes.SavePedCurrentScriptSkin()
```

How to write it as export:

```lua
exports['fs_bridge']:SavePedCurrentScriptSkin()
```

Example as function:

```lua
FWB.Clothes.SavePedCurrentScriptSkin()
```

Example as export:

```lua
exports['fs_bridge']:SavePedCurrentScriptSkin()
```

</details>

### Clothing Resource

<details>
<summary><strong>Clothing Resource Name</strong></summary>

Short description: Get the detected clothing resource name that Bridge is currently using.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `string` resource name
- `nil` when no compatible clothing resource is active

How to write it as function:

```lua
local resourceName = FWB.Clothes.ResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetClothingResourceName()
```

Example as function:

```lua
print(FWB.Clothes.ResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetClothingResourceName())
```

</details>