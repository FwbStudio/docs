# FWB.Dispatch

The current dispatch entry point is the public alert helper:

```lua
FWB.AddCustomDispatch(argument)
FWB.GetDispatchResourceName()
```

## Dispatch Payload Shape

```lua
{
    Job = { 'police', 'sheriff' },
    Location = vector3(0.0, 0.0, 0.0),
    CallCode = { Code = '10-10', Title = 'Vehicle Pursuit' },
    Message = 'Message text',
    Flashes = true,
    Image = 'https://cdn.example.com/image.png',
    icon = 'fas fa-car',
    Blip = {
        Sprite = 488,
        Scale = 1.5,
        Colour = 1,
        Flashes = true,
        Text = 'High-Speed Pursuit',
        Time = 60000,
        radius = 0
    }
}
```

<details>
<summary><strong>Send A Custom Dispatch Alert</strong></summary>

Short description: Route bridge alerts through a custom dispatch system.

Signature:

```lua
Override.AddCustomDispatch(argument)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `argument` | `table` | Yes | Dispatch payload |

Returns:

- optional result from your dispatch resource

Override code:

```lua
function Override.AddCustomDispatch(argument)
    exports.my_dispatch:SendDispatch(argument)
end
```

Example usage:

```lua
FWB.AddCustomDispatch({
    Job = { 'police' },
    Location = GetEntityCoords(GetPlayerPed(source)),
    CallCode = { Code = '10-90', Title = 'Robbery' },
    Message = 'Store robbery in progress'
})
```

Notes:

- server-side override
- keep your payload keys stable for your dispatch resource

</details>

<details>
<summary><strong>Report The Active Dispatch Resource</strong></summary>

Short description: Return the dispatch resource name used by your server.

Signature:

```lua
Override.GetDispatchResourceName()
```

Arguments:

- none

Returns:

- `string`

Override code:

```lua
function Override.GetDispatchResourceName()
    return 'my_dispatch'
end
```

Example usage:

```lua
print(FWB.GetDispatchResourceName())
```

Notes:

- used for status and compatibility reporting

</details>
