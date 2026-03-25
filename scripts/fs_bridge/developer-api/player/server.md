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
# Server

This page documents the public server-side Player API.

It includes player lookups, money helpers, permissions, character deletion helpers, job helpers, and the current server-side request compatibility calls.

## FWB.Player

### Player

<details>
<summary><strong>Get Player</strong></summary>

Short description: Read the framework player object by source id or by character identifier.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `sourceOrCharacterId` | `number|string` | Pass a player source number or a character identifier string |

Returns:

- framework player object
- `nil` when unavailable

How to write it as function:

```lua
local player = FWB.Player.Get(sourceOrCharacterId)
```

How to write it as export:

```lua
local player = exports['fs_bridge']:GetPlayer(sourceOrCharacterId)
```

Example as function:

```lua
local onlinePlayer = FWB.Player.Get(source)
local byCharacterId = FWB.Player.Get('char1:identifier')
print(onlinePlayer, byCharacterId)
```

Example as export:

```lua
local onlinePlayer = exports['fs_bridge']:GetPlayer(source)
local byCharacterId = exports['fs_bridge']:GetPlayer('char1:identifier')
print(onlinePlayer, byCharacterId)
```

</details>

<details>
<summary><strong>Get Online Players</strong></summary>

Short description: Read the current online player list from the active framework.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- player list table

How to write it as function:

```lua
local players = FWB.GetPlayers()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local players = FWB.GetPlayers()
print(players)
```

</details>

<details>
<summary><strong>Character Id</strong></summary>

Short description: Read the character identifier for an online player source.

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
<summary><strong>Player Name</strong></summary>

Short description: Read a player name from an online source or from a character identifier.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `sourceOrCharacterId` | `number|string` | Pass an online player source or a character identifier string |

Returns:

- `string`
- empty string when unavailable

How to write it as function:

```lua
local name = FWB.Player.Name(sourceOrCharacterId)
```

How to write it as export:

```lua
local name = exports['fs_bridge']:GetPlayerName(sourceOrCharacterId)
```

Example as function:

```lua
local onlineName = FWB.Player.Name(source)
local offlineName = FWB.Player.Name('char1:identifier')
print(onlineName, offlineName)
```

Example as export:

```lua
local onlineName = exports['fs_bridge']:GetPlayerName(source)
local offlineName = exports['fs_bridge']:GetPlayerName('char1:identifier')
print(onlineName, offlineName)
```

</details>

<details>
<summary><strong>Is Boss</strong></summary>

Short description: Check whether a player is a boss in the active job.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `boolean`

How to write it as function:

```lua
local isBoss = FWB.Player.IsBoss(source)
```

How to write it as export:

```lua
local isBoss = exports['fs_bridge']:IsPlayerBoss(source)
```

Example as function:

```lua
if FWB.Player.IsBoss(source) then
    print('Boss menu allowed')
end
```

Example as export:

```lua
if exports['fs_bridge']:IsPlayerBoss(source) then
    print('Boss menu allowed')
end
```

</details>

### Cash / Money

<details>
<summary><strong>Get Money</strong></summary>

Short description: Read the current player cash or money balance.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `number`
- `nil` when unavailable

How to write it as function:

```lua
local money = FWB.Player.GetMoney(source)
```

How to write it as export:

```lua
local money = exports['fs_bridge']:GetPlayerMoney(source)
```

Example as function:

```lua
print(FWB.Player.GetMoney(source))
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerMoney(source))
```

</details>

<details>
<summary><strong>Add Money</strong></summary>

Short description: Add cash or money to a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `amount` | `number` | Money amount to add |

Returns:

- nothing

How to write it as function:

```lua
FWB.Player.AddMoney(source, amount)
```

How to write it as export:

```lua
exports['fs_bridge']:AddPlayerMoney(source, amount)
```

Example as function:

```lua
FWB.Player.AddMoney(source, 500)
```

Example as export:

```lua
exports['fs_bridge']:AddPlayerMoney(source, 500)
```

</details>

<details>
<summary><strong>Remove Money</strong></summary>

Short description: Remove cash or money from a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `amount` | `number` | Money amount to remove |

Returns:

- nothing

How to write it as function:

```lua
FWB.Player.RemoveMoney(source, amount)
```

How to write it as export:

```lua
exports['fs_bridge']:RemovePlayerMoney(source, amount)
```

Example as function:

```lua
FWB.Player.RemoveMoney(source, 250)
```

Example as export:

```lua
exports['fs_bridge']:RemovePlayerMoney(source, 250)
```

</details>

### Bank

