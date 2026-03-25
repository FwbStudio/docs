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

# Manual Compatibility

This page lists the active override functions currently used by the local Bridge build.

Use these when your setup needs custom compatibility that is not already covered by normal public support.

## ðŸ“ Where Manual Compatibility Code Goes

Client side:

```lua
fs_bridge/unlocked/client.lua
```

Server side:

```lua
fs_bridge/unlocked/server.lua
```

## ðŸ–¥ï¸ Client Overrides

### Player Status

<details>
<summary><strong>Hunger</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Player.Hunger.Add(value)` and `FWB.Player.Hunger.Remove(value)` should call your own status system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your status resource

Override code:

```lua
function Override.AddHunger(value)
    return exports['your_status']:addHunger(value)
end

function Override.RemoveHunger(value)
    return exports['your_status']:removeHunger(value)
end
```

Notes:

- Bridge expects `value` to be numeric
- this override is client-side

</details>

<details>
<summary><strong>Thirst</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Player.Thirst.Add(value)` and `FWB.Player.Thirst.Remove(value)` should call your own status system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your status resource

Override code:

```lua
function Override.AddThirst(value)
    return exports['your_status']:addThirst(value)
end

function Override.RemoveThirst(value)
    return exports['your_status']:removeThirst(value)
end
```

Notes:

- Bridge expects `value` to be numeric
- this override is client-side

</details>

<details>
<summary><strong>Stress</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Player.Stress.Add(value)` and `FWB.Player.Stress.Remove(value)` should call your own stress system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your stress resource

Override code:

```lua
function Override.AddStress(value)
    return exports['your_status']:addStress(value)
end

function Override.RemoveStress(value)
    return exports['your_status']:removeStress(value)
end
```

Notes:

- Bridge expects `value` to be numeric
- this override is client-side

</details>

<details>
<summary><strong>Health</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Player.Health.Add(value)` and `FWB.Player.Health.Remove(value)` should use your own health logic.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your health logic

Override code:

```lua
function Override.AddHealth(value)
    local ped = PlayerPedId()
    SetEntityHealth(ped, GetEntityHealth(ped) + value)
end

function Override.RemoveHealth(value)
    local ped = PlayerPedId()
    SetEntityHealth(ped, GetEntityHealth(ped) - value)
end
```

Notes:

- this override is client-side
- clamp values if your server needs stricter health limits

</details>

<details>
<summary><strong>Armour</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Player.Armour.Add(value)` and `FWB.Player.Armour.Remove(value)` should use your own armour logic.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `value` | `number` | Yes | Amount to add or remove |

Returns:

- optional result from your armour logic

Override code:

```lua
function Override.AddArmour(value)
    local ped = PlayerPedId()
    SetPedArmour(ped, GetPedArmour(ped) + value)
end

function Override.RemoveArmour(value)
    local ped = PlayerPedId()
    SetPedArmour(ped, math.max(0, GetPedArmour(ped) - value))
end
```

Notes:

- this override is client-side
- clamp values if your armour system has its own limits

</details>

### Banking

<details>
<summary><strong>OpenBossMenu</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Banking.OpenBossMenu(job)` should open your own banking or society menu.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `job` | `string` | Yes | Job name for the boss menu |

Returns:

- optional result from your banking resource

Override code:

```lua
function Override.OpenBossMenu(job)
    return exports['your_banking']:openBossMenu(job)
end
```

Notes:

- use the exact export or event name from your banking resource
- this override is client-side

</details>

<details>
<summary><strong>GetBankResourceName (Client)</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when Bridge should report your custom banking resource name on the client side.

Arguments:

- none

Returns:

- `string` resource name
- `nil` if you do not want to report one

Override code:

```lua
function Override.GetBankResourceName()
    return 'your_banking'
end
```

Notes:

- return the exact started resource folder name
- if you also need this on the server side, define the same function in `fs_bridge/unlocked/server.lua`

</details>

### Clothing

<details>
<summary><strong>ResetPedCurrentScriptSkin</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Clothes.ResetPedCurrentScriptSkin()` should reset the player back to the last saved outfit from your clothing system.

Arguments:

- none

Returns:

- optional result from your clothing resource

Override code:

```lua
function Override.ResetPedCurrentScriptSkin()
    TriggerEvent('your_clothing:resetSkin')
end
```

Notes:

- this override is client-side
- replace the example event with your real clothing reset event or export

</details>

<details>
<summary><strong>SavePedCurrentScriptSkin</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Clothes.SavePedCurrentScriptSkin()` should save the current outfit through your clothing system.

Arguments:

- none

Returns:

- optional result from your clothing resource

Override code:

```lua
function Override.SavePedCurrentScriptSkin()
    TriggerServerEvent('your_clothing:saveSkin')
end
```

Notes:

- this override is client-side
- replace the example event with your real clothing save flow

</details>

<details>
<summary><strong>GetClothingResourceName</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when Bridge should report your custom clothing resource name.

Arguments:

- none

Returns:

- `string` resource name
- `nil` if you do not want to report one

Override code:

```lua
function Override.GetClothingResourceName()
    return 'your_clothing'
end
```

Notes:

- return the exact started resource folder name
- this override is client-side

</details>

### Inventory

<details>
<summary><strong>OpenStash</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.OpenStash(argument)` should open a stash in your own inventory system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `argument.name` | `string` | Yes | Unique stash name |
| `argument.label` | `string` | Yes | Stash label shown in UI |
| `argument.slots` | `number` | Yes | Slot count |
| `argument.weight` | `number` | Yes | Max weight |
| `argument.coords` | `vector3` | No | Stash location |
| `argument.jobs` | `table` | No | Job access rules |
| `argument.identifier` | `string` | No | Owner-linked identifier |

Returns:

- optional result from your inventory resource

Override code:

```lua
function Override.OpenStash(argument)
    return exports['your_inventory']:openStash({
        name = argument.name,
        label = argument.label,
        slots = argument.slots,
        weight = argument.weight,
        coords = argument.coords,
        jobs = argument.jobs,
        identifier = argument.identifier,
    })
end
```

Notes:

- this override is client-side
- keep your security checks around `coords`, `jobs`, or `identifier`

</details>

<details>
<summary><strong>OpenShop</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.OpenShop(argument)` should open a shop in your own inventory system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `argument.name` | `string` | Yes | Unique shop name |
| `argument.label` | `string` | Yes | Shop label shown in UI |
| `argument.items` | `table` | Yes | Shop item list |

Returns:

- optional result from your inventory resource

Override code:

```lua
function Override.OpenShop(argument)
    return exports['your_inventory']:openShop({
        name = argument.name,
        label = argument.label,
        items = argument.items,
    })
end
```

Notes:

- this override is client-side
- the current Bridge source marks this path as one you should test carefully with your inventory

</details>

### Phone

<details>
<summary><strong>GetPhoneResourceName (Client)</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when Bridge should report your custom phone resource name on the client side.

Arguments:

- none

Returns:

- `string` resource name
- `nil` if you do not want to report one

Override code:

```lua
function Override.GetPhoneResourceName()
    return 'your_phone'
end
```

Notes:

- return the exact started resource folder name
- if you also need this on the server side, define the same function in `fs_bridge/unlocked/server.lua`

</details>

### Interface

<details>
<summary><strong>Notification</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.Notify(argument)` should display notifications through your own UI resource.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `argument.description` | `string` | Yes | Main notification text |
| `argument.title` | `string` | No | Notification title |
| `argument.type` | `string` | No | Example: `inform`, `success`, `warning`, `error` |
| `argument.position` | `string` | No | Bridge defaults this to `top` |
| `argument.duration` | `number` | No | Bridge defaults this to `5000` |

Returns:

- optional result from your notification resource

Override code:

```lua
function Override.Notification(argument)
    return exports['your_notify']:notify({
        title = argument.title,
        description = argument.description,
        type = argument.type,
        position = argument.position,
        duration = argument.duration,
    })
end
```

Notes:

- this override is client-side
- Bridge already normalizes string notifications into a table before calling this override

</details>

<details>
<summary><strong>TextUi</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.TextUi.Show(text, options)` and `FWB.TextUi.Hide()` should use your own text UI resource.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `text` | `string` | No | Text to show; may be `nil` when hiding |
| `options.type` | `string` | No | Example: `inform`, `success`, `warning`, `error` |
| `options.icon` | `string` | No | Font Awesome icon |
| `options.iconColor` | `string` | No | Hex color |
| `options.position` | `string` | No | Example: `right-center`, `left-center`, `top-center`, `bottom-center` |
| `options.iconAnimation` | `string` | No | Example: `spin`, `pulse`, `bounce`, `shake` |

Returns:

- optional result from your text UI resource

Override code:

```lua
function Override.TextUi(text, options)
    if not text then
        return exports['your_textui']:hideTextUi()
    end

    return exports['your_textui']:showTextUi(text, options or {})
end
```

Notes:

- this override is client-side
- use one function for both show and hide behavior

</details>

<details>
<summary><strong>SetClipBoard</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/client.lua`.
Use it when `FWB.SetClipBoard(string)` should copy text through your own clipboard helper.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `string` | `string` | Yes | Text to copy |

Returns:

- optional result from your clipboard resource

Override code:

```lua
function Override.SetClipBoard(string)
    return exports['your_clipboard']:setClipboard(string)
