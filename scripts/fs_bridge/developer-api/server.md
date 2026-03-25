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

# Server API

This page documents the current public server-side Bridge API from the live `fs_bridge` build.

Function-style examples assume you first get the Bridge object:

```lua
local FWB = exports['fs_bridge']:GetObject()
```

Deprecated globals and internal helper paths are intentionally skipped here. This page focuses on the current public namespaces, public root helpers, and direct exports that are available in the live server runtime.

## Access

<details>
<summary><strong>GetObject()</strong></summary>

Short description: Get the shared Bridge object so you can call namespaced server helpers like `FWB.Player`, `FWB.Vehicle`, `FWB.Banking`, and more.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` Bridge object

How to write it as export:

```lua
local FWB = exports['fs_bridge']:GetObject()
```

Example as export:

```lua
local FWB = exports['fs_bridge']:GetObject()
print(FWB.Job.All())
```

</details>

<details>
<summary><strong>Cache(key) / Cache(resource, key)</strong></summary>

Short description: Read Bridge cache values for the invoking resource, or read a specific resource bucket when you pass both `resource` and `key`.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `key` | `string` | Read the invoking resource bucket when this is the only argument |
| `resource` | `string` | Optional explicit resource bucket name |
| `key` | `string` | Optional second argument when you want a specific bucket and key |

Returns:

- cached value for the requested key
- `nil` when nothing is stored

How to write it as export:

```lua
local cacheReady = exports['fs_bridge']:Cache('CacheReady')
local customValue = exports['fs_bridge']:Cache('my_resource', 'my_key')
```

Example as export:

```lua
local cacheReady = exports['fs_bridge']:Cache('CacheReady')
local isServerSide = exports['fs_bridge']:Cache('IsServerSide')
```

Notes:

- Common server protected keys include `IsServerSide`, `Resource`, and `CacheReady`.

</details>

## FWB.CB

<details>
<summary><strong>Await(eventName, player, ...)</strong></summary>

Short description: Trigger a registered client callback on a target player and wait for the return values on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Registered callback name |
| `player` | `number` | Target player source |
| `...` | `any` | Optional payload passed through to the callback |

Returns:

- one or more callback return values
- `nil` when the callback returns nothing

How to write it as function:

```lua
local result = FWB.CB.Await(eventName, player, ...)
```

How to write it as export:

```lua
local result = exports['fs_bridge']:AwaitCallback(eventName, player, ...)
```

Example as function:

```lua
local canOpen = FWB.CB.Await('garage:clientCanOpen', source, 'ABC123')
```

Example as export:

```lua
local canOpen = exports['fs_bridge']:AwaitCallback('garage:clientCanOpen', source, 'ABC123')
```

</details>

<details>
<summary><strong>Register(eventName, callback)</strong></summary>

Short description: Register a server callback that can be triggered from client code through Bridge callback routing.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Callback name to register |
| `callback` | `function` | Lua function that receives `source` first and may return one or more values |

Returns:

- nothing

How to write it as function:

```lua
FWB.CB.Register(eventName, callback)
```

How to write it as export:

```lua
exports['fs_bridge']:RegisterCallback(eventName, callback)
```

Example as function:

```lua
FWB.CB.Register('garage:getLabel', function(playerSource, plate)
    return ('Garage lookup for %s'):format(plate)
end)
```

Example as export:

```lua
exports['fs_bridge']:RegisterCallback('garage:getLabel', function(playerSource, plate)
    return ('Garage lookup for %s'):format(plate)
end)
```

</details>

<details>
<summary><strong>DoesRegistered(player, name)</strong></summary>

Short description: Check whether a client callback is currently registered on a target player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `player` | `number` | Target player source |
| `name` | `string` | Callback name to check |

Returns:

- `boolean`

How to write it as function:

```lua
local exists = FWB.CB.DoesRegistered(player, name)
```

How to write it as export:

```lua
local exists = exports['fs_bridge']:DoesClientCallbackRegistered(player, name)
```

Example as function:

```lua
local exists = FWB.CB.DoesRegistered(source, 'garage:clientCanOpen')
```

Example as export:

```lua
local exists = exports['fs_bridge']:DoesClientCallbackRegistered(source, 'garage:clientCanOpen')
```

</details>

## FWB.Notify

<details>
<summary><strong>Notify(source, argument)</strong></summary>

Short description: Send a Bridge notification to a player through the currently selected notification resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `argument` | `string|table` | Accepts a plain string or a table with keys like `title`, `description`, `type`, `position`, and `duration` |

Returns:

- resource-specific notification result
- `nil`

How to write it as function:

```lua
FWB.Notify(source, argument)
```

How to write it as export:

```lua
exports['fs_bridge']:Notify(source, argument)
```

Example as function:

```lua
FWB.Notify(source, {
    title = 'Garage',
    description = 'Vehicle stored successfully.',
    type = 'success'
})
```

Example as export:

```lua
exports['fs_bridge']:Notify(source, {
    description = 'Vehicle stored successfully.',
    type = 'success'
})
```

</details>

## FWB.Player

### Player

<details>
<summary><strong>Get(source)</strong></summary>

Short description: Read the framework player object for a player source.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- framework player object
- `nil` when unavailable

How to write it as function:

```lua
local player = FWB.Player.Get(source)
```

How to write it as export:

```lua
local player = exports['fs_bridge']:GetPlayer(source)
```

Example as function:

```lua
local player = FWB.Player.Get(source)
if player then
    print('player found')
end
```

Example as export:

```lua
local player = exports['fs_bridge']:GetPlayer(source)
if player then
    print('player found')
end
```

</details>

<details>
<summary><strong>CharacterId(source)</strong></summary>

Short description: Read the current character identifier for a player source.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local characterId = FWB.Player.CharacterId(source)
```

How to write it as export:

```lua
local characterId = exports['fs_bridge']:GetPlayerCharacterId(source)
```

Example as function:

```lua
print(FWB.Player.CharacterId(source))
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerCharacterId(source))
```

</details>

<details>
<summary><strong>Name(source) / IsBoss(source)</strong></summary>

Short description: Read a player's display name or check whether the player is a boss in the active job.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- player name for `Name(source)`
- `boolean` for `IsBoss(source)`

How to write it as function:

```lua
local name = FWB.Player.Name(source)
local isBoss = FWB.Player.IsBoss(source)
```

How to write it as export:

```lua
local name = exports['fs_bridge']:GetPlayerName(source)
local isBoss = exports['fs_bridge']:IsPlayerBoss(source)
```

Example as function:

```lua
print(FWB.Player.Name(source), FWB.Player.IsBoss(source))
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerName(source), exports['fs_bridge']:IsPlayerBoss(source))
```

</details>

<details>
<summary><strong>GetMoney(source) / AddMoney(source, amount) / RemoveMoney(source, amount)</strong></summary>

Short description: Read or update a player's cash money balance through the active framework.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `amount` | `number` | Money amount for add/remove calls |

Returns:

- current money for `GetMoney`
- framework-specific result for add/remove calls

How to write it as function:

```lua
local money = FWB.Player.GetMoney(source)
FWB.Player.AddMoney(source, amount)
FWB.Player.RemoveMoney(source, amount)
```

How to write it as export:

```lua
local money = exports['fs_bridge']:GetPlayerMoney(source)
exports['fs_bridge']:AddPlayerMoney(source, amount)
exports['fs_bridge']:RemovePlayerMoney(source, amount)
```

Example as function:

```lua
print(FWB.Player.GetMoney(source))
FWB.Player.AddMoney(source, 500)
FWB.Player.RemoveMoney(source, 250)
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerMoney(source))
exports['fs_bridge']:AddPlayerMoney(source, 500)
exports['fs_bridge']:RemovePlayerMoney(source, 250)
```

</details>

<details>
<summary><strong>GetBankMoney(source) / AddBankMoney(source, amount) / RemoveBankMoney(source, amount)</strong></summary>

Short description: Read or update a player's bank balance through the active framework.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `amount` | `number` | Money amount for add/remove calls |

Returns:

- current bank money for `GetBankMoney`
- framework-specific result for add/remove calls

