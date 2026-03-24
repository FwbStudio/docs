# FWB.Vehicle.Fuel

Fuel helpers are resolved through the active fuel integration or your override.

## Public Calls

```lua
FWB.Vehicle.Fuel.Set(vehicle, value)
FWB.Vehicle.Fuel.Get(vehicle)
FWB.Vehicle.Fuel.ResourceName()
```

<details>
<summary><strong>Set Fuel</strong></summary>

Short description: Apply a fuel value through a custom fuel system.

Signature:

```lua
Override.SetFuel(vehicle, value)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `vehicle` | `number` | Yes | Vehicle entity |
| `value` | `number` | No | Fuel level, defaults to `100.0` when omitted by the caller |

Returns:

- optional result from your fuel resource

Override code:

```lua
function Override.SetFuel(vehicle, value)
    exports.my_fuel:SetFuel(vehicle, value)
end
```

Example usage:

```lua
FWB.Vehicle.Fuel.Set(vehicle, 85.0)
```

Notes:

- usually client-side because the bridge fuel helper lives on the client

</details>

<details>
<summary><strong>Get Fuel</strong></summary>

Short description: Read the current fuel level from a custom fuel system.

Signature:

```lua
Override.GetFuel(vehicle)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `vehicle` | `number` | Yes | Vehicle entity |

Returns:

- `number`

Override code:

```lua
function Override.GetFuel(vehicle)
    return exports.my_fuel:GetFuel(vehicle)
end
```

Example usage:

```lua
local fuel = FWB.Vehicle.Fuel.Get(vehicle)
```

Notes:

- return a number the rest of your scripts can trust

</details>

<details>
<summary><strong>Report The Active Fuel Resource</strong></summary>

Short description: Return the fuel resource name used by your setup.

Signature:

```lua
Override.GetFuelResourceName()
```

Arguments:

- none

Returns:

- `string`

Override code:

```lua
function Override.GetFuelResourceName()
    return 'my_fuel'
end
```

Example usage:

```lua
print(FWB.Vehicle.Fuel.ResourceName())
```

Notes:

- useful for debug output

</details>
