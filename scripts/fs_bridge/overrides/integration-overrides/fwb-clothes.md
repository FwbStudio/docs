# FWB.Clothes

The clothes namespace mixes built-in native helpers with optional resource integration hooks.

## Public Calls

```lua
FWB.Clothes.GetPedCurrentNativeSkin(ped)
FWB.Clothes.SetPedCurrentNativeSkin(ped, clothes)
FWB.Clothes.ResetPedCurrentScriptSkin()
FWB.Clothes.SavePedCurrentScriptSkin()
FWB.Clothes.ResourceName()

FWB.Player.Clothes.GetNative()
FWB.Player.Clothes.SetNative(clothes)
FWB.Player.Clothes.Reset()
FWB.Player.Clothes.Save()
```

<details>
<summary><strong>Reset Script Skin</strong></summary>

Short description: Reset the player to their saved appearance in a custom clothes resource.

Signature:

```lua
Override.ResetPedCurrentScriptSkin()
```

Arguments:

- none

Returns:

- optional result from your clothes resource

Override code:

```lua
function Override.ResetPedCurrentScriptSkin()
    exports.my_clothes:ResetSkin()
end
```

Example usage:

```lua
FWB.Player.Clothes.Reset()
```

Notes:

- client-side override

</details>

<details>
<summary><strong>Save Script Skin</strong></summary>

Short description: Save the player's current appearance to your clothes resource.

Signature:

```lua
Override.SavePedCurrentScriptSkin()
```

Arguments:

- none

Returns:

- optional save result

Override code:

```lua
function Override.SavePedCurrentScriptSkin()
    exports.my_clothes:SaveSkin()
end
```

Example usage:

```lua
FWB.Player.Clothes.Save()
```

Notes:

- client-side override

</details>

<details>
<summary><strong>Report The Active Clothing Resource</strong></summary>

Short description: Return the clothes or appearance resource name used by your setup.

Signature:

```lua
Override.GetClothingResourceName()
```

Arguments:

- none

Returns:

- `string`

Override code:

```lua
function Override.GetClothingResourceName()
    return 'my_clothes'
end
```

Example usage:

```lua
print(FWB.Clothes.ResourceName())
```

Notes:

- the native get/set skin helpers already work without this override

</details>
