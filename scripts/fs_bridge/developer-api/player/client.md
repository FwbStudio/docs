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
<summary><strong>IsLoaded()</strong></summary>

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
<summary><strong>Data() / CharacterId() / Name() / Salary()</strong></summary>

Short description: Read the main local player information table and common identity values from the current framework bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- player data table, character id, name, or salary depending on the call
- `false` or `nil` when the framework data is not ready yet

How to write it as function:

```lua
local playerData = FWB.Player.Data()
local characterId = FWB.Player.CharacterId()
local name = FWB.Player.Name()
local salary = FWB.Player.Salary()
```

How to write it as export:

```lua
local playerData = exports['fs_bridge']:GetPlayerData()
local characterId = exports['fs_bridge']:GetPlayerIdentifier()
local name = exports['fs_bridge']:GetPlayerName()
local salary = exports['fs_bridge']:GetPlayerSalary()
```

Example as function:

```lua
local playerData = FWB.Player.Data()
if playerData then
    print(FWB.Player.Name(), FWB.Player.CharacterId(), FWB.Player.Salary())
end
```

Example as export:

```lua
local playerData = exports['fs_bridge']:GetPlayerData()
if playerData then
    print(exports['fs_bridge']:GetPlayerName())
end
```

</details>

<details>
<summary><strong>IsBoss()</strong></summary>

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
<summary><strong>Job.Name() / Job.Label() / Job.GradeLabel() / Job.GradeLevel() / Job.Data()</strong></summary>

Short description: Read the active local player job state from Bridge, including the raw job data table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- job name, label, grade label, grade level, or full job data depending on the call
- `nil` when unavailable

How to write it as function:

```lua
local jobName = FWB.Player.Job.Name()
local jobLabel = FWB.Player.Job.Label()
local gradeLabel = FWB.Player.Job.GradeLabel()
local gradeLevel = FWB.Player.Job.GradeLevel()
local jobData = FWB.Player.Job.Data()
```

How to write it as export:

```lua
local jobName = exports['fs_bridge']:GetPlayerJob()
local jobLabel = exports['fs_bridge']:GetPlayerJobLabel()
local gradeLabel = exports['fs_bridge']:GetPlayerJobGradeLabel()
local gradeLevel = exports['fs_bridge']:GetPlayerJobGradeLevel()
local jobData = exports['fs_bridge']:GetPlayerJobData()
```

Example as function:

```lua
local jobData = FWB.Player.Job.Data()
if jobData then
    print(FWB.Player.Job.Name(), FWB.Player.Job.GradeLevel())
end
```

Example as export:

```lua
local jobData = exports['fs_bridge']:GetPlayerJobData()
if jobData then
    print(exports['fs_bridge']:GetPlayerJob())
end
```

</details>

### Status

<details>
<summary><strong>Hunger.Add(value) / Hunger.Remove(value)</strong></summary>

Short description: Increase or decrease the local player's hunger through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Numeric `1-100` percentage-style change on the current hunger status |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Hunger.Add(value)
FWB.Player.Hunger.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddHunger(value)
exports['fs_bridge']:RemoveHunger(value)
```

Example as function:

```lua
FWB.Player.Hunger.Add(10)
FWB.Player.Hunger.Remove(15)
```

Example as export:

```lua
exports['fs_bridge']:AddHunger(10)
exports['fs_bridge']:RemoveHunger(15)
```

</details>

<details>
<summary><strong>Thirst.Add(value) / Thirst.Remove(value)</strong></summary>

Short description: Increase or decrease the local player's thirst through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Numeric `1-100` percentage-style change on the current thirst status |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Thirst.Add(value)
FWB.Player.Thirst.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddThirst(value)
exports['fs_bridge']:RemoveThirst(value)
```

Example as function:

```lua
FWB.Player.Thirst.Add(10)
FWB.Player.Thirst.Remove(10)
```

Example as export:

```lua
exports['fs_bridge']:AddThirst(10)
exports['fs_bridge']:RemoveThirst(10)
```

</details>

<details>
<summary><strong>Stress.Add(value) / Stress.Remove(value)</strong></summary>

Short description: Increase or decrease the local player's stress through the active Bridge-compatible status handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Numeric `1-100` percentage-style change on the current stress status |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Stress.Add(value)
FWB.Player.Stress.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddStress(value)
exports['fs_bridge']:RemoveStress(value)
```

Example as function:

```lua
FWB.Player.Stress.Add(5)
FWB.Player.Stress.Remove(5)
```

Example as export:

```lua
exports['fs_bridge']:AddStress(5)
exports['fs_bridge']:RemoveStress(5)
```

</details>

<details>
<summary><strong>Health.Add(value) / Health.Remove(value)</strong></summary>

Short description: Increase or decrease the local player's health through the active Bridge-compatible health handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Numeric health value applied to the current health state |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Health.Add(value)
FWB.Player.Health.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddHealth(value)
exports['fs_bridge']:RemoveHealth(value)
```