How to write it as function:

```lua
local bankMoney = FWB.Player.GetBankMoney(source)
FWB.Player.AddBankMoney(source, amount)
FWB.Player.RemoveBankMoney(source, amount)
```

How to write it as export:

```lua
local bankMoney = exports['fs_bridge']:GetBankMoney(source)
exports['fs_bridge']:AddBankMoney(source, amount)
exports['fs_bridge']:RemoveBankMoney(source, amount)
```

Example as function:

```lua
print(FWB.Player.GetBankMoney(source))
FWB.Player.AddBankMoney(source, 500)
FWB.Player.RemoveBankMoney(source, 250)
```

Example as export:

```lua
print(exports['fs_bridge']:GetBankMoney(source))
exports['fs_bridge']:AddBankMoney(source, 500)
exports['fs_bridge']:RemoveBankMoney(source, 250)
```

</details>

<details>
<summary><strong>ToggleDuty(source) / IsOnDuty(source)</strong></summary>

Short description: Toggle or check the active duty state for a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- framework-specific result for `ToggleDuty`
- `boolean` for `IsOnDuty`

How to write it as function:

```lua
FWB.Player.ToggleDuty(source)
local onDuty = FWB.Player.IsOnDuty(source)
```

How to write it as export:

```lua
exports['fs_bridge']:TogglePlayerDuty(source)
local onDuty = exports['fs_bridge']:IsPlayerOnDuty(source)
```

Example as function:

```lua
FWB.Player.ToggleDuty(source)
print(FWB.Player.IsOnDuty(source))
```

Example as export:

```lua
exports['fs_bridge']:TogglePlayerDuty(source)
print(exports['fs_bridge']:IsPlayerOnDuty(source))
```

</details>

<details>
<summary><strong>IsAllowed(source, permissions)</strong></summary>

Short description: Check a player against a Bridge permissions table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `permissions` | `table` | Permission table such as `jobgroups`, `characters`, or other framework-supported checks |

Returns:

- `boolean`

How to write it as function:

```lua
local allowed = FWB.Player.IsAllowed(source, permissions)
```

How to write it as export:

```lua
local allowed = exports['fs_bridge']:IsPlayerAllowed(source, permissions)
```

Example as function:

```lua
local allowed = FWB.Player.IsAllowed(source, {
    jobgroups = {
        police = 0,
        ambulance = 1
    }
})
```

Example as export:

```lua
local allowed = exports['fs_bridge']:IsPlayerAllowed(source, {
    jobgroups = {
        police = 0,
        ambulance = 1
    }
})
```

</details>

<details>
<summary><strong>Detail(characterId)</strong></summary>

Short description: Read player detail data by character identifier, commonly for offline lookups.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `characterId` | `string` | Character identifier |

Returns:

- detail table
- `nil` when unavailable

How to write it as function:

```lua
local detail = FWB.Player.Detail(characterId)
```

How to write it as export:

```lua
local detail = exports['fs_bridge']:GetPlayerDetail(characterId)
```

Example as function:

```lua
local detail = FWB.Player.Detail('char1:identifier')
```

Example as export:

```lua
local detail = exports['fs_bridge']:GetPlayerDetail('char1:identifier')
```

</details>

<details>
<summary><strong>Online_CK_By_Source(source) / Offline_CK_By_CharacterId(characterId) / Offline_Ck_All_Characters_By_Identifier(identifier)</strong></summary>

Short description: Run Bridge character cleanup helpers for online and offline character records.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source for online cleanup |
| `characterId` | `string` | Character identifier for one offline character |
| `identifier` | `string` | Base identifier for all characters under one owner |

Returns:

- framework-specific cleanup result

How to write it as function:

```lua
FWB.Player.Online_CK_By_Source(source)
FWB.Player.Offline_CK_By_CharacterId(characterId)
FWB.Player.Offline_Ck_All_Characters_By_Identifier(identifier)
```

How to write it as export:

```lua
exports['fs_bridge']:CKOnlineCharacterBySource(source)
exports['fs_bridge']:CKOfflineCharacterByCharacterId(characterId)
exports['fs_bridge']:CKAllOfflineCharactersByIdentifier(identifier)
```

Example as function:

```lua
FWB.Player.Offline_CK_By_CharacterId('char1:identifier')
```

Example as export:

```lua
exports['fs_bridge']:CKOfflineCharacterByCharacterId('char1:identifier')
```

</details>

### Job

<details>
<summary><strong>Job.Data(source) / Job.Name(source) / Job.GradeLevel(source)</strong></summary>

Short description: Read the active job state for a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- job data table, job name, or grade level depending on the call

How to write it as function:

```lua
local jobData = FWB.Player.Job.Data(source)
local jobName = FWB.Player.Job.Name(source)
local gradeLevel = FWB.Player.Job.GradeLevel(source)
```

How to write it as export:

```lua
local jobData = exports['fs_bridge']:GetPlayerJobData(source)
local jobName = exports['fs_bridge']:GetPlayerJobName(source)
local gradeLevel = exports['fs_bridge']:GetPlayerJobGradeLevel(source)
```

Example as function:

```lua
print(FWB.Player.Job.Name(source), FWB.Player.Job.GradeLevel(source))
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerJobName(source), exports['fs_bridge']:GetPlayerJobGradeLevel(source))
```

</details>

<details>
<summary><strong>Job.Set(source, job, grade)</strong></summary>

Short description: Set a player's job through the active framework bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `job` | `string` | Job name |
| `grade` | `number|string` | Job grade |

Returns:

- framework-specific result

How to write it as function:

```lua
FWB.Player.Job.Set(source, job, grade)
```

How to write it as export:

```lua
exports['fs_bridge']:SetPlayerJob(source, job, grade)
```

Example as function:

```lua
FWB.Player.Job.Set(source, 'police', 2)
```

Example as export:

```lua
exports['fs_bridge']:SetPlayerJob(source, 'police', 2)
```

</details>

## FWB.Job

<details>
<summary><strong>All() / PlayerCount(jobName)</strong></summary>

Short description: Read all job definitions or count online players inside a job.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `jobName` | `string` | Job name for `PlayerCount(jobName)` |

Returns:

- jobs table for `All()`
- `number` online count for `PlayerCount(jobName)`

How to write it as function:

```lua
local jobs = FWB.Job.All()
local count = FWB.Job.PlayerCount(jobName)
```

How to write it as export:

```lua
local jobs = exports['fs_bridge']:GetJobs()
local count = exports['fs_bridge']:GetJobPlayerCount(jobName)
```

Example as function:

```lua
local jobs = FWB.Job.All()
local count = FWB.Job.PlayerCount('police')
```

Example as export:

```lua
local jobs = exports['fs_bridge']:GetJobs()
local count = exports['fs_bridge']:GetJobPlayerCount('police')
```

</details>

## FWB.Ambulance

<details>
<summary><strong>GetAmbulanceResourceName()</strong></summary>

Short description: Get the detected ambulance resource name for the current server build.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` resource name
- `nil` when unavailable

How to write it as function:

```lua
local resourceName = FWB.Ambulance.GetAmbulanceResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetAmbulanceResourceName()
```

Example as function:

```lua
print(FWB.Ambulance.GetAmbulanceResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetAmbulanceResourceName())
```

</details>

<details>
<summary><strong>IsPlayerDowned(source) / IsPlayerDead(source) / RevivePlayer(source)</strong></summary>

Short description: Read or update ambulance state for a player source.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `boolean` for downed/dead checks
- compatibility-specific result for revive

How to write it as function:

```lua
local downed = FWB.Ambulance.IsPlayerDowned(source)
local dead = FWB.Ambulance.IsPlayerDead(source)
FWB.Ambulance.RevivePlayer(source)
```

How to write it as export:

```lua
local downed = exports['fs_bridge']:IsPlayerDowned(source)
local dead = exports['fs_bridge']:IsPlayerDead(source)
exports['fs_bridge']:RevivePlayer(source)
```

Example as function:

```lua
if FWB.Ambulance.IsPlayerDead(source) then
    FWB.Ambulance.RevivePlayer(source)
