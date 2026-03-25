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
# Client

This page documents the public client-side Player API.

Vehicle and clothing namespaces are documented on their own pages so this page stays focused on player, job, status, and request helpers.

## FWB.Player

### Player

<details>
<summary><strong>Is Loaded</strong></summary>

Short description: Check whether the local player is fully loaded in the active framework.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `boolean`

How to write it as function:

```lua
local loaded = FWB.Player.IsLoaded()
```

How to write it as export:

```lua
local loaded = exports['fs_bridge']:IsPlayerLoaded()
```

Example as function:

```lua
if not FWB.Player.IsLoaded() then return end
print('Player ready')
```

Example as export:

```lua
if exports['fs_bridge']:IsPlayerLoaded() then
    print('Player ready')
end
```

</details>

<details>
<summary><strong>Player Data</strong></summary>

Short description: Read the full local player data table from the active framework.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table` player data
- `false` when player data is not ready yet

How to write it as function:

```lua
local playerData = FWB.Player.Data()
```

How to write it as export:

```lua
local playerData = exports['fs_bridge']:GetPlayerData()
```

Example as function:

```lua
local playerData = FWB.Player.Data()
if playerData then
    print(playerData)
end
```

Example as export:

```lua
local playerData = exports['fs_bridge']:GetPlayerData()
if playerData then
    print(playerData)
end
```

</details>

<details>
<summary><strong>Character Id</strong></summary>

Short description: Read the current local character identifier.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local characterId = FWB.Player.CharacterId()
```

How to write it as export:

```lua
local characterId = exports['fs_bridge']:GetPlayerIdentifier()
```

Example as function:

```lua
print(FWB.Player.CharacterId())
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerIdentifier())
```

</details>

<details>
<summary><strong>Player Name</strong></summary>

Short description: Read the local player name, or pass a target player source to request another player's display name through Bridge callback routing.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Optional target player source. Leave empty to read the local player name |

Returns:

- `string`
- fallback source value when the remote name lookup fails

How to write it as function:

```lua
local name = FWB.Player.Name(source)
```

How to write it as export:

```lua
local name = exports['fs_bridge']:GetPlayerName(source)
```

Example as function:

```lua
local localName = FWB.Player.Name()
local targetName = FWB.Player.Name(12)
print(localName, targetName)
```

Example as export:

```lua
local localName = exports['fs_bridge']:GetPlayerName()
local targetName = exports['fs_bridge']:GetPlayerName(12)
print(localName, targetName)
```

</details>

<details>
<summary><strong>Salary</strong></summary>

Short description: Read the current local job salary or payment value.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `number`
- `nil` when unavailable

How to write it as function:

```lua
local salary = FWB.Player.Salary()
```

How to write it as export:

```lua
local salary = exports['fs_bridge']:GetPlayerSalary()
```

Example as function:

```lua
print(FWB.Player.Salary())
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerSalary())
```

</details>

<details>
<summary><strong>Is Boss</strong></summary>

Short description: Check whether the local player is a boss in the current active job.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `boolean`

How to write it as function:

```lua
local isBoss = FWB.Player.IsBoss()
```

How to write it as export:

```lua
local isBoss = exports['fs_bridge']:IsPlayerBoss()
```

Example as function:

```lua
if FWB.Player.IsBoss() then
    print('Boss menu allowed')
end
```

Example as export:

```lua
if exports['fs_bridge']:IsPlayerBoss() then
    print('Boss menu allowed')
end
```

</details>

### Job

<details>
<summary><strong>Job Data</strong></summary>

Short description: Read the active local player job data table in Bridge format.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `table`
- `nil` when unavailable

How to write it as function:

```lua
local jobData = FWB.Player.Job.Data()
```

How to write it as export:

```lua
local jobData = exports['fs_bridge']:GetPlayerJobData()
```

Example as function:

```lua
local jobData = FWB.Player.Job.Data()
if jobData then
    print(jobData.name, jobData.grade.level)
end
```

Example as export:

```lua
local jobData = exports['fs_bridge']:GetPlayerJobData()
if jobData then
    print(jobData.name, jobData.grade.level)
end
```

</details>

<details>
<summary><strong>Job Name</strong></summary>

Short description: Read the active local player job name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local jobName = FWB.Player.Job.Name()
```

How to write it as export:

```lua
local jobName = exports['fs_bridge']:GetPlayerJob()
```

Example as function:

```lua
print(FWB.Player.Job.Name())
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerJob())
```

</details>

<details>
<summary><strong>Job Label</strong></summary>

Short description: Read the active local player job label.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local jobLabel = FWB.Player.Job.Label()
```

How to write it as export:

```lua
local jobLabel = exports['fs_bridge']:GetPlayerJobLabel()
```

Example as function:

```lua
print(FWB.Player.Job.Label())
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerJobLabel())
```

</details>

<details>
<summary><strong>Job Grade Label</strong></summary>