<details>
<summary><strong>Get Bank Money</strong></summary>

Short description: Read the current player bank balance.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `number`
- `nil` when unavailable

How to write it as function:

```lua
local bankMoney = FWB.Player.GetBankMoney(source)
```

How to write it as export:

```lua
local bankMoney = exports['fs_bridge']:GetBankMoney(source)
```

Example as function:

```lua
print(FWB.Player.GetBankMoney(source))
```

Example as export:

```lua
print(exports['fs_bridge']:GetBankMoney(source))
```

</details>

<details>
<summary><strong>Add Bank Money</strong></summary>

Short description: Add bank money to a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `amount` | `number` | Bank amount to add |

Returns:

- nothing

How to write it as function:

```lua
FWB.Player.AddBankMoney(source, amount)
```

How to write it as export:

```lua
exports['fs_bridge']:AddBankMoney(source, amount)
```

Example as function:

```lua
FWB.Player.AddBankMoney(source, 500)
```

Example as export:

```lua
exports['fs_bridge']:AddBankMoney(source, 500)
```

</details>

<details>
<summary><strong>Remove Bank Money</strong></summary>

Short description: Remove bank money from a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `amount` | `number` | Bank amount to remove |

Returns:

- nothing

How to write it as function:

```lua
FWB.Player.RemoveBankMoney(source, amount)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveBankMoney(source, amount)
```

Example as function:

```lua
FWB.Player.RemoveBankMoney(source, 250)
```

Example as export:

```lua
exports['fs_bridge']:RemoveBankMoney(source, 250)
```

</details>

### Society

Bridge society money helpers are part of the Banking namespace, not `FWB.Player`. They should be documented under banking-focused API pages, not under the Player object itself.

### Duty

<details>
<summary><strong>Toggle Duty</strong></summary>

Short description: Toggle the current duty state for a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- framework-specific result
- `nil` when unavailable

How to write it as function:

```lua
FWB.Player.ToggleDuty(source)
```

How to write it as export:

```lua
exports['fs_bridge']:TogglePlayerDuty(source)
```

Example as function:

```lua
FWB.Player.ToggleDuty(source)
```

Example as export:

```lua
exports['fs_bridge']:TogglePlayerDuty(source)
```

</details>

<details>
<summary><strong>Is On Duty</strong></summary>

Short description: Check whether a player is currently on duty.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `boolean`

How to write it as function:

```lua
local onDuty = FWB.Player.IsOnDuty(source)
```

How to write it as export:

```lua
local onDuty = exports['fs_bridge']:IsPlayerOnDuty(source)
```

Example as function:

```lua
print(FWB.Player.IsOnDuty(source))
```

Example as export:

```lua
print(exports['fs_bridge']:IsPlayerOnDuty(source))
```

</details>

### Permissions

<details>
<summary><strong>Check Permissions</strong></summary>

Short description: Check a player against a Bridge permissions table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `permissions` | `table` | Supports checks such as `admingroups`, `aces`, `identifiers`, `characters`, and `jobgroups` |

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

### Player Detail By CharacterId

<details>
<summary><strong>Get Player Detail</strong></summary>

Short description: Read player detail data for an offline character identifier.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `characterId` | `string` | Character identifier string |

Returns:

- detail table
- empty table or `nil` when unavailable

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
print(detail)
```

Example as export:

```lua
local detail = exports['fs_bridge']:GetPlayerDetail('char1:identifier')
print(detail)
```

</details>

### Character Delete

<details>
<summary><strong>Delete Online Character By Source</strong></summary>

Short description: Delete the online character data for a source and drop that player after the delete completes.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Online player source |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Online_CK_By_Source(source)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:CKOnlineCharacterBySource(source)
```

Example as function:

```lua
local ok = FWB.Player.Online_CK_By_Source(source)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:CKOnlineCharacterBySource(source)
print(ok)
```

</details>

<details>
<summary><strong>Delete Offline Character By CharacterId</strong></summary>

Short description: Delete one offline character by character identifier.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `characterId` | `string` | Character identifier |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Offline_CK_By_CharacterId(characterId)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:CKOfflineCharacterByCharacterId(characterId)
```

Example as function:

```lua
local ok = FWB.Player.Offline_CK_By_CharacterId('char1:identifier')
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:CKOfflineCharacterByCharacterId('char1:identifier')
print(ok)
```

</details>

<details>
<summary><strong>Delete All Offline Characters By Identifier</strong></summary>

Short description: Delete all offline characters that belong to one base identifier.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `identifier` | `string` | Base identifier without the character prefix where your framework uses one |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Offline_Ck_All_Characters_By_Identifier(identifier)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:CKAllOfflineCharactersByIdentifier(identifier)
```

