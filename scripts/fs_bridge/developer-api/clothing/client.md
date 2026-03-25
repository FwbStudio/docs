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

It includes native clothing reads and writes, script skin save and reset helpers, and the detected clothing resource name.
## FWB.Player.Clothes
<details>
<summary><strong>Clothes.GetNative() / Clothes.SetNative(clothes)</strong></summary>

Short description: Read or apply the local player native clothing table through Bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `clothes` | `table` | Clothing table that matches the Bridge native skin shape for `SetNative` |

Returns:

- `table` clothing table for `GetNative`
- nothing or `false` for `SetNative`

How to write it as function:

```lua
local clothes = FWB.Player.Clothes.GetNative()
FWB.Player.Clothes.SetNative(clothes)
```

How to write it as export:

```lua
local clothes = exports['fs_bridge']:GetPedCurrentNativeSkin()
exports['fs_bridge']:SetPedCurrentNativeSkin(clothes)
```

Example as function:

```lua
local clothes = FWB.Player.Clothes.GetNative()
FWB.Player.Clothes.SetNative({
    torso_1 = { drawable = 15, texture = 0, palette = 0 }
})
```

Example as export:

```lua
local clothes = exports['fs_bridge']:GetPedCurrentNativeSkin()
exports['fs_bridge']:SetPedCurrentNativeSkin(clothes)
```

Notes:

- The direct export also accepts an explicit ped argument when you need it.

</details>

<details>
<summary><strong>Clothes.Reset() / Clothes.Save()</strong></summary>

Short description: Reset the current script skin or save the current script skin through the active clothing resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- resource-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Clothes.Reset()
FWB.Player.Clothes.Save()
```

How to write it as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
exports['fs_bridge']:SavePedCurrentScriptSkin()
```

Example as function:

```lua
FWB.Player.Clothes.Reset()
FWB.Player.Clothes.Save()
```

Example as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
exports['fs_bridge']:SavePedCurrentScriptSkin()
```

</details>


## FWB.Clothes

<details>
<summary><strong>ResourceName()</strong></summary>

Short description: Get the detected clothing resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` resource name
- `nil` when nothing is active

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