Short description: Read the active local player job grade label.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local gradeLabel = FWB.Player.Job.GradeLabel()
```

How to write it as export:

```lua
local gradeLabel = exports['fs_bridge']:GetPlayerJobGradeLabel()
```

Example as function:

```lua
print(FWB.Player.Job.GradeLabel())
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerJobGradeLabel())
```

</details>

<details>
<summary><strong>Job Grade Level</strong></summary>

Short description: Read the active local player job grade level.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `number`
- `nil` when unavailable

How to write it as function:

```lua
local gradeLevel = FWB.Player.Job.GradeLevel()
```

How to write it as export:

```lua
local gradeLevel = exports['fs_bridge']:GetPlayerJobGradeLevel()
```

Example as function:

```lua
print(FWB.Player.Job.GradeLevel())
```

Example as export:

```lua
print(exports['fs_bridge']:GetPlayerJobGradeLevel())
```

</details>

### Status

<details>
<summary><strong>Add Hunger</strong></summary>

Short description: Increase the local player hunger value through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current hunger value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Hunger.Add(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddHunger(value)
```

Example as function:

```lua
FWB.Player.Hunger.Add(10)
```

Example as export:

```lua
exports['fs_bridge']:AddHunger(10)
```

</details>

<details>
<summary><strong>Remove Hunger</strong></summary>

Short description: Decrease the local player hunger value through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current hunger value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Hunger.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveHunger(value)
```

Example as function:

```lua
FWB.Player.Hunger.Remove(15)
```

Example as export:

```lua
exports['fs_bridge']:RemoveHunger(15)
```

</details>

<details>
<summary><strong>Add Thirst</strong></summary>

Short description: Increase the local player thirst value through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current thirst value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Thirst.Add(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddThirst(value)
```

Example as function:

```lua
FWB.Player.Thirst.Add(10)
```

Example as export:

```lua
exports['fs_bridge']:AddThirst(10)
```

</details>

<details>
<summary><strong>Remove Thirst</strong></summary>

Short description: Decrease the local player thirst value through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current thirst value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Thirst.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveThirst(value)
```

Example as function:

```lua
FWB.Player.Thirst.Remove(10)
```

Example as export:

```lua
exports['fs_bridge']:RemoveThirst(10)
```

</details>

<details>
<summary><strong>Add Stress</strong></summary>

Short description: Increase the local player stress value through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current stress value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Stress.Add(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddStress(value)
```

Example as function:

```lua
FWB.Player.Stress.Add(5)
```

Example as export:

```lua
exports['fs_bridge']:AddStress(5)
```

</details>

<details>
<summary><strong>Remove Stress</strong></summary>

Short description: Decrease the local player stress value through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current stress value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Stress.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveStress(value)
```

Example as function:

```lua
FWB.Player.Stress.Remove(5)
```

Example as export:

```lua
exports['fs_bridge']:RemoveStress(5)
```

</details>

<details>
<summary><strong>Add Health</strong></summary>

Short description: Increase the local player health value through the active Bridge-compatible health handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Numeric health value added to the current health state |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Health.Add(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddHealth(value)
```

Example as function:

```lua
FWB.Player.Health.Add(25)
```

Example as export:

```lua
exports['fs_bridge']:AddHealth(25)
```

</details>

<details>
<summary><strong>Remove Health</strong></summary>

Short description: Decrease the local player health value through the active Bridge-compatible health handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Numeric health value removed from the current health state |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Health.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveHealth(value)
```

Example as function:

```lua
FWB.Player.Health.Remove(10)
```

Example as export:

```lua
exports['fs_bridge']:RemoveHealth(10)
```

</details>

<details>
<summary><strong>Add Armour</strong></summary>

Short description: Increase the local player armour value through the active Bridge-compatible armour handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current armour value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Armour.Add(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddArmour(value)
```

Example as function:

```lua
FWB.Player.Armour.Add(20)
```

Example as export:

```lua
exports['fs_bridge']:AddArmour(20)
```

</details>

<details>
<summary><strong>Remove Armour</strong></summary>

Short description: Decrease the local player armour value through the active Bridge-compatible armour handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Percentage-style change from `1` to `100` on the current armour value |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Armour.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:RemoveArmour(value)
```

Example as function:

```lua
FWB.Player.Armour.Remove(10)
```

Example as export:

```lua
exports['fs_bridge']:RemoveArmour(10)
```

</details>

### Request

<details>
<summary><strong>Request Anim Dict</strong></summary>

Short description: Load an animation dictionary before using it on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `dict` | `string` | Animation dictionary name when using the short form |
| `timeout` | `number` | Optional timeout in milliseconds when using the short form |
| `options.dict` | `string` | Required animation dictionary name when using the table form |
| `options.timeout` | `number` | Optional timeout in milliseconds. Defaults to `10000` |
| `options.silent` | `boolean` | Set `true` to suppress Bridge failure prints |
| `options.keepLoaded` | `boolean` | Set `false` to unload the dict after a successful request |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Request.AnimDict(dictOrOptions, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestAnimDict(dictOrOptions, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.AnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000,
    keepLoaded = true
})
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestAnimDict('amb@world_human_stand_mobile@male@text@enter', 5000)
```

