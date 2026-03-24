# FWB.Banking

Banking overrides are split between client and server responsibilities.

## Public Calls

Client:

```lua
FWB.Banking.OpenBossMenu(job)
FWB.Banking.ResourceName()
```

Server:

```lua
FWB.Banking.AddSocietyMoney(job, money)
FWB.Banking.RemoveSocietyMoney(job, money)
FWB.Banking.GetSocietyMoney(job)
FWB.Banking.RegisterSociety(jobname, joblabel)
FWB.Banking.ResourceName()
```

<details>
<summary><strong>Open Boss Menu</strong></summary>

Short description: Open your custom boss menu from the public banking namespace.

Signature:

```lua
Override.OpenBossMenu(job)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `job` | `string` | Yes | Job name |

Returns:

- optional UI or menu result

Override code:

```lua
function Override.OpenBossMenu(job)
    exports.my_banking:OpenBossMenu(job)
end
```

Example usage:

```lua
FWB.Banking.OpenBossMenu('police')
```

Notes:

- client-side override

</details>

<details>
<summary><strong>Add Or Remove Society Money</strong></summary>

Short description: Route society balance changes through your own banking resource.

Signature:

```lua
Override.AddSocietyMoney(job, money)
Override.RemoveSocietyMoney(job, money)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `job` | `string` | Yes | Society name |
| `money` | `number` | Yes | Amount to add or remove |

Returns:

- `boolean` or resource-specific result

Override code:

```lua
function Override.AddSocietyMoney(job, money)
    return exports.my_banking:AddSocietyMoney(job, money)
end

function Override.RemoveSocietyMoney(job, money)
    return exports.my_banking:RemoveSocietyMoney(job, money)
end
```

Example usage:

```lua
FWB.Banking.AddSocietyMoney('police', 5000)
FWB.Banking.RemoveSocietyMoney('police', 1000)
```

Notes:

- server-side override

</details>

<details>
<summary><strong>Read Society Balance</strong></summary>

Short description: Return the current society money balance.

Signature:

```lua
Override.GetSocietyMoney(job)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `job` | `string` | Yes | Society name |

Returns:

- `number`

Override code:

```lua
function Override.GetSocietyMoney(job)
    return exports.my_banking:GetSocietyMoney(job)
end
```

Example usage:

```lua
local balance = FWB.Banking.GetSocietyMoney('police')
```

Notes:

- server-side override

</details>

<details>
<summary><strong>Report The Active Banking Resource</strong></summary>

Short description: Return the banking resource name used by your custom setup.

Signature:

```lua
Override.GetBankResourceName()
```

Arguments:

- none

Returns:

- `string`

Override code:

```lua
function Override.GetBankResourceName()
    return 'my_banking'
end
```

Example usage:

```lua
print(FWB.Banking.ResourceName())
```

Notes:

- helps status reporting and diagnostics

</details>