Example as function:

```lua
FWB.Player.Health.Add(25)
FWB.Player.Health.Remove(10)
```

Example as export:

```lua
exports['fs_bridge']:AddHealth(25)
exports['fs_bridge']:RemoveHealth(10)
```

</details>

<details>
<summary><strong>Armour.Add(value) / Armour.Remove(value)</strong></summary>

Short description: Increase or decrease the local player's armour through the active Bridge-compatible armour handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Numeric `1-100` percentage-style change on the current armour |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Armour.Add(value)
FWB.Player.Armour.Remove(value)
```

How to write it as export:

```lua
exports['fs_bridge']:AddArmour(value)
exports['fs_bridge']:RemoveArmour(value)
```

Example as function:

```lua
FWB.Player.Armour.Add(20)
FWB.Player.Armour.Remove(10)
```

Example as export:

```lua
exports['fs_bridge']:AddArmour(20)
exports['fs_bridge']:RemoveArmour(10)
```

</details>


### Request

<details>
<summary><strong>Request.AnimDict(dict, timeout) / Request.Model(model, timeout)</strong></summary>

Short description: Load an animation dictionary or model before using it on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `dict` | `string|table` | Dict name or an extras table with `dict`, `timeout`, `silent`, and `keepLoaded` |
| `model` | `string|number|table` | Model name, hash, or an extras table with `model`, `timeout`, `silent`, `keepLoaded`, and `requireValid` |
| `timeout` | `number` | Optional timeout when you use the short form |

Returns:

- `boolean` success

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
FWB.Player.Request.AnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000
})

FWB.Player.Request.Model({
    model = `adder`,
    timeout = 5000
})
```

Example as export:

```lua
exports['fs_bridge']:RequestAnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter'
})

exports['fs_bridge']:RequestModel({
    model = `adder`
})
```

Notes:

- Default timeout is `10000` ms.
- Use `keepLoaded = false` when you want Bridge to release the asset after a successful load.

</details>

<details>
<summary><strong>Request.AnimSet(animSet, timeout) / Request.ClipSet(clipSet, timeout)</strong></summary>

Short description: Load a movement set or clip set before applying it to the local ped.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `animSet` | `string|table` | Anim set name or an extras table with `animSet`, `timeout`, `silent`, and `keepLoaded` |
| `clipSet` | `string|table` | Clip set name or an extras table with `clipSet`, `timeout`, `silent`, and `keepLoaded` |
| `timeout` | `number` | Optional timeout when you use the short form |

Returns:

- `boolean` success

How to write it as function:

```lua
local okAnimSet = FWB.Player.Request.AnimSet(animSet, timeout)
local okClipSet = FWB.Player.Request.ClipSet(clipSet, timeout)
```

How to write it as export:

```lua
local okAnimSet = exports['fs_bridge']:RequestAnimSet(animSet, timeout)
local okClipSet = exports['fs_bridge']:RequestClipSet(clipSet, timeout)
```

Example as function:

```lua
FWB.Player.Request.AnimSet({ animSet = 'move_m@drunk@slightlydrunk' })
FWB.Player.Request.ClipSet({ clipSet = 'move_ped_crouched' })
```

Example as export:

```lua
exports['fs_bridge']:RequestAnimSet({ animSet = 'move_m@drunk@slightlydrunk' })
exports['fs_bridge']:RequestClipSet({ clipSet = 'move_ped_crouched' })
```

</details>

<details>
<summary><strong>Request.NamedPtfxAsset(asset, timeout) / Request.WeaponAsset(weapon, timeout)</strong></summary>

Short description: Load a particle asset or weapon asset before using it on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `asset` | `string|table` | Asset name or an extras table with `asset`, `timeout`, `silent`, and `keepLoaded` |
| `weapon` | `string|number|table` | Weapon name, hash, or an extras table with `weapon`, `timeout`, `silent`, `keepLoaded`, `weaponRequestFlags`, and `ammoType` |
| `timeout` | `number` | Optional timeout when you use the short form |

Returns:

- `boolean` success

How to write it as function:

```lua
local okPtfx = FWB.Player.Request.NamedPtfxAsset(asset, timeout)
local okWeapon = FWB.Player.Request.WeaponAsset(weapon, timeout)
```

How to write it as export:

```lua
local okPtfx = exports['fs_bridge']:RequestNamedPtfxAsset(asset, timeout)
local okWeapon = exports['fs_bridge']:RequestWeaponAsset(weapon, timeout)
```

Example as function:

```lua
FWB.Player.Request.NamedPtfxAsset({ asset = 'core' })
FWB.Player.Request.WeaponAsset({ weapon = `WEAPON_PISTOL` })
```

Example as export:

```lua
exports['fs_bridge']:RequestNamedPtfxAsset({ asset = 'core' })
exports['fs_bridge']:RequestWeaponAsset({ weapon = `WEAPON_PISTOL` })
```

</details>
