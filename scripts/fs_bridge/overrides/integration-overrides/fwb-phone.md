# FWB.Phone

The current phone-facing bridge helpers are:

```lua
FWB.SendEmail(source, emaildata)
FWB.GetPhoneResourceName()
```

<details>
<summary><strong>Send Email</strong></summary>

Short description: Send mail through a custom phone resource.

Signature:

```lua
Override.SendEmail(source, emaildata)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` or `string` | Yes | Player source or identifier, depending on your phone system |
| `emaildata` | `table` | Yes | Email payload |

Email payload:

| Key | Type | Notes |
|---|---|---|
| `sender` | `string` | Sender display name |
| `subject` | `string` | Email subject |
| `message` | `string` | Email body |
| `imageurl` | `string` | Optional image |

Returns:

- optional result from your phone resource

Override code:

```lua
function Override.SendEmail(source, emaildata)
    return exports.my_phone:SendEmail(source, emaildata)
end
```

Example usage:

```lua
FWB.SendEmail(source, {
    sender = 'Dispatch',
    subject = 'New Alert',
    message = 'Check your MDT for details'
})
```

Notes:

- server-side override

</details>

<details>
<summary><strong>Report The Active Phone Resource</strong></summary>

Short description: Return the phone resource name used by your setup.

Signature:

```lua
Override.GetPhoneResourceName()
```

Arguments:

- none

Returns:

- `string`

Override code:

```lua
function Override.GetPhoneResourceName()
    return 'my_phone'
end
```

Example usage:

```lua
print(FWB.GetPhoneResourceName())
```

Notes:

- useful for diagnostics

</details>