end
```

Example as export:

```lua
if exports['fs_bridge']:IsPlayerDead(source) then
    exports['fs_bridge']:RevivePlayer(source)
end
```

</details>

## FWB.Banking

<details>
<summary><strong>ResourceName()</strong></summary>

Short description: Read the active banking resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` resource name
- `nil` when unavailable

How to write it as function:

```lua
local resourceName = FWB.Banking.ResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetBankResourceName()
```

Example as function:

```lua
print(FWB.Banking.ResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetBankResourceName())
```

</details>

<details>
<summary><strong>AddSocietyMoney(job, money) / RemoveSocietyMoney(job, money) / GetSocietyMoney(job) / RegisterSociety(job, label)</strong></summary>

Short description: Manage Bridge society account helpers for banking integrations.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `job` | `string` | Society or job name |
| `money` | `number` | Money amount for add/remove calls |
| `label` | `string` | Display label for `RegisterSociety` |

Returns:

- current society money for `GetSocietyMoney`
- banking-specific result for the other calls

How to write it as function:

```lua
FWB.Banking.AddSocietyMoney(job, money)
FWB.Banking.RemoveSocietyMoney(job, money)
local money = FWB.Banking.GetSocietyMoney(job)
FWB.Banking.RegisterSociety(job, label)
```

How to write it as export:

```lua
exports['fs_bridge']:AddSocietyMoney(job, money)
exports['fs_bridge']:RemoveSocietyMoney(job, money)
local money = exports['fs_bridge']:GetSocietyMoney(job)
exports['fs_bridge']:RegisterSociety(job, label)
```

Example as function:

```lua
FWB.Banking.RegisterSociety('police', 'Police')
FWB.Banking.AddSocietyMoney('police', 5000)
print(FWB.Banking.GetSocietyMoney('police'))
```

Example as export:

```lua
exports['fs_bridge']:RegisterSociety('police', 'Police')
exports['fs_bridge']:AddSocietyMoney('police', 5000)
print(exports['fs_bridge']:GetSocietyMoney('police'))
```

</details>

## FWB.Player.Request

<details>
<summary><strong>AnimDict(dict, timeout) / Model(model, timeout)</strong></summary>

Short description: Server-side request helpers exist for API compatibility, but they do not actually stream assets on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `dict` | `string` | Animation dictionary name |
| `model` | `string|number` | Model name or hash |
| `timeout` | `number` | Optional compatibility argument |

Returns:

- `true`

How to write it as function:

```lua
local okDict = FWB.Player.Request.AnimDict(dict, timeout)
local okModel = FWB.Player.Request.Model(model, timeout)
```

How to write it as export:

```lua
local okDict = exports['fs_bridge']:RequestAnimDict(dict, timeout)
local okModel = exports['fs_bridge']:RequestModel(model, timeout)
```

Example as function:

```lua
FWB.Player.Request.AnimDict('amb@prop_human_bum_bin@base')
FWB.Player.Request.Model('adder')
```

Example as export:

```lua
exports['fs_bridge']:RequestAnimDict('amb@prop_human_bum_bin@base')
exports['fs_bridge']:RequestModel('adder')
```

</details>

## FWB.Player.Vehicle.Keys

<details>
<summary><strong>Give(source, vehicle) / Remove(source, vehicle)</strong></summary>

