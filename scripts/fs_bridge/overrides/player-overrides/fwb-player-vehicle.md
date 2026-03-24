# FWB.Player.Vehicle

This page covers player-facing vehicle key helpers.

Fuel helpers are documented separately on [FWB.Vehicle.Fuel](../integration-overrides/fwb-vehicle-fuel.md).

## Public Calls

Client:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)
FWB.Vehicle.Keys.ResourceName()
```

Server:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
FWB.Vehicle.Keys.ResourceName()
```

<details>
<summary><strong>Give Vehicle Keys</strong></summary>

Short description: Give keys to the player through a custom or unsupported key system.

Signature:

```lua
Override.GiveCarKeyPlayer(vehicle)
Override.GiveCarKeyPlayer(source, vehicle)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Server only | Player source |
| `vehicle` | `number` | Yes | Vehicle entity or supported vehicle reference |

Returns:

- optional response from your key system

Override code:

```lua
function Override.GiveCarKeyPlayer(source, vehicle)
    local playerSource = source or cache.serverId
    exports.my_vehiclekeys:GiveKeys(playerSource, vehicle)
end
```

Example usage:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
```

Notes:

- use the client or server signature that matches where you paste the override
- if your key system already has built-in support, you do not need this override

</details>

<details>
<summary><strong>Remove Vehicle Keys</strong></summary>

Short description: Remove keys from the player through a custom key system.

Signature:

```lua
Override.RemoveCarKeyPlayer(vehicle)
Override.RemoveCarKeyPlayer(source, vehicle)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Server only | Player source |
| `vehicle` | `number` | Yes | Vehicle entity or supported vehicle reference |

Returns:

- optional response from your key system

Override code:

```lua
function Override.RemoveCarKeyPlayer(source, vehicle)
    local playerSource = source or cache.serverId
    exports.my_vehiclekeys:RemoveKeys(playerSource, vehicle)
end
```

Example usage:

```lua
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
```

Notes:

- keep the same vehicle format your key resource expects

</details>

<details>
<summary><strong>Report The Active Keys Resource</strong></summary>

Short description: Return the key resource name used by your custom integration.

Signature:

```lua
Override.GetVehicleKeysResourceName()
```

Arguments:

- none

Returns:

- `string`

Override code:

```lua
function Override.GetVehicleKeysResourceName()
    return 'my_vehiclekeys'
end
```

Example usage:

```lua
print(FWB.Vehicle.Keys.ResourceName())
```

Notes:

- this helps bridge diagnostics and resource status reporting

</details>
