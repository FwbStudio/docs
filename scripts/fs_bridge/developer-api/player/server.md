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

It includes player state, player job helpers, job listing helpers, and the server-side request compatibility helpers that are exposed publicly.
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