Short description: Give or remove vehicle keys for a target player through the active key system resolver.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- resource-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(source, vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(source, vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Give(source, vehicle)
FWB.Player.Vehicle.Keys.Remove(source, vehicle)
```

Example as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(source, vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(source, vehicle)
```

</details>

## FWB.Vehicle.Keys

<details>
<summary><strong>ResourceName()</strong></summary>

Short description: Get the detected vehicle keys resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` resource name
- `nil` when unavailable

How to write it as function:

```lua
local resourceName = FWB.Vehicle.Keys.ResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetVehicleKeysResourceName()
```

Example as function:

```lua
print(FWB.Vehicle.Keys.ResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetVehicleKeysResourceName())
```

</details>

## FWB.Log

<details>
<summary><strong>Create(source, event, message, ...)</strong></summary>

Short description: Send a structured log entry through the active Bridge logger.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source related to the log |
| `event` | `string` | Log event name |
| `message` | `string` | Main log message |
| `...` | `any` | Optional extra values passed through to the logger |

Returns:

- logger-specific result
- `nil`

How to write it as function:

```lua
FWB.Log.Create(source, event, message, ...)
```

How to write it as export:

```lua
exports['fs_bridge']:CreateLog(source, event, message, ...)
```

Example as function:

```lua
FWB.Log.Create(source, 'Garage', 'Vehicle stored successfully.')
```

Example as export:

```lua
exports['fs_bridge']:CreateLog(source, 'Garage', 'Vehicle stored successfully.')
```

</details>

## FWB.Hacker

<details>
<summary><strong>Kick(source, reason) / Ban(source, reason)</strong></summary>

Short description: Run the configured Bridge kick or ban handlers.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `reason` | `string` | Optional reason text |

Returns:

- framework or override-specific result
- `false` when no handler is configured

How to write it as function:

```lua
FWB.Hacker.Kick(source, reason)
FWB.Hacker.Ban(source, reason)
```

How to write it as export:

```lua
exports['fs_bridge']:KickPlayer(source, reason)
exports['fs_bridge']:Ban(source, reason)
```

Example as function:

```lua
FWB.Hacker.Kick(source, 'Unauthorized action detected.')
```

Example as export:

```lua
exports['fs_bridge']:KickPlayer(source, 'Unauthorized action detected.')
```

</details>

## Dispatch Helpers

<details>
<summary><strong>FWB.AddCustomDispatch(argument) / FWB.GetDispatchResourceName()</strong></summary>

Short description: Create a dispatch alert through the active server dispatch layer and read the detected dispatch resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `argument` | `table` | Dispatch payload with keys like `Job`, `Location`, `CallCode`, `Message`, `Flashes`, `Image`, `icon`, and `Blip` |

Returns:

- dispatch-specific result for `FWB.AddCustomDispatch(argument)`
- resource name for `FWB.GetDispatchResourceName()`

How to write it as function:

```lua
FWB.AddCustomDispatch(argument)
local resourceName = FWB.GetDispatchResourceName()
```

How to write it as export:

- No direct export is provided for these server helpers.

Example as function:

```lua
FWB.AddCustomDispatch({
    Job = { 'police' },
    Location = vector3(0.0, 0.0, 0.0),
    Message = 'Suspicious activity reported.'
})
```

</details>

## FWB.Blip

<details>
<summary><strong>Create(options) / CreateMoving(options)</strong></summary>

Short description: Create static or moving server-managed blips and sync them to allowed players.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Blip options table |

Common option keys:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Coordinates for static blips |
| `targets` | `number|table|-1` | Audience for the blip |
| `jobs` | `string|table` | Job-based permission helper |
| `grade` | `number` | Minimum grade helper |
| `handle` | `string` | Optional custom handle |
| `title` | `string` | Blip label |
| `id` | `number` | Sprite id |
| `color` | `number` | Blip color |
| `route` | `boolean` | Draw route |
| `radius` | `number` | Optional radius zone |
| `trackSource` | `number` | Tracked player source for moving blips |
| `entity` | `number` | Tracked entity for moving blips |
| `updateTime` | `number` | Minimum `5000` ms |

Returns:

- `string` handle
- entry table

How to write it as function:

```lua
local handle, entry = FWB.Blip.Create(options)
local movingHandle, movingEntry = FWB.Blip.CreateMoving(options)
```

How to write it as export:

```lua
local handle, entry = exports['fs_bridge']:CreateBlip(options)
local movingHandle, movingEntry = exports['fs_bridge']:CreateMovingBlip(options)
```

Example as function:

```lua
FWB.Blip.Create({
    targets = -1,
    coords = vector3(441.2, -981.9, 30.7),
    title = 'Police HQ',
    id = 60,
    color = 3
})
```

Example as export:

```lua
exports['fs_bridge']:CreateBlip({
    targets = -1,
    coords = vector3(441.2, -981.9, 30.7),
    title = 'Police HQ',
    id = 60,
    color = 3
})
```

</details>

<details>
<summary><strong>Update(handle, updates) / Toggle(handle, enabled) / Remove(handle)</strong></summary>

Short description: Update, toggle, or remove a server-managed blip entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Bridge blip handle |
| `updates` | `table` | Partial updates table for `Update` |
| `enabled` | `boolean` | Toggle state for `Toggle` |

Returns:

- updated handle and entry for `Update`
- `boolean` for `Toggle` and `Remove`

How to write it as function:

```lua
local handle2, entry = FWB.Blip.Update(handle, updates)
local ok = FWB.Blip.Toggle(handle, enabled)
local removed = FWB.Blip.Remove(handle)
```

How to write it as export:

```lua
local handle2, entry = exports['fs_bridge']:UpdateBlip(handle, updates)
local ok = exports['fs_bridge']:ToggleBlip(handle, enabled)
local removed = exports['fs_bridge']:RemoveBlip(handle)
```

Example as function:

```lua
FWB.Blip.Update(handle, { color = 1, route = true })
FWB.Blip.Toggle(handle, false)
FWB.Blip.Remove(handle)
```

Example as export:

```lua
exports['fs_bridge']:UpdateBlip(handle, { color = 1, route = true })
exports['fs_bridge']:ToggleBlip(handle, false)
exports['fs_bridge']:RemoveBlip(handle)
```

</details>

<details>
<summary><strong>Get(handle) / GetAll() / Clear(resource)</strong></summary>

Short description: Read one server blip entry, read all entries, or clear entries for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Bridge blip handle for `Get(handle)` |
| `resource` | `string` | Optional resource name for `Clear(resource)` |

Returns:

- one blip entry for `Get(handle)`
- all entries for `GetAll()`
- clear result for `Clear(resource)`

How to write it as function:

```lua
local entry = FWB.Blip.Get(handle)
local allBlips = FWB.Blip.GetAll()
FWB.Blip.Clear(resource)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetBlip(handle)
local allBlips = exports['fs_bridge']:GetAllBlips()
exports['fs_bridge']:ClearBlips(resource)
```

Example as function:

```lua
local entry = FWB.Blip.Get(handle)
local allBlips = FWB.Blip.GetAll()
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetBlip(handle)
local allBlips = exports['fs_bridge']:GetAllBlips()
```

</details>

## FWB.Entity

<details>
<summary><strong>Object.Nearby(extras) / Object.Closest(extras)</strong></summary>

Short description: Find nearby objects around server-side coordinates or a source player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `source`, `coords`, `model`, `models`, `excludeModels`, `maxDistance`, and `maxCount` |

Returns:

- object entry list for `Nearby`
- one object entry for `Closest`

How to write it as function:

```lua
local objects = FWB.Entity.Object.Nearby(extras)
local object = FWB.Entity.Object.Closest(extras)
```

How to write it as export:

```lua
local objects = exports['fs_bridge']:GetNearbyObjects(extras)
local object = exports['fs_bridge']:GetClosestObject(extras)
```

Example as function:

```lua
local object = FWB.Entity.Object.Closest({
    source = source,
    maxDistance = 5.0
})
```

Example as export:

```lua
local object = exports['fs_bridge']:GetClosestObject({
    source = source,
    maxDistance = 5.0
})
```

</details>

<details>
<summary><strong>Player.Nearby(extras) / Player.Closest(extras)</strong></summary>

Short description: Find nearby player entries around server-side coordinates or a source player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `source`, `coords`, `selfInclude`, `maxDistance`, and `maxCount` |

Returns:

- player entry list for `Nearby`
- one player entry for `Closest`

How to write it as function:

```lua
local players = FWB.Entity.Player.Nearby(extras)
local player = FWB.Entity.Player.Closest(extras)
```

How to write it as export:

```lua
local players = exports['fs_bridge']:GetNearbyPlayers(extras)
local player = exports['fs_bridge']:GetClosestPlayer(extras)
```

Example as function:

```lua
local player = FWB.Entity.Player.Closest({
    source = source,
    maxDistance = 3.0,
    selfInclude = false
})
```

Example as export:

```lua
local player = exports['fs_bridge']:GetClosestPlayer({
    source = source,
    maxDistance = 3.0,
    selfInclude = false
})
```

</details>

<details>
<summary><strong>Ped.Nearby(extras) / Ped.Closest(extras)</strong></summary>

Short description: Find nearby peds around server-side coordinates or a source player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `source`, `coords`, `includePlayerPeds`, `includeMissionPeds`, `aliveOnly`, and model filters |

Returns:

- ped entry list for `Nearby`
- one ped entry for `Closest`

How to write it as function:

```lua
local peds = FWB.Entity.Ped.Nearby(extras)
local ped = FWB.Entity.Ped.Closest(extras)
```

How to write it as export:

```lua
local peds = exports['fs_bridge']:GetNearbyPeds(extras)
local ped = exports['fs_bridge']:GetClosestPed(extras)
```

Example as function:

```lua
local ped = FWB.Entity.Ped.Closest({
    source = source,
    maxDistance = 5.0,
    aliveOnly = true
})
```

Example as export:

```lua
local ped = exports['fs_bridge']:GetClosestPed({
    source = source,
    maxDistance = 5.0,
    aliveOnly = true
})
```

</details>

<details>
<summary><strong>Vehicle.Nearby(extras) / Vehicle.Closest(extras)</strong></summary>

Short description: Find nearby vehicles around server-side coordinates or a source player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `source`, `coords`, `includePlayerVehicle`, `maxDistance`, and model filters |

Returns:

- vehicle entry list for `Nearby`
- one vehicle entry for `Closest`

How to write it as function:

```lua
local vehicles = FWB.Entity.Vehicle.Nearby(extras)
local vehicle = FWB.Entity.Vehicle.Closest(extras)
```

How to write it as export:

```lua
local vehicles = exports['fs_bridge']:GetNearbyVehicles(extras)
local vehicle = exports['fs_bridge']:GetClosestVehicle(extras)
```

Example as function:

```lua
local vehicle = FWB.Entity.Vehicle.Closest({
    source = source,
    maxDistance = 8.0
})
```

Example as export:

```lua
local vehicle = exports['fs_bridge']:GetClosestVehicle({
    source = source,
    maxDistance = 8.0
})
```

</details>

<details>
<summary><strong>Player.GetFrontCoords(source, extras) / Entity.GetFrontCoords(source, extras) / Entity.FrontCoords(source, extras)</strong></summary>

Short description: Get a point directly in front of a player source, ped, or heading on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Optional player source |
| `extras` | `number|table` | Number shorthand for distance, or a table with `source`, `ped`, `coords`, `heading`, `distance`, and `verticalOffset` |

Returns:

- `vector3`

How to write it as function:

```lua
local frontCoords = FWB.Player.GetFrontCoords(source, extras)
local frontCoords2 = FWB.Entity.GetFrontCoords(source, extras)
local frontCoords3 = FWB.Entity.FrontCoords(source, extras)
```

How to write it as export:

```lua
local frontCoords = exports['fs_bridge']:GetFrontCoords(source, extras)
```

Example as function:

```lua
local frontCoords = FWB.Player.GetFrontCoords(source, {
    distance = 2.0,
    verticalOffset = -0.7
})
```

Example as export:

```lua
local frontCoords = exports['fs_bridge']:GetFrontCoords(source, {
    distance = 2.0,
    verticalOffset = -0.7
})
```

</details>

## FWB.Ped

<details>
<summary><strong>Create(options) / Update(handle, updates) / Remove(handle)</strong></summary>

Short description: Create, update, or remove server-managed ped entries.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Ped creation options table |
| `handle` | `string` | Bridge ped handle |
| `updates` | `table` | Partial updates table for `Update` |

Common option keys:

| Key | Type | Notes |
|---|---|---|
| `model` | `string|number` | Ped model |
| `coords` | `vector4|vector3|table` | Spawn location |
| `source` | `number` | Player source fallback when no coords are supplied |
| `heading` | `number` | Spawn heading |
| `freeze` | `boolean` | Freeze ped in place |
| `invincible` | `boolean` | Make ped invincible |
| `blockEvents` | `boolean` | Ignore ambient events |
| `health` | `number` | Apply health |
| `armour` | `number` | Apply armour |
| `weapon` | `string|number|false` | Give a weapon or remove weapons |
| `ammo` | `number` | Weapon ammo |
| `removeOnDisconnect` | `boolean` | Auto-remove if owner disconnects |

Returns:

- handle, net id, ped entity for `Create`
- success and updated entry for `Update`
- boolean for `Remove`

How to write it as function:

```lua
local handle, netId, ped = FWB.Ped.Create(options)
local success, entry = FWB.Ped.Update(handle, updates)
local ok = FWB.Ped.Remove(handle)
```

How to write it as export:

```lua
local handle, netId, ped = exports['fs_bridge']:CreatePed(options)
local success, entry = exports['fs_bridge']:UpdatePed(handle, updates)
local ok = exports['fs_bridge']:RemovePed(handle)
```

Example as function:

```lua
local handle = FWB.Ped.Create({
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true
})
```

Example as export:

```lua
local handle = exports['fs_bridge']:CreatePed({
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true
})
```

</details>

<details>
<summary><strong>Get(handle) / GetAll() / Clear(resource)</strong></summary>

Short description: Read one server ped entry, read all entries, or clear entries for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Bridge ped handle for `Get(handle)` |
| `resource` | `string` | Optional resource name for `Clear(resource)` |

Returns:

- one ped entry for `Get(handle)`
- all entries for `GetAll()`
- cleared count for `Clear(resource)`

How to write it as function:

```lua
local entry = FWB.Ped.Get(handle)
local allPeds = FWB.Ped.GetAll()
local cleared = FWB.Ped.Clear(resource)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetPed(handle)
local allPeds = exports['fs_bridge']:GetAllPeds()
local cleared = exports['fs_bridge']:ClearPeds(resource)
```

Example as function:

```lua
local entry = FWB.Ped.Get(handle)
local allPeds = FWB.Ped.GetAll()
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetPed(handle)
local allPeds = exports['fs_bridge']:GetAllPeds()
```

</details>

## FWB.Vehicle

<details>
<summary><strong>GeneratePlate() / Plate.Generate()</strong></summary>

Short description: Generate a vehicle plate through the server Bridge runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` generated plate
- `nil` when generation fails

How to write it as function:

```lua
local plate = FWB.Vehicle.GeneratePlate()
local plate2 = FWB.Vehicle.Plate.Generate()
```

How to write it as export:

```lua
local plate = exports['fs_bridge']:GenerateVehiclePlate()
```

Example as function:

```lua
local plate = FWB.Vehicle.GeneratePlate()
print(plate)
```

Example as export:

```lua
local plate = exports['fs_bridge']:GenerateVehiclePlate()
print(plate)
```

</details>

<details>
<summary><strong>Props.Set(source, vehicleNetId, properties)</strong></summary>

Short description: Apply vehicle properties from the server by routing the update through the owning client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Owning player source |
| `vehicleNetId` | `number` | Vehicle network id |
| `properties` | `table` | Vehicle properties table |

Returns:

- `boolean` or callback result

How to write it as function:

```lua
local ok = FWB.Vehicle.Props.Set(source, vehicleNetId, properties)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:SetVehicleProps(source, vehicleNetId, properties)
```

Example as function:

```lua
FWB.Vehicle.Props.Set(source, vehicleNetId, {
    plate = 'ABC123'
})
```

Example as export:

```lua
exports['fs_bridge']:SetVehicleProps(source, vehicleNetId, {
    plate = 'ABC123'
})
```

</details>

<details>
<summary><strong>Owner.Update(oldOwner, newOwner, plate) / InsertNewOwnedVehicle(options)</strong></summary>

Short description: Update an existing owned vehicle record or insert a new owned vehicle entry in the framework database.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `oldOwner` | `string|number` | Previous owner identifier or source |
| `newOwner` | `string|number` | New owner identifier or source |
| `plate` | `string` | Vehicle plate |
| `options` | `table` | Insert table with `owner/source`, `plate`, `model`, and `props` |

Returns:

- success and framework result or error text

How to write it as function:

```lua
local ok, result = FWB.Vehicle.Owner.Update(oldOwner, newOwner, plate)
local ok2, result2 = FWB.Vehicle.InsertNewOwnedVehicle(options)
```

How to write it as export:

```lua
local ok, result = exports['fs_bridge']:UpdateVehicleOwner(oldOwner, newOwner, plate)
local ok2, result2 = exports['fs_bridge']:InsertNewOwnedVehicle(options)
```

Example as function:

```lua
FWB.Vehicle.InsertNewOwnedVehicle({
    owner = source,
    plate = 'ABC123',
    model = 'adder',
    props = {}
})
```

Example as export:

```lua
exports['fs_bridge']:InsertNewOwnedVehicle({
    owner = source,
    plate = 'ABC123',
    model = 'adder',
    props = {}
})
```

</details>

<details>
<summary><strong>Create(spawnSource, model, options) / Update(handleOrEntry, updates) / Remove(handleOrEntry)</strong></summary>

Short description: Create, update, or remove server-managed vehicle entries.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `spawnSource` | `number|vector3|vector4|nil` | Player source, ped handle, coordinates, or omit when `options.coords` is provided |
| `model` | `string|number` | Vehicle model |
| `options` | `table` | Vehicle creation options table |
| `handleOrEntry` | `string|number|table` | Bridge handle, entity, net id, or entry table |
| `updates` | `table` | Partial updates table for `Update` |

Common option keys:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Spawn location |
| `heading` | `number` | Spawn heading |
| `source` | `number` | Owner source |
| `plate` | `string` | Custom plate |
| `fuel` | `number` | Initial fuel |
| `keys` | `boolean` | Give keys |
| `props` | `table` | Vehicle props |
| `rbucket` | `number` | Routing bucket |
| `freeze` | `boolean` | Freeze state |
| `warp` | `boolean` | Warp owner into vehicle |
| `spawnclear` | `boolean` | Clear nearby vehicles before spawning |
| `removeOnDisconnect` | `boolean` | Auto-remove if owner disconnects |
| `removeOnLogout` | `boolean` | Auto-remove if owner logs out |

Returns:

- entry table for `Create`
- success and updated entry for `Update`
- boolean for `Remove`

How to write it as function:

```lua
local entry = FWB.Vehicle.Create(spawnSource, model, options)
local success, updated = FWB.Vehicle.Update(handleOrEntry, updates)
local ok = FWB.Vehicle.Remove(handleOrEntry)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(spawnSource, model, options)
local success, updated = exports['fs_bridge']:UpdateVehicle(handleOrEntry, updates)
local ok = exports['fs_bridge']:RemoveVehicle(handleOrEntry)
```

Example as function:

```lua
local entry = FWB.Vehicle.Create(source, 'adder', {
    source = source,
    plate = FWB.Vehicle.GeneratePlate(),
    keys = true,
    warp = true
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(source, 'adder', {
    source = source,
    plate = exports['fs_bridge']:GenerateVehiclePlate(),
    keys = true,
    warp = true
})
```

</details>

<details>
<summary><strong>Get(handleOrEntry) / GetAll() / Clear(resource)</strong></summary>

Short description: Read one server vehicle entry, read all entries, or clear entries for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrEntry` | `string|number|table` | Bridge handle, entity, net id, or entry table |
| `resource` | `string` | Optional resource name when clearing |

Returns:

- one entry for `Get(handleOrEntry)`
- all entries for `GetAll()`
- cleared count for `Clear(resource)`

How to write it as function:

```lua
local entry = FWB.Vehicle.Get(handleOrEntry)
local allVehicles = FWB.Vehicle.GetAll()
local cleared = FWB.Vehicle.Clear(resource)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetVehicle(handleOrEntry)
local allVehicles = exports['fs_bridge']:GetAllVehicles()
local cleared = exports['fs_bridge']:ClearVehicles(resource)
```

Example as function:

```lua
local entry = FWB.Vehicle.Get(entry.handle)
local allVehicles = FWB.Vehicle.GetAll()
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetVehicle(entry.handle)
local allVehicles = exports['fs_bridge']:GetAllVehicles()
```

</details>

## Framework Helpers

<details>
<summary><strong>GetFrameworkName() / GetPlayers()</strong></summary>

Short description: Read the detected framework name or the current player list from the active server bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | `GetFrameworkName()` and `GetPlayers()` do not take any arguments |

Returns:

- `string` framework name for `GetFrameworkName()`
- player list table for `GetPlayers()`

How to write it as function:

```lua
local framework = FWB.GetFrameworkName()
local players = FWB.GetPlayers()
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local framework = FWB.GetFrameworkName()
local players = FWB.GetPlayers()
print(framework, #players)
```

</details>

## Vehicle Ownership Helpers

<details>
<summary><strong>GetOwnedVehiclesList() / GetVehicleDetailFromPlate(plate)</strong></summary>

Short description: Read the framework-backed owned vehicle index or fetch one owned vehicle record by plate.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `plate` | `string` | Vehicle plate text for `GetVehicleDetailFromPlate(plate)` |

Returns:

- owned vehicle table for `GetOwnedVehiclesList()`
- vehicle detail table for `GetVehicleDetailFromPlate(plate)`
- `nil` when not found

How to write it as function:

```lua
local ownedVehicles = FWB.GetOwnedVehiclesList()
local detail = FWB.GetVehicleDetailFromPlate(plate)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local ownedVehicles = FWB.GetOwnedVehiclesList()
local detail = FWB.GetVehicleDetailFromPlate('ABC123')
```

Notes:

- These helpers read framework ownership data, not only the runtime vehicle list managed by `FWB.Vehicle`.

</details>

## Inventory Helpers

<details>
<summary><strong>AddItem(source, item, amount, slot, metadata) / RemoveItem(source, item, amount, slot)</strong></summary>

Short description: Add or remove inventory items through the active inventory compatibility layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `item` | `string` | Item name |
| `amount` | `number` | Item count |
| `slot` | `number` | Optional slot |
| `metadata` | `table` | Optional metadata table for `AddItem` |

Returns:

- inventory-specific success result
- `false` when the action fails

How to write it as function:

```lua
local added = FWB.AddItem(source, item, amount, slot, metadata)
local removed = FWB.RemoveItem(source, item, amount, slot)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
FWB.AddItem(source, 'water', 2, nil, {
    description = 'Fresh water bottle'
})

FWB.RemoveItem(source, 'water', 1)
```

</details>

<details>
<summary><strong>CanCarryItem(source, item, amount) / GetItemCount(source, item) / HasInventoryItemCount(source, item, amount, metadata)</strong></summary>

Short description: Run common server-side inventory checks before adding, removing, or validating items.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `item` | `string` | Item name |
| `amount` | `number` | Target amount |
| `metadata` | `table` | Optional metadata filter for `HasInventoryItemCount` |

Returns:

- `boolean` for `CanCarryItem` and `HasInventoryItemCount`
- `number` item count for `GetItemCount`

How to write it as function:

```lua
local canCarry = FWB.CanCarryItem(source, item, amount)
local count = FWB.GetItemCount(source, item)
local hasEnough = FWB.HasInventoryItemCount(source, item, amount, metadata)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
if FWB.CanCarryItem(source, 'water', 2) then
    FWB.AddItem(source, 'water', 2)
end

local hasRadio = FWB.HasInventoryItemCount(source, 'radio', 1)
```

</details>

<details>
<summary><strong>GetItemLabel(item) / ItemExists(item)</strong></summary>

Short description: Read item label metadata or validate that an item exists in the active framework or inventory setup.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `item` | `string` | Item name |

Returns:

- `string` item label for `GetItemLabel(item)`
- `boolean` for `ItemExists(item)`

How to write it as function:

```lua
local label = FWB.GetItemLabel(item)
local exists = FWB.ItemExists(item)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
if FWB.ItemExists('water') then
    print(FWB.GetItemLabel('water'))
end
```

</details>

<details>
<summary><strong>GetInventoryItems(source, name_index) / GetInventoryItemsList(source, name_index)</strong></summary>

Short description: Read a player's inventory item data table or a simplified item label list.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `name_index` | `boolean` | Optional name-indexed result mode |

Returns:

- formatted inventory item table for `GetInventoryItems`
- label-only list for `GetInventoryItemsList`

How to write it as function:

```lua
local items = FWB.GetInventoryItems(source, name_index)
local labels = FWB.GetInventoryItemsList(source, name_index)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local items = FWB.GetInventoryItems(source, true)
local labels = FWB.GetInventoryItemsList(source)
```

</details>

<details>
<summary><strong>GetServerItems() / GetInventory()</strong></summary>

Short description: Read the cached server item definition list or the detected inventory resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- item definition table for `GetServerItems()`
- `string` detected inventory resource name for `GetInventory()`

How to write it as function:

```lua
local items = FWB.GetServerItems()
local inventoryName = FWB.GetInventory()
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local items = FWB.GetServerItems()
local inventoryName = FWB.GetInventory()
print(inventoryName, items['water'] and items['water'].label)
```

</details>

<details>
<summary><strong>RegisterItem(item, event, ...)</strong></summary>

Short description: Register a usable item event through the active inventory or framework layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `item` | `string` | Item name |
| `event` | `string` | Event name to run |
| `...` | `any` | Optional extra values passed through to the registration layer |

Returns:

- inventory-specific registration result

How to write it as function:

```lua
FWB.RegisterItem(item, event, ...)
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
FWB.RegisterItem('water', 'my_resource:useWater')
```

Notes:

- The older `RegisterUseableItem` path is intentionally omitted here because it is deprecated.

</details>

<details>
<summary><strong>GetBlackMoney(source) / AddBlackMoney(source, amount) / RemoveBlackMoney(source, amount)</strong></summary>

Short description: Read or update black money through the active framework or inventory compatibility layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `amount` | `number` | Money amount for add or remove calls |

Returns:

- current black money amount for `GetBlackMoney(source)`
- inventory-specific result for add or remove calls

How to write it as function:

```lua
local dirtyMoney = FWB.GetBlackMoney(source)
FWB.AddBlackMoney(source, amount)
FWB.RemoveBlackMoney(source, amount)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local dirtyMoney = FWB.GetBlackMoney(source)
FWB.AddBlackMoney(source, 500)
FWB.RemoveBlackMoney(source, 250)
```

</details>

<details>
<summary><strong>RegisterStash(data) / ReRegisterStash(data) / RegisterShop(data)</strong></summary>

Short description: Register shared stash or shop data through the active inventory compatibility layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `data` | `table` | Registration table with keys like `name`, `label`, `slots`, `weight`, `coords`, `jobs`, or `identifier` |

Returns:

- inventory-specific registration result
- `nil` when validation fails

How to write it as function:

```lua
FWB.RegisterStash(data)
FWB.ReRegisterStash(data)
FWB.RegisterShop(data)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
FWB.RegisterStash({
    name = 'police_armory',
    label = 'Police Armory',
    slots = 100,
    weight = 100000,
    jobs = {
        police = 0
    }
})
```

Notes:

- `ReRegisterStash(data)` is mainly useful when your script edits stash data at runtime.
- `RegisterShop(data)` depends on inventory support and may not be available in every provider.

</details>

## Phone Helpers

<details>
<summary><strong>SendEmail(source, emaildata)</strong></summary>

Short description: Send an email payload through the active phone compatibility layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number|string` | Online source id or identifier string depending on provider |
| `emaildata` | `table` | Email payload with keys like `sender`, `subject`, `message`, and `imageurl` |

Returns:

- phone-specific send result
- `nil` when the provider does not support the request

How to write it as function:

```lua
FWB.SendEmail(source, emaildata)
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
FWB.SendEmail(source, {
    sender = 'Garage',
    subject = 'Vehicle Stored',
    message = 'Your vehicle has been stored successfully.'
})
```

</details>

<details>
<summary><strong>GetPhoneResourceName()</strong></summary>

Short description: Read the currently detected phone resource name from the server compatibility layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` phone resource name
- `nil` when unavailable

How to write it as function:

```lua
local phoneResource = FWB.GetPhoneResourceName()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local phoneResource = FWB.GetPhoneResourceName()
print(phoneResource)
```

</details>

## Sound Helpers

<details>
<summary><strong>PlayUrlPos(source, position, distance, url, volume, loop)</strong></summary>

Short description: Play a positioned sound through the active sound compatibility layer and return the generated sound id.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number|-1` | Target player source or broadcast target depending on provider |
| `position` | `vector3` | World position |
| `distance` | `number` | Audible distance |
| `url` | `string` | Audio stream url |
| `volume` | `number` | Volume level |
| `loop` | `boolean` | Loop flag |

Returns:

- provider-specific response
- generated sound id string

How to write it as function:

```lua
local response, soundId = FWB.PlayUrlPos(source, position, distance, url, volume, loop)
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local response, soundId = FWB.PlayUrlPos(source, vec3(441.2, -981.9, 30.7), 20.0, 'https://example.com/audio.mp3', 0.5, false)
```

</details>

<details>
<summary><strong>Destroy(source, soundId) / GetSoundResourceName()</strong></summary>

Short description: Stop a sound that was started through Bridge, or read the detected sound resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number|-1` | Target player source or broadcast target depending on provider |
| `soundId` | `string` | Generated sound id returned by `PlayUrlPos` |

Returns:

- destroy result for `Destroy(source, soundId)`
- `string` sound resource name for `GetSoundResourceName()`

How to write it as function:

```lua
FWB.Destroy(source, soundId)
local soundResource = FWB.GetSoundResourceName()
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
FWB.Destroy(source, soundId)
print(FWB.GetSoundResourceName())
```

</details>

## FWB.String

<details>
<summary><strong>Trim(str) / Plate(str)</strong></summary>

Short description: Trim whitespace from a string. `Plate(str)` is the public plate-cleaning alias.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Input string |

Returns:

- `string`

How to write it as function:

```lua
local value = FWB.String.Trim(str)
local plate = FWB.String.Plate(str)
```

How to write it as export:

```lua
local value = exports['fs_bridge']:TrimString(str)
```

Example as function:

```lua
local plate = FWB.String.Plate('  ABC123  ')
print(plate)
```

Example as export:

```lua
local value = exports['fs_bridge']:TrimString('  hello  ')
print(value)
```

</details>

<details>
<summary><strong>Capitalize(str) / Upper(str) / Lower(str)</strong></summary>

Short description: Normalize a string to capitalized, uppercase, or lowercase text.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Input string |

Returns:

- `string`

How to write it as function:

```lua
local capitalized = FWB.String.Capitalize(str)
local upper = FWB.String.Upper(str)
local lower = FWB.String.Lower(str)
```

How to write it as export:

```lua
local capitalized = exports['fs_bridge']:CapitalizeString(str)
local upper = exports['fs_bridge']:UpperString(str)
local lower = exports['fs_bridge']:LowerString(str)
```

Example as function:

```lua
print(FWB.String.Capitalize('garage'))
print(FWB.String.Upper('garage'))
print(FWB.String.Lower('GARAGE'))
```

Example as export:

```lua
print(exports['fs_bridge']:CapitalizeString('garage'))
print(exports['fs_bridge']:UpperString('garage'))
print(exports['fs_bridge']:LowerString('GARAGE'))
```

</details>

<details>
<summary><strong>StartsWith(str, prefix, caseSensitive) / EndsWith(str, suffix, caseSensitive) / Contains(str, search, caseSensitive, plain)</strong></summary>

Short description: Run common prefix, suffix, or contains checks on text.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Input string |
| `prefix` | `string` | Prefix for `StartsWith` |
| `suffix` | `string` | Suffix for `EndsWith` |
| `search` | `string` | Search text for `Contains` |
| `caseSensitive` | `boolean` | Optional case-sensitive check, defaults to `true` |
| `plain` | `boolean` | Optional plain search mode for `Contains`, defaults to `true` |

Returns:

- `boolean`

How to write it as function:

```lua
local a = FWB.String.StartsWith(str, prefix, caseSensitive)
local b = FWB.String.EndsWith(str, suffix, caseSensitive)
local c = FWB.String.Contains(str, search, caseSensitive, plain)
```

How to write it as export:

```lua
local a = exports['fs_bridge']:StringStartsWith(str, prefix, caseSensitive)
local b = exports['fs_bridge']:StringEndsWith(str, suffix, caseSensitive)
local c = exports['fs_bridge']:StringContains(str, search, caseSensitive, plain)
```

Example as function:

```lua
print(FWB.String.StartsWith('police_armory', 'police'))
print(FWB.String.EndsWith('plate:ABC123', 'ABC123'))
print(FWB.String.Contains('garage menu', 'menu'))
```

Example as export:

```lua
print(exports['fs_bridge']:StringStartsWith('police_armory', 'police'))
print(exports['fs_bridge']:StringEndsWith('plate:ABC123', 'ABC123'))
print(exports['fs_bridge']:StringContains('garage menu', 'menu'))
```

</details>

<details>
<summary><strong>IsNullOrEmpty(str, trim) / IsNullOrWhitespace(str)</strong></summary>

Short description: Check whether a string is empty, nil, or whitespace-only.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Input string |
| `trim` | `boolean` | Optional trim flag for `IsNullOrEmpty` |

Returns:

- `boolean`

How to write it as function:

```lua
local empty = FWB.String.IsNullOrEmpty(str, trim)
local whitespace = FWB.String.IsNullOrWhitespace(str)
```

How to write it as export:

```lua
local empty = exports['fs_bridge']:StringIsNullOrEmpty(str, trim)
local whitespace = exports['fs_bridge']:StringIsNullOrWhitespace(str)
```

Example as function:

```lua
print(FWB.String.IsNullOrEmpty('', true))
print(FWB.String.IsNullOrWhitespace('   '))
```

Example as export:

```lua
print(exports['fs_bridge']:StringIsNullOrEmpty('', true))
print(exports['fs_bridge']:StringIsNullOrWhitespace('   '))
```

</details>

<details>
<summary><strong>Split(str, separator, plain) / Replace(str, search, replacement, plain)</strong></summary>

Short description: Split or replace text with Bridge string helpers.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Input string |
| `separator` | `string` | Separator used by `Split` |
| `search` | `string` | Search text used by `Replace` |
| `replacement` | `string` | Replacement text |
| `plain` | `boolean` | Optional plain mode |

Returns:

- `table` for `Split`
- `string` for `Replace`

How to write it as function:

```lua
local parts = FWB.String.Split(str, separator, plain)
local replaced = FWB.String.Replace(str, search, replacement, plain)
```

How to write it as export:

```lua
local parts = exports['fs_bridge']:SplitString(str, separator, plain)
local replaced = exports['fs_bridge']:ReplaceString(str, search, replacement, plain)
```

Example as function:

```lua
local parts = FWB.String.Split('police,ambulance,mechanic', ',')
local replaced = FWB.String.Replace('plate-abc123', '-', ':')
```

Example as export:

```lua
local parts = exports['fs_bridge']:SplitString('police,ambulance,mechanic', ',')
local replaced = exports['fs_bridge']:ReplaceString('plate-abc123', '-', ':')
```

</details>

## FWB.Table

<details>
<summary><strong>Contains(tbl, value) / TableContains(tbl, value)</strong></summary>

Short description: Run shallow or deep table contains checks.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Target table |
| `value` | `any` | Value to search for |

Returns:

- `boolean`

How to write it as function:

```lua
local shallow = FWB.Table.Contains(tbl, value)
local deep = FWB.Table.TableContains(tbl, value)
```

How to write it as export:

```lua
local deep = exports['fs_bridge']:TableContains(tbl, value)
```

Example as function:

```lua
local shallow = FWB.Table.Contains({ 'water', 'bread' }, 'water')
local deep = FWB.Table.TableContains({ items = { 'water' } }, 'water')
```

Example as export:

```lua
local deep = exports['fs_bridge']:TableContains({ items = { 'water' } }, 'water')
```

</details>

<details>
<summary><strong>Dump(value) / SizeOf(tbl) / Length(tbl) / Count(tbl)</strong></summary>

Short description: Dump a table to text or count its keys.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `any` | Value or table for `Dump` |
| `tbl` | `table` | Table for count helpers |

Returns:

- `string` for `Dump`
- `number` for count helpers

How to write it as function:

```lua
local dumped = FWB.Table.Dump(value)
local count = FWB.Table.SizeOf(tbl)
local count2 = FWB.Table.Length(tbl)
local count3 = FWB.Table.Count(tbl)
```

How to write it as export:

```lua
local dumped = exports['fs_bridge']:DumpTable(value)
local count = exports['fs_bridge']:TableSizeOf(tbl)
local count2 = exports['fs_bridge']:TableLength(tbl)
local count3 = exports['fs_bridge']:TableCount(tbl)
```

Example as function:

```lua
print(FWB.Table.Dump({ label = 'Water', amount = 2 }))
print(FWB.Table.Count({ one = true, two = true }))
```

Example as export:

```lua
print(exports['fs_bridge']:DumpTable({ label = 'Water', amount = 2 }))
print(exports['fs_bridge']:TableCount({ one = true, two = true }))
```

</details>

<details>
<summary><strong>Find(tbl, predicate) / Keys(tbl) / Values(tbl)</strong></summary>

Short description: Find one matching value or read the keys and values of a table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Target table |
| `predicate` | `function` | Match callback for `Find` |

Returns:

- value and key for `Find`
- key array for `Keys`
- value array for `Values`

How to write it as function:

```lua
local foundValue, foundKey = FWB.Table.Find(tbl, predicate)
local keys = FWB.Table.Keys(tbl)
local values = FWB.Table.Values(tbl)
```

How to write it as export:

```lua
local foundValue, foundKey = exports['fs_bridge']:FindInTable(tbl, predicate)
local keys = exports['fs_bridge']:GetTableKeys(tbl)
local values = exports['fs_bridge']:GetTableValues(tbl)
```

Example as function:

```lua
local value = FWB.Table.Find({
    { name = 'water', count = 2 },
    { name = 'bread', count = 1 }
}, function(row)
    return row.name == 'water'
end)
```

Example as export:

```lua
local keys = exports['fs_bridge']:GetTableKeys({ police = 2, ambulance = 1 })
local values = exports['fs_bridge']:GetTableValues({ police = 2, ambulance = 1 })
```

</details>

<details>
<summary><strong>Copy(tbl) / ShallowCopy(tbl) / DeepCopy(tbl) / Merge(target, source, deep)</strong></summary>

Short description: Copy or merge tables through the Bridge utility namespace.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |
| `target` | `table` | Merge target |
| `source` | `table` | Merge source |
| `deep` | `boolean` | Optional deep merge flag |

Returns:

- copied or merged table

How to write it as function:

```lua
local copy = FWB.Table.Copy(tbl)
local shallow = FWB.Table.ShallowCopy(tbl)
local deepCopy = FWB.Table.DeepCopy(tbl)
local merged = FWB.Table.Merge(target, source, deep)
```

How to write it as export:

```lua
local copy = exports['fs_bridge']:CopyTable(tbl)
local deepCopy = exports['fs_bridge']:DeepCopyTable(tbl)
local merged = exports['fs_bridge']:MergeTables(target, source, deep)
```

Example as function:

```lua
local merged = FWB.Table.Merge({
    fuel = 50
}, {
    locked = true
}, true)
```

Example as export:

```lua
local merged = exports['fs_bridge']:MergeTables({
    fuel = 50
}, {
    locked = true
}, true)
```

</details>

<details>
<summary><strong>IsArray(tbl) / Map(tbl, mapper) / Filter(tbl, predicate) / Join(tbl, separator) / Sort(tbl, comparer)</strong></summary>

Short description: Run common collection helpers on a table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |
| `mapper` | `function` | Mapper callback for `Map` |
| `predicate` | `function` | Predicate callback for `Filter` |
| `separator` | `string` | Optional separator for `Join` |
| `comparer` | `function` | Optional sort callback for `Sort` |

Returns:

- `boolean` for `IsArray`
- transformed table for `Map`, `Filter`, and `Sort`
- `string` for `Join`

How to write it as function:

```lua
local isArray = FWB.Table.IsArray(tbl)
local mapped = FWB.Table.Map(tbl, mapper)
local filtered = FWB.Table.Filter(tbl, predicate)
local joined = FWB.Table.Join(tbl, separator)
local sorted = FWB.Table.Sort(tbl, comparer)
```

How to write it as export:

```lua
local isArray = exports['fs_bridge']:TableIsArray(tbl)
local mapped = exports['fs_bridge']:MapTable(tbl, mapper)
local filtered = exports['fs_bridge']:FilterTable(tbl, predicate)
local joined = exports['fs_bridge']:JoinTable(tbl, separator)
local sorted = exports['fs_bridge']:SortTable(tbl, comparer)
```

Example as function:

```lua
local joined = FWB.Table.Join({ 'police', 'ambulance', 'mechanic' }, ', ')
local sorted = FWB.Table.Sort({ 3, 1, 2 })
```

Example as export:

```lua
local joined = exports['fs_bridge']:JoinTable({ 'police', 'ambulance', 'mechanic' }, ', ')
local sorted = exports['fs_bridge']:SortTable({ 3, 1, 2 })
```

</details>

## FWB.Math

<details>
<summary><strong>Round(num, decimalPlaces) / Random(minRange, maxRange)</strong></summary>

Short description: Use Bridge math helpers for rounding and simple random number generation.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `num` | `number` | Input number for `Round` |
| `decimalPlaces` | `number` | Optional decimal precision |
| `minRange` | `number` | Optional minimum random value |
| `maxRange` | `number` | Optional maximum random value |

Returns:

- rounded number for `Round`
- random number for `Random`

How to write it as function:

```lua
local rounded = FWB.Math.Round(num, decimalPlaces)
local randomValue = FWB.Math.Random(minRange, maxRange)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local rounded = FWB.Math.Round(12.3456, 2)
local randomValue = FWB.Math.Random(1, 10)
print(rounded, randomValue)
```

</details>

## Language Helper

<details>
<summary><strong>Lang()</strong></summary>

Short description: Read the currently active Bridge language key.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` language key such as `en`

How to write it as function:

```lua
local language = FWB.Lang()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local language = FWB.Lang()
print(language)
```

</details>

## Version Helpers

<details>
<summary><strong>GetResourceServerVersion(resource) / GetResourceServerVersionString(resource)</strong></summary>

Short description: Read numeric or raw version values from a resource `fxmanifest` version field on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Resource name to inspect |

Returns:

- numeric version for `GetResourceServerVersion`
- raw version string for `GetResourceServerVersionString`
- `0` when version metadata is missing or invalid

How to write it as function:

```lua
local version = FWB.GetResourceServerVersion(resource)
local versionText = FWB.GetResourceServerVersionString(resource)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local version = FWB.GetResourceServerVersion('fs_bridge')
local versionText = FWB.GetResourceServerVersionString('fs_bridge')
print(version, versionText)
```

</details>

<details>
<summary><strong>GetResourceGithubVersion(resource) / GetResourceGithubVersionString(resource) / HasLatestVersion(resource)</strong></summary>

Short description: Read the latest release version for a resource and compare it with the installed server version.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Resource name to inspect |

Returns:

- numeric repo version for `GetResourceGithubVersion`
- raw repo version string for `GetResourceGithubVersionString`
- `boolean` for `HasLatestVersion`

How to write it as function:

```lua
local repoVersion = FWB.GetResourceGithubVersion(resource)
local repoVersionText = FWB.GetResourceGithubVersionString(resource)
local upToDate = FWB.HasLatestVersion(resource)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local repoVersion = FWB.GetResourceGithubVersion('fs_bridge')
local repoVersionText = FWB.GetResourceGithubVersionString('fs_bridge')
local upToDate = FWB.HasLatestVersion('fs_bridge')
print(repoVersion, repoVersionText, upToDate)
```

</details>
