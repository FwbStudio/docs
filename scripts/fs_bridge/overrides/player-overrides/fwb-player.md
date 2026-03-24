# FWB.Player

This page covers the player status hooks that most commonly need custom overrides.

Paste these into `unlocked/client.lua`.

## Public Calls

```lua
FWB.Player.Hunger.Add(value)
FWB.Player.Hunger.Remove(value)
FWB.Player.Thirst.Add(value)
FWB.Player.Thirst.Remove(value)
FWB.Player.Stress.Add(value)
FWB.Player.Stress.Remove(value)
FWB.Player.Health.Add(value)
FWB.Player.Health.Remove(value)
FWB.Player.Armour.Add(value)
FWB.Player.Armour.Remove(value)
```

<details>
<summary><strong>Hunger</strong></summary>

Short description: Adds or removes hunger through your own status system.

Signature:

```lua
Override.AddHunger(value)
Override.RemoveHunger(value)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your own status system

Override code:

```lua
function Override.AddHunger(value)
    TriggerEvent('my_status:add', 'hunger', value)
end

function Override.RemoveHunger(value)
    TriggerEvent('my_status:remove', 'hunger', value)
end
```

Example usage:

```lua
FWB.Player.Hunger.Add(10)
FWB.Player.Hunger.Remove(5)
```

Notes:

- this is client-side
- `value` should be numeric

</details>

<details>
<summary><strong>Thirst</strong></summary>

Short description: Adds or removes thirst through your own status system.

Signature:

```lua
Override.AddThirst(value)
Override.RemoveThirst(value)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your own status system

Override code:

```lua
function Override.AddThirst(value)
    TriggerEvent('my_status:add', 'thirst', value)
end

function Override.RemoveThirst(value)
    TriggerEvent('my_status:remove', 'thirst', value)
end
```

Example usage:

```lua
FWB.Player.Thirst.Add(10)
FWB.Player.Thirst.Remove(5)
```

Notes:

- this is client-side
- use your real status event names here

</details>

<details>
<summary><strong>Stress</strong></summary>

Short description: Adds or removes stress in a custom stress system.

Signature:

```lua
Override.AddStress(value)
Override.RemoveStress(value)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your own stress system

Override code:

```lua
function Override.AddStress(value)
    exports.my_stress:AddStress(value)
end

function Override.RemoveStress(value)
    exports.my_stress:RemoveStress(value)
end
```

Example usage:

```lua
FWB.Player.Stress.Add(15)
FWB.Player.Stress.Remove(10)
```

Notes:

- only add this when the built-in integration is not enough

</details>

<details>
<summary><strong>Health</strong></summary>

Short description: Adds or removes player health with custom logic.

Signature:

```lua
Override.AddHealth(value)
Override.RemoveHealth(value)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Health amount |

Returns:

- optional result from your own health logic

Override code:

```lua
function Override.AddHealth(value)
    SetEntityHealth(PlayerPedId(), GetEntityHealth(PlayerPedId()) + value)
end

function Override.RemoveHealth(value)
    SetEntityHealth(PlayerPedId(), GetEntityHealth(PlayerPedId()) - value)
end
```

Example usage:

```lua
FWB.Player.Health.Add(25)
FWB.Player.Health.Remove(10)
```

Notes:

- clamp values in your own implementation if needed

</details>

<details>
<summary><strong>Armour</strong></summary>

Short description: Adds or removes player armour with custom logic.

Signature:

```lua
Override.AddArmour(value)
Override.RemoveArmour(value)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Armour amount |

Returns:

- optional result from your own armour logic

Override code:

```lua
function Override.AddArmour(value)
    SetPedArmour(PlayerPedId(), GetPedArmour(PlayerPedId()) + value)
end

function Override.RemoveArmour(value)
    SetPedArmour(PlayerPedId(), GetPedArmour(PlayerPedId()) - value)
end
```

Example usage:

```lua
FWB.Player.Armour.Add(25)
FWB.Player.Armour.Remove(10)
```

Notes:

- keep your own max-armour safeguards if your server uses them

</details>