Example as function:

```lua
local ok = FWB.Player.Offline_Ck_All_Characters_By_Identifier('license:123456789')
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:CKAllOfflineCharactersByIdentifier('license:123456789')
print(ok)
```

</details>

### Job

<details>
<summary><strong>Job Data</strong></summary>

Short description: Read the active job data for a player in Bridge format.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `table`
- `nil` when unavailable

How to write it as function:

```lua
local jobData = FWB.Player.Job.Data(source)
```

How to write it as export:

```lua
local jobData = exports['fs_bridge']:GetPlayerJobData(source)
```

Example as function:

```lua
local jobData = FWB.Player.Job.Data(source)
print(jobData)
```

Example as export:

```lua
local jobData = exports['fs_bridge']:GetPlayerJobData(source)
print(jobData)
```

</details>

<details>
<summary><strong>Job Name</strong></summary>

Short description: Read the active job name for a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local jobName = FWB.Player.Job.Name(source)
```

How to write it as export:

```lua
local jobName = exports['fs_bridge']:GetPlayerJobName(source)
```

Example as function:

```lua
print(FWB.Player.Job.Name(source))
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerJobName(source))
```

</details>

<details>
<summary><strong>Job Grade</strong></summary>

Short description: Read the active job grade level for a player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |

Returns:

- `number`
- `nil` when unavailable

How to write it as function:

```lua
local gradeLevel = FWB.Player.Job.GradeLevel(source)
```

How to write it as export:

```lua
local gradeLevel = exports['fs_bridge']:GetPlayerJobGradeLevel(source)
```

Example as function:

```lua
print(FWB.Player.Job.GradeLevel(source))
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerJobGradeLevel(source))
```

</details>

<details>
<summary><strong>Set Job</strong></summary>

Short description: Set a player job through the active framework bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Player source |
| `job` | `string` | Job name |
| `grade` | `number|string` | Job grade |

Returns:

- `boolean` success when the job exists
- `nil` when the framework player is unavailable

How to write it as function:

```lua
local ok = FWB.Player.Job.Set(source, job, grade)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:SetPlayerJob(source, job, grade)
```

Example as function:

```lua
local ok = FWB.Player.Job.Set(source, 'police', 2)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:SetPlayerJob(source, 'police', 2)
print(ok)
```

</details>

## FWB.Job

<details>
<summary><strong>All Jobs</strong></summary>

Short description: Read all job definitions with their grade data.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- jobs table

How to write it as function:

```lua
local jobs = FWB.Job.All()
```

How to write it as export:

```lua
local jobs = exports['fs_bridge']:GetJobs()
```

Example as function:

```lua
local jobs = FWB.Job.All()
print(jobs)
```

Example as export:

```lua
local jobs = exports['fs_bridge']:GetJobs()
print(jobs)
```

</details>

<details>
<summary><strong>Job Player Count</strong></summary>

Short description: Count how many online players are inside one job.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `jobName` | `string` | Job name |

Returns:

- `number`

How to write it as function:

```lua
local count = FWB.Job.PlayerCount(jobName)
```

How to write it as export:

```lua
local count = exports['fs_bridge']:GetJobPlayerCount(jobName)
```

Example as function:

```lua
print(FWB.Job.PlayerCount('police'))
```

Example as export:

```lua
print(exports['fs_bridge']:GetJobPlayerCount('police'))
```

</details>

## FWB.Player.Request

<details>
<summary><strong>Request Anim Dict</strong></summary>

Short description: Server-side request helpers exist for API compatibility only. They do not actually stream assets on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `dict` | `string` | Animation dictionary name |
| `timeout` | `number` | Optional compatibility argument |

Returns:

- `true`

How to write it as function:

```lua
local ok = FWB.Player.Request.AnimDict(dict, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestAnimDict(dict, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.AnimDict('amb@prop_human_bum_bin@base')
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestAnimDict('amb@prop_human_bum_bin@base')
print(ok)
```

</details>

<details>
<summary><strong>Request Model</strong></summary>

Short description: Server-side request helpers exist for API compatibility only. They do not actually stream assets on the server.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `model` | `string|number` | Model name or hash |
| `timeout` | `number` | Optional compatibility argument |

Returns:

- `true`

How to write it as function:

```lua
local ok = FWB.Player.Request.Model(model, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestModel(model, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.Model('adder')
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestModel('adder')
print(ok)
```

</details>