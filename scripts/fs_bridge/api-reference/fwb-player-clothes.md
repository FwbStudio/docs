# FWB.Player.Clothes

`FWB.Player.Clothes` provides current-player clothing shortcuts for reading native skin data, applying native skin data, resetting the saved outfit, and saving the current outfit.

## Public Calls

```lua
FWB.Player.Clothes.GetNative()
FWB.Player.Clothes.SetNative(clothes)
FWB.Player.Clothes.Reset()
FWB.Player.Clothes.Save()
```

<details>
<summary><strong>Get Native Clothes</strong></summary>

Short description: Read the current local player's native clothing state.

Signature:

```lua
FWB.Player.Clothes.GetNative()
exports.fs_bridge:GetPedCurrentNativeSkin()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Clothes.GetNative()` | none | Reads the current local player skin only |

Returns:

- clothes table keyed by component and prop names

Example usage:

```lua
local clothes = FWB.Player.Clothes.GetNative()

if clothes then
    print(clothes.torso_1 and clothes.torso_1.drawable)
end
```

Notes:

- use this client shortcut for the current player only
- for direct ped-oriented calls, use the `FWB.Clothes` namespace

</details>

<details>
<summary><strong>Set Native Clothes</strong></summary>

Short description: Apply a native clothes table to the current local player.

Signature:

```lua
FWB.Player.Clothes.SetNative(clothes)
exports.fs_bridge:SetPedCurrentNativeSkin(clothes)
```

Arguments:

| Name | Type | Notes |
|---|---|---|
| `clothes` | `table` | Native skin table keyed by component and prop names |

Returns:

- framework-specific apply result
- `false` when the provided clothes data is invalid

Example usage:

```lua
FWB.Player.Clothes.SetNative({
    tshirt_1 = { drawable = 15, texture = 0, palette = 0 },
    torso_1 = { drawable = 65, texture = 0, palette = 0 },
    pants_1 = { drawable = 24, texture = 0, palette = 0 }
})
```

Notes:

- this helper targets the local player only
- the clothes table can include component keys such as `torso_1`, `pants_1`, and props such as `helmet_1`

</details>

<details>
<summary><strong>Reset Saved Clothes</strong></summary>

Short description: Reset the local player to the last saved clothing state through the active clothing resource.

Signature:

```lua
FWB.Player.Clothes.Reset()
exports.fs_bridge:ResetPedCurrentScriptSkin()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Clothes.Reset()` | none | Resets the local player only |

Returns:

- compatibility-specific reset result

Example usage:

```lua
FWB.Player.Clothes.Reset()
```

Notes:

- this uses the active clothing integration rather than only natives

</details>

<details>
<summary><strong>Save Current Clothes</strong></summary>

Short description: Save the current local player outfit through the active clothing resource.

Signature:

```lua
FWB.Player.Clothes.Save()
exports.fs_bridge:SavePedCurrentScriptSkin()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Clothes.Save()` | none | Saves the local player only |

Returns:

- compatibility-specific save result

Example usage:

```lua
FWB.Player.Clothes.Save()
```

Notes:

- use this after changing outfit data when your clothing resource supports saving through Bridge

</details>