end
```

Notes:

- this override is client-side
- Bridge only calls this when a string is provided

</details>

## ðŸ› ï¸ Server Overrides

### Banking

<details>
<summary><strong>AddSocietyMoney</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Banking.AddSocietyMoney(job, money)` should add money through your own society banking system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `job` | `string` | Yes | Society or job name |
| `money` | `number` | Yes | Amount to add |

Returns:

- `boolean` success result
- optional custom result from your banking resource

Override code:

```lua
function Override.AddSocietyMoney(job, money)
    return exports['your_banking']:addSocietyMoney(job, money)
end
```

Notes:

- this override is server-side
- keep your own validation around negative values if needed

</details>

<details>
<summary><strong>RemoveSocietyMoney</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Banking.RemoveSocietyMoney(job, money)` should remove money through your own society banking system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `job` | `string` | Yes | Society or job name |
| `money` | `number` | Yes | Amount to remove |

Returns:

- `boolean` success result
- optional custom result from your banking resource

Override code:

```lua
function Override.RemoveSocietyMoney(job, money)
    return exports['your_banking']:removeSocietyMoney(job, money)
end
```

Notes:

- this override is server-side
- make sure your banking system handles missing accounts safely

</details>

<details>
<summary><strong>GetSocietyMoney</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Banking.GetSocietyMoney(job)` should read balance through your own society banking system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `job` | `string` | Yes | Society or job name |

Returns:

- `number` balance
- `false` or `nil` if the account cannot be read

Override code:

```lua
function Override.GetSocietyMoney(job)
    return exports['your_banking']:getSocietyMoney(job)
end
```

Notes:

- this override is server-side
- return a number when possible so dependent scripts can compare balances safely

</details>

<details>
<summary><strong>GetBankResourceName (Server)</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when Bridge should report your custom banking resource name on the server side.

Arguments:

- none

Returns:

- `string` resource name
- `nil` if you do not want to report one

Override code:

```lua
function Override.GetBankResourceName()
    return 'your_banking'
end
```

Notes:

- return the exact started resource folder name
- if you also need this on the client side, define the same function in `fs_bridge/unlocked/client.lua`

</details>

### Dispatch

<details>
<summary><strong>AddCustomDispatch</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.AddCustomDispatch(argument)` should send alerts through your own dispatch resource.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `argument.Job` | `table` | Yes | Target jobs, for example `{ 'police', 'sheriff' }` |
| `argument.Location` | `vector3` | Yes | Dispatch location |
| `argument.CallCode.Code` | `string` | No | Dispatch call code |
| `argument.CallCode.Title` | `string` | No | Dispatch title |
| `argument.Message` | `string` | Yes | Main dispatch message |
| `argument.Flashes` | `boolean` | No | Flash state |
| `argument.Image` | `string` | No | Screenshot or image URL |
| `argument.icon` | `string` | No | Dispatch icon |
| `argument.Blip` | `table` | No | Blip settings such as sprite, scale, colour, text, time, and radius |

Returns:

- optional result from your dispatch resource

Override code:

```lua
function Override.AddCustomDispatch(argument)
    return exports['your_dispatch']:sendAlert({
        jobs = argument.Job,
        coords = argument.Location,
        code = argument.CallCode,
        message = argument.Message,
        flashes = argument.Flashes,
        image = argument.Image,
        icon = argument.icon,
        blip = argument.Blip,
    })
end
```

Notes:

- this override is server-side
- match the argument mapping to the exact alert format your dispatch expects

</details>

<details>
<summary><strong>GetDispatchResourceName</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when Bridge should report your custom dispatch resource name.

Arguments:

- none

Returns:

- `string` resource name
- `nil` if you do not want to report one

Override code:

```lua
function Override.GetDispatchResourceName()
    return 'your_dispatch'
end
```

Notes:

- return the exact started resource folder name
- this override is server-side

</details>

### Phone

<details>
<summary><strong>SendEmail</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.SendEmail(source, emaildata)` should send mail through your own phone resource.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` or `string` | Yes | Player source or identifier |
| `emaildata.sender` | `string` | Yes | Sender name |
| `emaildata.subject` | `string` | Yes | Email subject |
| `emaildata.message` | `string` | Yes | Email message |
| `emaildata.imageurl` | `string` | No | Optional image URL |

Returns:

- optional result from your phone resource

Override code:

```lua
function Override.SendEmail(source, emaildata)
    return exports['your_phone']:sendEmail(source, {
        sender = emaildata.sender,
        subject = emaildata.subject,
        message = emaildata.message,
        imageurl = emaildata.imageurl,
    })