</details>

<details>
<summary><strong>Request Model</strong></summary>

Short description: Load a model before using it on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `model` | `string|number` | Model name or hash when using the short form |
| `timeout` | `number` | Optional timeout in milliseconds when using the short form |
| `options.model` | `string|number` | Required model name or hash when using the table form |
| `options.timeout` | `number` | Optional timeout in milliseconds. Defaults to `10000` |
| `options.silent` | `boolean` | Set `true` to suppress Bridge failure prints |
| `options.keepLoaded` | `boolean` | Set `false` to unload the model after a successful request |
| `options.requireValid` | `boolean` | Set `false` to skip the Bridge valid-model check |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Request.Model(modelOrOptions, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestModel(modelOrOptions, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.Model({
    model = `adder`,
    timeout = 5000,
    requireValid = true
})
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestModel('adder', 5000)
```

</details>

<details>
<summary><strong>Request Anim Set</strong></summary>

Short description: Load an animation set before applying it to the player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `animSet` | `string` | Animation set name when using the short form |
| `timeout` | `number` | Optional timeout in milliseconds when using the short form |
| `options.animSet` | `string` | Required animation set name when using the table form |
| `options.timeout` | `number` | Optional timeout in milliseconds. Defaults to `10000` |
| `options.silent` | `boolean` | Set `true` to suppress Bridge failure prints |
| `options.keepLoaded` | `boolean` | Set `false` to unload the anim set after a successful request |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Request.AnimSet(animSetOrOptions, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestAnimSet(animSetOrOptions, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.AnimSet({
    animSet = 'move_m@drunk@slightlydrunk',
    keepLoaded = true
})
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestAnimSet('move_m@drunk@slightlydrunk', 5000)
```

</details>

<details>
<summary><strong>Request Clip Set</strong></summary>

Short description: Load a clip set before applying it to the player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `clipSet` | `string` | Clip set name when using the short form |
| `timeout` | `number` | Optional timeout in milliseconds when using the short form |
| `options.clipSet` | `string` | Required clip set name when using the table form |
| `options.timeout` | `number` | Optional timeout in milliseconds. Defaults to `10000` |
| `options.silent` | `boolean` | Set `true` to suppress Bridge failure prints |
| `options.keepLoaded` | `boolean` | Set `false` to unload the clip set after a successful request |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Request.ClipSet(clipSetOrOptions, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestClipSet(clipSetOrOptions, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.ClipSet({
    clipSet = 'move_ped_crouched',
    keepLoaded = true
})
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestClipSet('move_ped_crouched', 5000)
```

</details>

<details>
<summary><strong>Request Named Ptfx Asset</strong></summary>

Short description: Load a named particle asset before using it on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `asset` | `string` | Asset name when using the short form |
| `timeout` | `number` | Optional timeout in milliseconds when using the short form |
| `options.asset` | `string` | Required asset name when using the table form |
| `options.timeout` | `number` | Optional timeout in milliseconds. Defaults to `10000` |
| `options.silent` | `boolean` | Set `true` to suppress Bridge failure prints |
| `options.keepLoaded` | `boolean` | Set `false` to unload the asset after a successful request |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Request.NamedPtfxAsset(assetOrOptions, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestNamedPtfxAsset(assetOrOptions, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.NamedPtfxAsset({
    asset = 'core',
    keepLoaded = true
})
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestNamedPtfxAsset('core', 5000)
```

</details>

<details>
<summary><strong>Request Weapon Asset</strong></summary>

Short description: Load a weapon asset before using it on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `weapon` | `string|number` | Weapon name or hash when using the short form |
| `timeout` | `number` | Optional timeout in milliseconds when using the short form |
| `options.weapon` | `string|number` | Required weapon name or hash when using the table form |
| `options.timeout` | `number` | Optional timeout in milliseconds. Defaults to `10000` |
| `options.silent` | `boolean` | Set `true` to suppress Bridge failure prints |
| `options.keepLoaded` | `boolean` | Set `false` to unload the weapon asset after a successful request |
| `options.weaponRequestFlags` | `number` | Optional weapon request flags. Defaults to `31` |
| `options.ammoType` | `number` | Optional ammo type. Defaults to `0` |

Returns:

- `boolean` success

How to write it as function:

```lua
local ok = FWB.Player.Request.WeaponAsset(weaponOrOptions, timeout)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RequestWeaponAsset(weaponOrOptions, timeout)
```

Example as function:

```lua
local ok = FWB.Player.Request.WeaponAsset({
    weapon = `WEAPON_PISTOL`,
    weaponRequestFlags = 31,
    ammoType = 0
})
```

Example as export:

```lua
local ok = exports['fs_bridge']:RequestWeaponAsset(`WEAPON_PISTOL`, 5000)
```

</details>