end
```

Notes:

- this override is server-side
- map `source` the way your phone resource expects it

</details>

<details>
<summary><strong>GetPhoneResourceName (Server)</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when Bridge should report your custom phone resource name on the server side.

Arguments:

- none

Returns:

- `string` resource name
- `nil` if you do not want to report one

Override code:

```lua
function Override.GetPhoneResourceName()
    return 'your_phone'
end
```

Notes:

- return the exact started resource folder name
- if you also need this on the client side, define the same function in `fs_bridge/unlocked/client.lua`

</details>

### Sounds

<details>
<summary><strong>PlayUrlPos</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.PlayUrlPos(source, position, distance, url, volume, loop)` should play positional audio through your own sound resource.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Yes | Target player source, or `-1` for broadcast if your sound system supports it |
| `soundId` | `string` | Yes | Generated Bridge sound id |
| `position` | `vector3` | Yes | Sound location |
| `distance` | `number` | Yes | Max hearing distance |
| `url` | `string` | Yes | Audio URL |
| `volume` | `number` | Yes | Sound volume |
| `loop` | `boolean` | No | Loop state |

Returns:

- optional result from your sound resource

Override code:

```lua
function Override.PlayUrlPos(source, soundId, position, distance, url, volume, loop)
    return exports['your_sound']:playUrlPos(source, soundId, position, distance, url, volume, loop)
end
```

Notes:

- this override is server-side
- Bridge will still return the generated `soundId` to the caller after this override runs

</details>

<details>
<summary><strong>DestroySound</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Destroy(source, soundId)` should stop sound playback through your own sound resource.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Yes | Target player source, or `-1` if your sound system supports it |
| `soundId` | `string` | Yes | Bridge sound id |

Returns:

- optional result from your sound resource

Override code:

```lua
function Override.DestroySound(source, soundId)
    return exports['your_sound']:destroySound(source, soundId)
end
```

Notes:

- this override is server-side
- use the same sound id created during `Override.PlayUrlPos`

</details>

<details>
<summary><strong>GetSoundResourceName</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when Bridge should report your custom sound resource name.

Arguments:

- none

Returns:

- `string` resource name
- `nil` if you do not want to report one

Override code:

```lua
function Override.GetSoundResourceName()
    return 'your_sound'
end
```

Notes:

- return the exact started resource folder name
- this override is server-side

</details>

### Vehicle

<details>
<summary><strong>GenerateVehiclePlate</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Vehicle.Plate.Generate()` should use your own custom plate generator.

Arguments:

- none

Returns:

- `string` generated vehicle plate

Override code:

```lua
function Override.GenerateVehiclePlate()
    return ('ABC %04d'):format(math.random(0, 9999))
end
```

Notes:

- this override is server-side
- keep the result compatible with your server plate format and database rules

</details>

### Security

<details>
<summary><strong>BanPlayer</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Hacker.Ban(source, reason)` should ban through your own anticheat or admin system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Yes | Player source |
| `reason` | `string` | No | Ban reason |

Returns:

- `boolean` success result
- optional custom result from your ban system

Override code:

```lua
function Override.BanPlayer(source, reason)
    return exports['your_anticheat']:banPlayer(source, reason)
end
```

Notes:

- this override is server-side
- Bridge uses a default reason if one is not provided

</details>

<details>
<summary><strong>Kick</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Hacker.Kick(source, reason)` should kick through your own admin system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Yes | Player source |
| `reason` | `string` | No | Kick reason |

Returns:

- optional result from your kick flow

Override code:

```lua
function Override.Kick(source, reason)
    DropPlayer(source, reason or 'You have been Kicked from the server.')
end
```

Notes:

- this override is server-side
- Bridge uses a default reason if one is not provided

</details>

### Logging

<details>
<summary><strong>CreateLog</strong></summary>

Description:

Copy this code into `fs_bridge/unlocked/server.lua`.
Use it when `FWB.Log.Create(source, event, message, ...)` should also send logs to your own logging system.

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` or `string` | Yes | Player source or invoking resource name |
| `event` | `string` | Yes | Log event name |
| `message` | `string` | Yes | Log message |
| `...` | `any` | No | Extra values forwarded by Bridge |

Returns:

- no return is required

Override code:

```lua
function Override.CreateLog(source, event, message, ...)
    local extra = { ... }

    return exports['your_logger']:createLog({
        source = source,
        event = event,
        message = message,
        extra = extra,
    })
end
```

Notes:

- this override is server-side
- Bridge can still run its own built-in logger after this override

</details>
