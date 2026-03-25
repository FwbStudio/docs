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

# Client API

This page documents the current public client-side Bridge API from the live `fs_bridge` build.

Function-style examples assume you first get the Bridge object:

```lua
local FWB = exports['fs_bridge']:GetObject()
```

Deprecated globals and internal helper paths are intentionally skipped here. This page focuses on the clean public surface and direct exports that are available in the current client runtime.

## Access

<details>
<summary><strong>GetObject()</strong></summary>

Short description: Get the shared Bridge object so you can call namespaced helpers like `FWB.Player`, `FWB.Vehicle`, `FWB.Blip`, and the rest of the public runtime.

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

if FWB.Player.IsLoaded() then
    print('Bridge object ready')
end
```

Notes:

- Use this once at the top of your client file when you prefer the function-style API.

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
local ped = exports['fs_bridge']:Cache('Ped')
local playerJob = exports['fs_bridge']:Cache('fs_bridge', 'fs_bridge_playerjob')
```

Example as export:

```lua
local ped = exports['fs_bridge']:Cache('Ped')
local coords = exports['fs_bridge']:Cache('Coords')
```

Notes:

- Client cache exposes protected keys like `Ped`, `Coords`, `Vehicle`, `Playerid`, `Serverid`, and `fs_bridge_playerjob`.

</details>

## FWB.CB

<details>
<summary><strong>Await(eventName, ...)</strong></summary>

Short description: Trigger a registered server callback and wait for the return values on the client.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Registered callback name |
| `...` | `any` | Optional payload passed through to the callback |

Returns:

- one or more callback return values
- `nil` when the callback returns nothing

How to write it as function:

```lua
local result = FWB.CB.Await(eventName, ...)
```

How to write it as export:

```lua
local result = exports['fs_bridge']:AwaitCallback(eventName, ...)
```

Example as function:

```lua
local vehicleLabel = FWB.CB.Await('garage:getLabel', 'ABC123')
```

Example as export:

```lua
local vehicleLabel = exports['fs_bridge']:AwaitCallback('garage:getLabel', 'ABC123')
```

Notes:

- Client callback waits up to roughly 15 seconds before timing out.

</details>

<details>
<summary><strong>Register(eventName, callback)</strong></summary>

Short description: Register a client callback that can be triggered from the server through Bridge callback routing.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `eventName` | `string` | Callback name to register |
| `callback` | `function` | Lua function that returns one or more values |

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
FWB.CB.Register('garage:clientCanOpen', function(plate)
    return plate == 'ABC123'
end)
```

Example as export:

```lua
exports['fs_bridge']:RegisterCallback('garage:clientCanOpen', function(plate)
    return plate == 'ABC123'
end)
```

Notes:

- The callback can return one or more values back to the server.

</details>

<details>
<summary><strong>DoesRegistered(name)</strong></summary>

Short description: Check whether a server callback is currently registered and reachable through Bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `name` | `string` | Callback name to check |

Returns:

- `boolean`

How to write it as function:

```lua
local exists = FWB.CB.DoesRegistered(name)
```

How to write it as export:

```lua
local exists = exports['fs_bridge']:DoesServerCallbackRegistered(name)
```

Example as function:

```lua
local exists = FWB.CB.DoesRegistered('garage:getLabel')
```

Example as export:

```lua
local exists = exports['fs_bridge']:DoesServerCallbackRegistered('garage:getLabel')
```

Notes:

- This checks the server-side callback registry from the client.

</details>

## FWB.Notify

<details>
<summary><strong>Notify(argument)</strong></summary>

Short description: Send a Bridge notification through the currently selected notification resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `argument` | `string|table` | Accepts a plain string or a table with keys like `title`, `description`, `type`, `position`, and `duration` |

Returns:

- resource-specific notification result
- `nil`

How to write it as function:

```lua
FWB.Notify(argument)
```

How to write it as export:

```lua
exports['fs_bridge']:Notify(argument)
```

Example as function:

```lua
FWB.Notify({
    title = 'Garage',
    description = 'Vehicle stored successfully.',
    type = 'success'
})
```

Example as export:

```lua
exports['fs_bridge']:Notify({
    description = 'Vehicle stored successfully.',
    type = 'success'
})
```

Notes:

- A plain string is automatically normalized into `{ description = string }`.

</details>

## FWB.TextUi

<details>
<summary><strong>Show(text, options)</strong></summary>

Short description: Show the configured text UI with the current Bridge-compatible provider.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `text` | `string` | Main text shown in the UI |
| `options` | `table` | Optional table with keys like `type`, `position`, `icon`, `iconColor`, and `iconAnimation` |

Returns:

- resource-specific text UI result
- `nil`

How to write it as function:

```lua
FWB.TextUi.Show(text, options)
```

How to write it as export:

```lua
exports['fs_bridge']:ShowTextUi(text, options)
```

Example as function:

```lua
FWB.TextUi.Show('Press [E] to interact', {
    type = 'inform',
    position = 'right-center'
})
```

Example as export:

```lua
exports['fs_bridge']:ShowTextUi('Press [E] to interact', {
    type = 'success',
    icon = 'fa-solid fa-car'
})
```

Notes:

- Bridge normalizes the default `type` to `inform` and default `position` to `right-center`.

</details>

<details>
<summary><strong>Hide()</strong></summary>

Short description: Hide the current Bridge text UI.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- resource-specific text UI result
- `nil`

How to write it as function:

```lua
FWB.TextUi.Hide()
```

How to write it as export:

```lua
exports['fs_bridge']:HideTextUi()
```

Example as function:

```lua
FWB.TextUi.Hide()
```

Example as export:

```lua
exports['fs_bridge']:HideTextUi()
```

</details>

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

### Clothes

<details>
<summary><strong>Clothes.GetNative() / Clothes.SetNative(clothes)</strong></summary>

Short description: Read or apply the local player native clothing table through Bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `clothes` | `table` | Clothing table that matches the Bridge native skin shape for `SetNative` |

Returns:

- `table` clothing table for `GetNative`
- nothing or `false` for `SetNative`

How to write it as function:

```lua
local clothes = FWB.Player.Clothes.GetNative()
FWB.Player.Clothes.SetNative(clothes)
```

How to write it as export:

```lua
local clothes = exports['fs_bridge']:GetPedCurrentNativeSkin()
exports['fs_bridge']:SetPedCurrentNativeSkin(clothes)
```

Example as function:

```lua
local clothes = FWB.Player.Clothes.GetNative()
FWB.Player.Clothes.SetNative({
    torso_1 = { drawable = 15, texture = 0, palette = 0 }
})
```

Example as export:

```lua
local clothes = exports['fs_bridge']:GetPedCurrentNativeSkin()
exports['fs_bridge']:SetPedCurrentNativeSkin(clothes)
```

Notes:

- The direct export also accepts an explicit ped argument when you need it.

</details>

<details>
<summary><strong>Clothes.Reset() / Clothes.Save()</strong></summary>

Short description: Reset the current script skin or save the current script skin through the active clothing resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- resource-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Clothes.Reset()
FWB.Player.Clothes.Save()
```

How to write it as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
exports['fs_bridge']:SavePedCurrentScriptSkin()
```

Example as function:

```lua
FWB.Player.Clothes.Reset()
FWB.Player.Clothes.Save()
```

Example as export:

```lua
exports['fs_bridge']:ResetPedCurrentScriptSkin()
exports['fs_bridge']:SavePedCurrentScriptSkin()
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

### Vehicle

<details>
<summary><strong>Vehicle.NearBy(extras) / Vehicle.Closest(extras)</strong></summary>

Short description: Search nearby vehicles around the local player through the player-scoped vehicle helpers.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `maxDistance`, `maxCount`, or `includePlayerVehicle` |

Returns:

- nearby vehicle entries or one closest vehicle entry

How to write it as function:

```lua
local vehicles = FWB.Player.Vehicle.NearBy(extras)
local vehicle = FWB.Player.Vehicle.Closest(extras)
```

How to write it as export:

```lua
local vehicles = exports['fs_bridge']:GetPlayerNearbyVehicles(extras)
local vehicle = exports['fs_bridge']:GetPlayerClosestVehicle(extras)
```

Example as function:

```lua
local vehicles = FWB.Player.Vehicle.NearBy({ maxDistance = 12.0 })
local vehicle = FWB.Player.Vehicle.Closest({ maxDistance = 8.0 })
```

Example as export:

```lua
local vehicles = exports['fs_bridge']:GetPlayerNearbyVehicles({ maxDistance = 12.0 })
local vehicle = exports['fs_bridge']:GetPlayerClosestVehicle({ maxDistance = 8.0 })
```

</details>

## FWB.Player.Vehicle.Keys

<details>
<summary><strong>Give(vehicle) / Remove(vehicle)</strong></summary>

Short description: Give or remove vehicle keys for the local player through the active key system resolver.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |

Returns:

- resource-specific result
- `nil`

How to write it as function:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)
```

How to write it as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(vehicle)
```

Example as function:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)
```

Example as export:

```lua
exports['fs_bridge']:GiveCarKeyPlayer(vehicle)
exports['fs_bridge']:RemoveCarKeyPlayer(vehicle)
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
- `nil` when nothing is active

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

## FWB.Ambulance

<details>
<summary><strong>ResourceName()</strong></summary>

Short description: Get the detected ambulance resource name for the current build.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` resource name
- `nil` when unavailable

How to write it as function:

```lua
local resourceName = FWB.Ambulance.ResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetAmbulanceResourceName()
```

Example as function:

```lua
print(FWB.Ambulance.ResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetAmbulanceResourceName())
```

</details>

<details>
<summary><strong>IsPlayerDowned(source?) / IsPlayerDead(source?)</strong></summary>

Short description: Check whether the local player, or another player when you pass `source`, is currently downed or dead.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Optional player source when you want to check another player |

Returns:

- `boolean`

How to write it as function:

```lua
local downed = FWB.Ambulance.IsPlayerDowned(source)
local dead = FWB.Ambulance.IsPlayerDead(source)
```

How to write it as export:

```lua
local downed = exports['fs_bridge']:IsPlayerDowned(source)
local dead = exports['fs_bridge']:IsPlayerDead(source)
```

Example as function:

```lua
local downed = FWB.Ambulance.IsPlayerDowned()
local dead = FWB.Ambulance.IsPlayerDead()
```

Example as export:

```lua
local downed = exports['fs_bridge']:IsPlayerDowned()
local dead = exports['fs_bridge']:IsPlayerDead()
```

</details>

## FWB.Banking

<details>
<summary><strong>ResourceName() / OpenBossMenu(job)</strong></summary>

Short description: Read the active banking resource name or open a boss menu through the banking compatibility layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `job` | `string` | Job name used for `OpenBossMenu(job)` |

Returns:

- resource name for `ResourceName()`
- resource-specific result or `nil` for `OpenBossMenu(job)`

How to write it as function:

```lua
local resourceName = FWB.Banking.ResourceName()
FWB.Banking.OpenBossMenu(job)
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetBankResourceName()
exports['fs_bridge']:OpenBossMenu(job)
```

Example as function:

```lua
print(FWB.Banking.ResourceName())
FWB.Banking.OpenBossMenu('police')
```

Example as export:

```lua
print(exports['fs_bridge']:GetBankResourceName())
exports['fs_bridge']:OpenBossMenu('police')
```

</details>

## FWB.Dispatch

<details>
<summary><strong>Generate(argument) / ResourceName()</strong></summary>

Short description: Create a dispatch alert through the active dispatch layer and read the detected dispatch resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `argument` | `table` | Dispatch payload with `Job`, `Location`, `CallCode`, `Message`, `Flashes`, `Image`, `icon`, and `Blip` |

Returns:

- dispatch resource result or `nil`
- dispatch resource name for `ResourceName()`

How to write it as function:

```lua
FWB.Dispatch.Generate(argument)
local resourceName = FWB.Dispatch.ResourceName()
```

How to write it as export:

```lua
exports['fs_bridge']:AddCustomDispatch(argument)
local resourceName = exports['fs_bridge']:GetDispatchResourceName()
```

Example as function:

```lua
FWB.Dispatch.Generate({
    Job = { 'police' },
    Location = GetEntityCoords(PlayerPedId()),
    Message = 'Suspicious activity reported.'
})
```

Example as export:

```lua
exports['fs_bridge']:AddCustomDispatch({
    Job = { 'police' },
    Location = GetEntityCoords(PlayerPedId()),
    Message = 'Suspicious activity reported.'
})
```

</details>

## FWB.Vehicle.Fuel

<details>
<summary><strong>Set(vehicle, value) / Get(vehicle) / ResourceName()</strong></summary>

Short description: Set fuel, read fuel, or read the detected fuel resource name through Bridge.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |
| `value` | `number` | Fuel value, defaults to `100.0` when omitted |

Returns:

- resource-specific result for `Set`
- `number` fuel value for `Get`
- `string` resource name for `ResourceName()`

How to write it as function:

```lua
FWB.Vehicle.Fuel.Set(vehicle, value)
local fuel = FWB.Vehicle.Fuel.Get(vehicle)
local resourceName = FWB.Vehicle.Fuel.ResourceName()
```

How to write it as export:

```lua
exports['fs_bridge']:SetFuel(vehicle, value)
local fuel = exports['fs_bridge']:GetFuel(vehicle)
local resourceName = exports['fs_bridge']:GetFuelResourceName()
```

Example as function:

```lua
FWB.Vehicle.Fuel.Set(vehicle, 75.0)
print(FWB.Vehicle.Fuel.Get(vehicle))
```

Example as export:

```lua
exports['fs_bridge']:SetFuel(vehicle, 75.0)
print(exports['fs_bridge']:GetFuel(vehicle))
```

</details>

## FWB.Clothes

<details>
<summary><strong>ResourceName()</strong></summary>

Short description: Get the detected clothing resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` resource name
- `nil` when nothing is active

How to write it as function:

```lua
local resourceName = FWB.Clothes.ResourceName()
```

How to write it as export:

```lua
local resourceName = exports['fs_bridge']:GetClothingResourceName()
```

Example as function:

```lua
print(FWB.Clothes.ResourceName())
```

Example as export:

```lua
print(exports['fs_bridge']:GetClothingResourceName())
```

</details>

## FWB.Blip

<details>
<summary><strong>Create(options)</strong></summary>

Short description: Create a static blip entry in the Bridge blip runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Blip options table |

Common option keys:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Coordinates for the blip |
| `handle` | `string` | Optional custom handle |
| `title` | `string` | Blip label |
| `id` | `number` | Sprite id |
| `scale` | `number` | Blip scale |
| `color` | `number` | Blip color |
| `route` | `boolean` | Draw GPS route |
| `radius` | `number` | Optional radius zone |
| `shortRange` | `boolean` | Toggle short-range behavior |
| `time` | `number` | Auto-remove duration in milliseconds |

Returns:

- `string` handle
- `table` entry

How to write it as function:

```lua
local handle, entry = FWB.Blip.Create(options)
```

How to write it as export:

```lua
local handle, entry = exports['fs_bridge']:CreateBlip(options)
```

Example as function:

```lua
local handle = FWB.Blip.Create({
    coords = vec3(215.76, -810.12, 30.73),
    title = 'Garage',
    id = 357,
    color = 3
})
```

Example as export:

```lua
local handle = exports['fs_bridge']:CreateBlip({
    coords = vec3(215.76, -810.12, 30.73),
    title = 'Garage',
    id = 357,
    color = 3
})
```

</details>

<details>
<summary><strong>CreateMoving(options)</strong></summary>

Short description: Create a moving blip that tracks a player, entity, net id, or fallback coordinates.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Moving blip options table |

Common option keys:

| Key | Type | Notes |
|---|---|---|
| `entity` | `number` | Track an entity |
| `player` | `number` | Track a local player id |
| `serverId` | `number` | Track a server id on client |
| `netId` | `number` | Track a network id |
| `updateTime` | `number` | Minimum `5000` ms |
| `title` | `string` | Blip label |
| `id` | `number` | Sprite id |

Returns:

- `string` handle
- `table` entry

How to write it as function:

```lua
local handle, entry = FWB.Blip.CreateMoving(options)
```

How to write it as export:

```lua
local handle, entry = exports['fs_bridge']:CreateMovingBlip(options)
```

Example as function:

```lua
local handle = FWB.Blip.CreateMoving({
    entity = vehicle,
    title = 'Tracked Vehicle',
    id = 225,
    updateTime = 5000
})
```

Example as export:

```lua
local handle = exports['fs_bridge']:CreateMovingBlip({
    entity = vehicle,
    title = 'Tracked Vehicle',
    id = 225,
    updateTime = 5000
})
```

</details>

<details>
<summary><strong>Update(handleOrNative, updates)</strong></summary>

Short description: Update an existing blip entry with new options.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrNative` | `string|number` | Bridge handle or native blip id |
| `updates` | `table` | Partial updates table |

Returns:

- `string` handle
- `table` updated entry
- `nil` when not found

How to write it as function:

```lua
local handle, entry = FWB.Blip.Update(handleOrNative, updates)
```

How to write it as export:

```lua
local handle, entry = exports['fs_bridge']:UpdateBlip(handleOrNative, updates)
```

Example as function:

```lua
FWB.Blip.Update(handle, {
    title = 'Garage Updated',
    color = 5,
    route = true
})
```

Example as export:

```lua
exports['fs_bridge']:UpdateBlip(handle, {
    title = 'Garage Updated',
    color = 5,
    route = true
})
```

</details>

<details>
<summary><strong>Toggle(handleOrNative, enabled)</strong></summary>

Short description: Toggle a blip on or off without deleting the stored Bridge record.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrNative` | `string|number` | Bridge handle or native blip id |
| `enabled` | `boolean` | Toggle state; omit to invert the current state |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.Blip.Toggle(handleOrNative, enabled)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:ToggleBlip(handleOrNative, enabled)
```

Example as function:

```lua
FWB.Blip.Toggle(handle, false)
```

Example as export:

```lua
exports['fs_bridge']:ToggleBlip(handle, false)
```

</details>

<details>
<summary><strong>Remove(handleOrNative)</strong></summary>

Short description: Remove a blip from the Bridge runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrNative` | `string|number` | Bridge handle or native blip id |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.Blip.Remove(handleOrNative)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RemoveBlip(handleOrNative)
```

Example as function:

```lua
FWB.Blip.Remove(handle)
```

Example as export:

```lua
exports['fs_bridge']:RemoveBlip(handle)
```

</details>

<details>
<summary><strong>Get(handleOrNative)</strong></summary>

Short description: Read one blip entry from the Bridge runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrNative` | `string|number` | Bridge handle or native blip id |

Returns:

- `table`
- `nil` when not found

How to write it as function:

```lua
local entry = FWB.Blip.Get(handleOrNative)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:GetBlip(handleOrNative)
```

Example as function:

```lua
local entry = FWB.Blip.Get(handle)
```

Example as export:

```lua
local entry = exports['fs_bridge']:GetBlip(handle)
```

</details>

<details>
<summary><strong>GetAll() / Clear(resource)</strong></summary>

Short description: Read all blip entries or clear entries for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Optional resource name when clearing |

Returns:

- `table` of all entries for `GetAll()`
- clear result or `nil` for `Clear(resource)`

How to write it as function:

```lua
local allBlips = FWB.Blip.GetAll()
FWB.Blip.Clear(resource)
```

How to write it as export:

```lua
local allBlips = exports['fs_bridge']:GetAllBlips()
exports['fs_bridge']:ClearBlips(resource)
```

Example as function:

```lua
local allBlips = FWB.Blip.GetAll()
FWB.Blip.Clear(GetCurrentResourceName())
```

Example as export:

```lua
local allBlips = exports['fs_bridge']:GetAllBlips()
exports['fs_bridge']:ClearBlips(GetCurrentResourceName())
```

</details>

## FWB.Entity

<details>
<summary><strong>Object.Nearby(extras) / Object.Closest(extras)</strong></summary>

Short description: Find nearby world objects with optional distance and model filtering.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `coords`, `ped`, `model`, `models`, `excludeModels`, `maxDistance`, and `maxCount` |

Returns:

- object entry table list for `Nearby`
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
    maxDistance = 3.0,
    model = `prop_atm_01`
})
```

Example as export:

```lua
local object = exports['fs_bridge']:GetClosestObject({
    maxDistance = 3.0,
    model = `prop_atm_01`
})
```

</details>

<details>
<summary><strong>Player.Nearby(extras) / Player.Closest(extras)</strong></summary>

Short description: Find nearby player entries for checks or interactions.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `maxDistance`, `selfInclude`, `maxCount`, and `requireClearLos` |

Returns:

- player entry table list for `Nearby`
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
    maxDistance = 2.5,
    selfInclude = false
})
```

Example as export:

```lua
local player = exports['fs_bridge']:GetClosestPlayer({
    maxDistance = 2.5,
    selfInclude = false
})
```

</details>

<details>
<summary><strong>Ped.Nearby(extras) / Ped.Closest(extras)</strong></summary>

Short description: Find nearby non-player peds with optional filtering.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `maxDistance`, `includeMissionPeds`, `aliveOnly`, `model`, `models`, and `excludeModels` |

Returns:

- ped entry table list for `Nearby`
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
    maxDistance = 5.0,
    aliveOnly = true
})
```

Example as export:

```lua
local ped = exports['fs_bridge']:GetClosestPed({
    maxDistance = 5.0,
    aliveOnly = true
})
```

</details>

<details>
<summary><strong>Vehicle.Nearby(extras) / Vehicle.Closest(extras)</strong></summary>

Short description: Find nearby vehicle entries with optional distance and model filtering.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `table` | Optional filters like `maxDistance`, `includePlayerVehicle`, `model`, `models`, and `excludeModels` |

Returns:

- vehicle entry table list for `Nearby`
- one vehicle entry for `Closest`

How to write it as function:

```lua
local vehicles = FWB.Entity.Vehicle.Nearby(extras)
local vehicle = FWB.Entity.Vehicle.Closest(extras)
```

How to write it as export:

- No separate direct export is documented for this helper on client side.
- In the current live build, the direct `GetNearbyVehicles` and `GetClosestVehicle` export names are owned by `FWB.Vehicle`.

Example as function:

```lua
local vehicle = FWB.Entity.Vehicle.Closest({
    maxDistance = 8.0,
    includePlayerVehicle = false
})
```

</details>

<details>
<summary><strong>GetFrontCoords(extras) / FrontCoords(extras)</strong></summary>

Short description: Get a point directly in front of a ped or heading.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `extras` | `number|table` | Number shorthand for distance, or a table with `distance`, `verticalOffset`, `ped`, `coords`, and `heading` |

Returns:

- `vector3`

How to write it as function:

```lua
local frontCoords = FWB.Player.GetFrontCoords(extras)
local frontCoords2 = FWB.Entity.GetFrontCoords(extras)
local frontCoords3 = FWB.Entity.FrontCoords(extras)
```

How to write it as export:

```lua
local frontCoords = exports['fs_bridge']:GetFrontCoords(extras)
```

Example as function:

```lua
local frontCoords = FWB.Player.GetFrontCoords({
    distance = 2.0,
    verticalOffset = -0.7
})
```

Example as export:

```lua
local frontCoords = exports['fs_bridge']:GetFrontCoords({
    distance = 2.0,
    verticalOffset = -0.7
})
```

</details>

## FWB.Ped

<details>
<summary><strong>Create(options)</strong></summary>

Short description: Spawn a client-managed ped and register it in the Bridge ped runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `options` | `table` | Ped creation options table |

Common option keys:

| Key | Type | Notes |
|---|---|---|
| `model` | `string|number` | Ped model, defaults to `a_m_m_business_01` |
| `coords` | `vector4|vector3|table` | Spawn location |
| `heading` | `number` | Optional heading override |
| `freeze` | `boolean` | Freeze ped in place |
| `invincible` | `boolean` | Make ped invincible |
| `blockEvents` | `boolean` | Ignore ambient events |
| `health` | `number` | Apply health |
| `armour` | `number` | Apply armour |
| `weapon` | `string|number|false` | Give a weapon or remove all weapons |
| `ammo` | `number` | Weapon ammo |
| `combat` | `table` | Combat behavior options |
| `attachments` | `table` | Attached object options |
| `target` | `table` | Local target options |
| `point` | `table` | Interaction point options |
| `blip` | `table|true` | Optional blip payload |
| `animation` | `table` | Animation dict/clip payload |
| `scenario` | `string` | Scenario name |
| `speech` | `string|table` | Ambient speech or lines |

Returns:

- `string` handle
- `number` net id
- `number` ped entity handle

How to write it as function:

```lua
local handle, netId, ped = FWB.Ped.Create(options)
```

How to write it as export:

```lua
local handle, netId, ped = exports['fs_bridge']:CreatePed(options)
```

Example as function:

```lua
local handle, netId, ped = FWB.Ped.Create({
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true,
    invincible = true,
    blip = { title = 'Guard', id = 280 }
})
```

Example as export:

```lua
local handle, netId, ped = exports['fs_bridge']:CreatePed({
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true,
    invincible = true
})
```

</details>

<details>
<summary><strong>Update(handle, updates)</strong></summary>

Short description: Update a client-managed ped entry, recreating it when the model or ped type changes.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Bridge ped handle |
| `updates` | `table` | Partial updates table |

Returns:

- `boolean` success
- updated entry table

How to write it as function:

```lua
local success, entry = FWB.Ped.Update(handle, updates)
```

How to write it as export:

```lua
local success, entry = exports['fs_bridge']:UpdatePed(handle, updates)
```

Example as function:

```lua
FWB.Ped.Update(handle, {
    freeze = false,
    coords = vec4(450.0, -980.0, 30.7, 180.0)
})
```

Example as export:

```lua
exports['fs_bridge']:UpdatePed(handle, {
    freeze = false,
    coords = vec4(450.0, -980.0, 30.7, 180.0)
})
```

</details>

<details>
<summary><strong>Remove(handle)</strong></summary>

Short description: Remove a client-managed ped from the Bridge runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Bridge ped handle |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.Ped.Remove(handle)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:RemovePed(handle)
```

Example as function:

```lua
FWB.Ped.Remove(handle)
```

Example as export:

```lua
exports['fs_bridge']:RemovePed(handle)
```

</details>

<details>
<summary><strong>Get(handle) / GetAll() / Clear(resource)</strong></summary>

Short description: Read one ped entry, read all ped entries, or clear ped entries for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handle` | `string` | Bridge ped handle for `Get(handle)` |
| `resource` | `string` | Optional resource name for `Clear(resource)` |

Returns:

- one ped entry for `Get(handle)`
- all ped entries for `GetAll()`
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

Short description: Generate a vehicle plate through the Bridge runtime callback.

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
<summary><strong>Props.Get(vehicle) / Props.Set(vehicle, properties)</strong></summary>

Short description: Read or apply vehicle properties through the active framework core implementation.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity handle |
| `properties` | `table` | Vehicle properties table for `Props.Set` |

Returns:

- props table for `Props.Get`
- boolean or framework-specific result for `Props.Set`

How to write it as function:

```lua
local props = FWB.Vehicle.Props.Get(vehicle)
local ok = FWB.Vehicle.Props.Set(vehicle, properties)
```

How to write it as export:

```lua
local props = exports['fs_bridge']:GetVehicleProperties(vehicle)
local ok = exports['fs_bridge']:SetVehicleProperties(vehicle, properties)
```

Example as function:

```lua
local props = FWB.Vehicle.Props.Get(vehicle)
props.modEngine = 2
FWB.Vehicle.Props.Set(vehicle, props)
```

Example as export:

```lua
local props = exports['fs_bridge']:GetVehicleProperties(vehicle)
props.modEngine = 2
exports['fs_bridge']:SetVehicleProperties(vehicle, props)
```

</details>

<details>
<summary><strong>LabelByModel(model) / LabelByEntity(entity)</strong></summary>

Short description: Read a vehicle display label from a model or a spawned entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `model` | `string|number` | Vehicle model name or hash |
| `entity` | `number` | Vehicle entity handle |

Returns:

- `string`
- `nil` when unavailable

How to write it as function:

```lua
local label = FWB.Vehicle.LabelByModel(model)
local label2 = FWB.Vehicle.LabelByEntity(entity)
```

How to write it as export:

```lua
local label = exports['fs_bridge']:GetVehicleLabelByModel(model)
local label2 = exports['fs_bridge']:GetVehicleLabelByEntity(entity)
```

Example as function:

```lua
print(FWB.Vehicle.LabelByModel('adder'))
print(FWB.Vehicle.LabelByEntity(vehicle))
```

Example as export:

```lua
print(exports['fs_bridge']:GetVehicleLabelByModel('adder'))
print(exports['fs_bridge']:GetVehicleLabelByEntity(vehicle))
```

</details>

<details>
<summary><strong>GetByPlate(plate) / FromPlate(plate)</strong></summary>

Short description: Find a spawned client vehicle by plate.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `plate` | `string` | Vehicle plate text |

Returns:

- vehicle entity handle
- `nil` when not found

How to write it as function:

```lua
local vehicle = FWB.Vehicle.GetByPlate(plate)
local vehicle2 = FWB.Vehicle.FromPlate(plate)
```

How to write it as export:

```lua
local vehicle = exports['fs_bridge']:GetVehicleByPlate(plate)
local vehicle2 = exports['fs_bridge']:GetVehicleFromPlate(plate)
```

Example as function:

```lua
local vehicle = FWB.Vehicle.FromPlate('ABC123')
```

Example as export:

```lua
local vehicle = exports['fs_bridge']:GetVehicleFromPlate('ABC123')
```

</details>

<details>
<summary><strong>Nearby(coords, extras) / Closest(coords, extras)</strong></summary>

Short description: Find nearby vehicles around coordinates or return the closest match.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3|vector4|table` | Optional search coordinates |
| `extras` | `table` | Optional filters like `maxDistance`, `model`, `includePlayerVehicle`, and `maxCount` |

Returns:

- nearby vehicle entry table list for `Nearby`
- closest vehicle entity handle for `Closest`

How to write it as function:

```lua
local vehicles = FWB.Vehicle.Nearby(coords, extras)
local vehicle = FWB.Vehicle.Closest(coords, extras)
```

How to write it as export:

```lua
local vehicles = exports['fs_bridge']:GetNearbyVehicles(coords, extras)
local vehicle = exports['fs_bridge']:GetClosestVehicle(coords, extras)
```

Example as function:

```lua
local vehicles = FWB.Vehicle.Nearby(GetEntityCoords(PlayerPedId()), { maxDistance = 10.0 })
local vehicle = FWB.Vehicle.Closest(GetEntityCoords(PlayerPedId()), { maxDistance = 8.0 })
```

Example as export:

```lua
local vehicles = exports['fs_bridge']:GetNearbyVehicles(GetEntityCoords(PlayerPedId()), { maxDistance = 10.0 })
local vehicle = exports['fs_bridge']:GetClosestVehicle(GetEntityCoords(PlayerPedId()), { maxDistance = 8.0 })
```

</details>

<details>
<summary><strong>Create(spawnSource, model, options)</strong></summary>

Short description: Spawn and register a client-managed vehicle entry.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `spawnSource` | `number|vector3|vector4|nil` | Player ped, coordinates, or omit to use the local player |
| `model` | `string|number` | Vehicle model |
| `options` | `table` | Vehicle creation options table |

Returns:

- entry table

How to write it as function:

```lua
local entry = FWB.Vehicle.Create(spawnSource, model, options)
```

How to write it as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(spawnSource, model, options)
```

Example as function:

```lua
local entry = FWB.Vehicle.Create(nil, 'adder', {
    warp = true,
    plate = FWB.Vehicle.GeneratePlate(),
    fuel = 80.0,
    keys = true
})
```

Example as export:

```lua
local entry = exports['fs_bridge']:CreateVehicle(nil, 'adder', {
    warp = true,
    plate = exports['fs_bridge']:GenerateVehiclePlate(),
    fuel = 80.0,
    keys = true
})
```

</details>

<details>
<summary><strong>Update(handleOrEntry, updates) / Remove(handleOrEntry)</strong></summary>

Short description: Update a client-managed vehicle entry or remove it from the Bridge runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `handleOrEntry` | `string|number|table` | Bridge handle, entity, net id, or entry table |
| `updates` | `table` | Partial updates table for `Update` |

Returns:

- success and updated entry for `Update`
- boolean for `Remove`

How to write it as function:

```lua
local success, entry = FWB.Vehicle.Update(handleOrEntry, updates)
local ok = FWB.Vehicle.Remove(handleOrEntry)
```

How to write it as export:

```lua
local success, entry = exports['fs_bridge']:UpdateVehicle(handleOrEntry, updates)
local ok = exports['fs_bridge']:RemoveVehicle(handleOrEntry)
```

Example as function:

```lua
FWB.Vehicle.Update(entry.handle, {
    fuel = 100.0,
    freeze = true
})
FWB.Vehicle.Remove(entry.handle)
```

Example as export:

```lua
exports['fs_bridge']:UpdateVehicle(entry.handle, {
    fuel = 100.0,
    freeze = true
})
exports['fs_bridge']:RemoveVehicle(entry.handle)
```

</details>

<details>
<summary><strong>Get(handleOrEntry) / GetAll() / Clear(resource)</strong></summary>

Short description: Read one vehicle entry, read all entries, or clear entries for a resource.

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

## FWB.Creator

<details>
<summary><strong>Zone.Polyzone() / Zone.Sphere()</strong></summary>

Short description: Launch the interactive zone creators and return the selected data.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These helpers do not take direct arguments |

Returns:

- `boolean` success
- result table with zone data

How to write it as function:

```lua
local success, polyzone = FWB.Creator.Zone.Polyzone()
local success2, sphere = FWB.Creator.Zone.Sphere()
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local success, polyzone = FWB.Creator.Zone.Polyzone()
if success then
    print(json.encode(polyzone))
end
```

</details>

<details>
<summary><strong>Entity.Ped(args) / Entity.Vehicle(args) / Entity.Object(args)</strong></summary>

Short description: Launch the interactive entity placement helpers for ped, vehicle, or object placement.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `args` | `table` | Optional table with `model`, `keepobject`, `multiple`, and `polyzone` |

Returns:

- `boolean` success
- result table with placement data

How to write it as function:

```lua
local success, data = FWB.Creator.Entity.Ped(args)
local success2, data2 = FWB.Creator.Entity.Vehicle(args)
local success3, data3 = FWB.Creator.Entity.Object(args)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local success, data = FWB.Creator.Entity.Vehicle({
    model = 'adder',
    keepobject = false,
    multiple = false
})
```

</details>

<details>
<summary><strong>Marker.Simple()</strong></summary>

Short description: Launch the interactive marker placement helper.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This helper does not take any arguments |

Returns:

- `boolean` success
- result table with `coords` and `heading`

How to write it as function:

```lua
local success, marker = FWB.Creator.Marker.Simple()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local success, marker = FWB.Creator.Marker.Simple()
if success then
    print(json.encode(marker))
end
```

</details>

## FWB.Points

<details>
<summary><strong>new(data) / new(coords, distance, data)</strong></summary>

Short description: Create a Bridge point helper for enter, exit, and nearby callbacks.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `data` | `table` | Point table with keys like `coords`, `distance`, `nearby`, `onEnter`, and `onExit` |
| `coords` | `vector3` | Shorthand first argument |
| `distance` | `number` | Shorthand point distance |
| `data` | `table` | Optional extra point fields in shorthand mode |

Returns:

- point object table with methods like `remove()`

How to write it as function:

```lua
local point = FWB.Points.new(data)
local point2 = FWB.Points.new(coords, distance, data)
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local point = FWB.Points.new({
    coords = vec3(441.2, -981.9, 30.7),
    distance = 2.0,
    onEnter = function(self)
        print('entered point', self.id)
    end,
    onExit = function(self)
        print('left point', self.id)
    end
})
```

</details>

## FWB.zones

<details>
<summary><strong>poly(data) / box(data) / sphere(data)</strong></summary>

Short description: Create Bridge zones from polygon, box, or sphere data.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `data` | `table` | Zone table with shape-specific fields like `points`, `coords`, `size`, `rotation`, `radius`, `thickness`, `debug`, `inside`, `onEnter`, and `onExit` |

Returns:

- zone object table

How to write it as function:

```lua
local poly = FWB.zones.poly(data)
local box = FWB.zones.box(data)
local sphere = FWB.zones.sphere(data)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local zone = FWB.zones.box({
    coords = vec3(441.2, -981.9, 30.7),
    size = vec3(2.0, 2.0, 4.0),
    rotation = 90.0,
    debug = true
})
```

</details>

<details>
<summary><strong>getAllZones() / getCurrentZones() / getNearbyZones()</strong></summary>

Short description: Read the client-side Bridge zone registries.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- table of all zones
- table of current inside zones
- array of nearby zones

How to write it as function:

```lua
local allZones = FWB.zones.getAllZones()
local currentZones = FWB.zones.getCurrentZones()
local nearbyZones = FWB.zones.getNearbyZones()
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
print(#FWB.zones.getNearbyZones())
```

</details>

## Framework Helper

<details>
<summary><strong>GetFrameworkName()</strong></summary>

Short description: Read the currently detected framework name from the live Bridge client runtime.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` framework name such as `esx`, `qbcore`, or `qbox`

How to write it as function:

```lua
local framework = FWB.GetFrameworkName()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local framework = FWB.GetFrameworkName()
print(framework)
```

</details>

## Inventory Helpers

<details>
<summary><strong>ImagePath()</strong></summary>

Short description: Get the configured item image base path from the active inventory or framework core.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` image base path
- empty string when the active setup does not expose one

How to write it as function:

```lua
local imagePath = FWB.ImagePath()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local imagePath = FWB.ImagePath()
local icon = imagePath .. 'water.png'
```

</details>

<details>
<summary><strong>OpenStash(argument)</strong></summary>

Short description: Open a stash through the active inventory compatibility layer.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `argument` | `table` | Stash payload with required keys like `name`, `label`, `slots`, and `weight` |

Common argument keys:

| Key | Type | Notes |
|---|---|---|
| `name` | `string` | Unique stash id |
| `label` | `string` | UI label |
| `slots` | `number` | Slot count |
| `weight` | `number` | Max weight |
| `coords` | `vector3` | Optional location restriction |
| `jobs` | `table` | Optional job access table |
| `identifier` | `string` | Optional owner character id |

Returns:

- inventory-specific open result
- `nil` when validation or compatibility fails

How to write it as function:

```lua
FWB.OpenStash(argument)
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
FWB.OpenStash({
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

- Use at least one access guard like `coords`, `jobs`, or `identifier`.

</details>

<details>
<summary><strong>OpenShop(argument)</strong></summary>

Short description: Open a shop through the active inventory compatibility layer when the selected provider supports it.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `argument` | `table` | Shop payload with required keys like `name`, `label`, and `items` |

Returns:

- inventory-specific open result
- `nil` when validation or compatibility fails

How to write it as function:

```lua
FWB.OpenShop(argument)
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
FWB.OpenShop({
    name = '24_7_market',
    label = '24/7 Market',
    items = {
        { name = 'water', price = 25, amount = 50 },
        { name = 'bread', price = 30, amount = 50 }
    }
})
```

Notes:

- Availability depends on the selected inventory. Some providers do not implement shop opening through Bridge yet.

</details>

<details>
<summary><strong>GetInventory() / GetServerItems()</strong></summary>

Short description: Read the detected inventory resource name or the cached item definition list exposed by the current setup.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- `string` detected inventory resource name for `GetInventory()`
- item definition table for `GetServerItems()`

How to write it as function:

```lua
local inventoryName = FWB.GetInventory()
local items = FWB.GetServerItems()
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local inventoryName = FWB.GetInventory()
local items = FWB.GetServerItems()

print(inventoryName, items['water'] and items['water'].label)
```

</details>

<details>
<summary><strong>GetItemLabel(item) / ItemExists(item)</strong></summary>

Short description: Read an item label or validate that the current framework or inventory knows about an item.

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
<summary><strong>GetCurrentWeapon() / DisarmWeapon()</strong></summary>

Short description: Read the active weapon state from the selected inventory provider or force a disarm action.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | These functions do not take any arguments |

Returns:

- weapon data table or hash for `GetCurrentWeapon()`
- nothing for `DisarmWeapon()`

How to write it as function:

```lua
local weapon = FWB.GetCurrentWeapon()
FWB.DisarmWeapon()
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local weapon = FWB.GetCurrentWeapon()
if weapon then
    FWB.DisarmWeapon()
end
```

</details>

## Phone Helpers

<details>
<summary><strong>GetPhoneResourceName()</strong></summary>

Short description: Read the currently detected phone resource name from the active client compatibility layer.

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

## Target Helpers

<details>
<summary><strong>LocalTargetModel(parm) / RemoveLocalTargetModel(models, optionNames, optionLabels)</strong></summary>

Short description: Register or remove local target options for one or more models through the active target resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `parm` | `table` | Model target payload with `models` and `options` |
| `models` | `table` | Model list used during registration |
| `optionNames` | `table` | Returned option names used for removal |
| `optionLabels` | `table` | Returned option labels used for removal |

Returns:

- target handle table for `LocalTargetModel(parm)`
- provider-specific removal result for `RemoveLocalTargetModel(...)`

How to write it as function:

```lua
local targetData = FWB.LocalTargetModel(parm)
FWB.RemoveLocalTargetModel(models, optionNames, optionLabels)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local targetData = FWB.LocalTargetModel({
    models = { 'prop_cs_tablet' },
    options = {
        {
            label = 'Use Tablet',
            icon = 'fas fa-tablet-alt',
            clientevent = 'my_resource:useTablet'
        }
    }
})
```

</details>

<details>
<summary><strong>LocalTargetCircle(parm) / RemoveLocalTargetCircle(id)</strong></summary>

Short description: Register or remove a local circle target area.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `parm` | `table` | Circle target payload with `coords`, `radius`, and `options` |
| `id` | `string|number` | Returned zone id for removal |

Returns:

- zone id or provider-specific handle for `LocalTargetCircle(parm)`
- provider-specific removal result for `RemoveLocalTargetCircle(id)`

How to write it as function:

```lua
local id = FWB.LocalTargetCircle(parm)
FWB.RemoveLocalTargetCircle(id)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local id = FWB.LocalTargetCircle({
    coords = vec3(441.2, -981.9, 30.7),
    radius = 2.0,
    options = {
        {
            label = 'Open Locker',
            icon = 'fas fa-box',
            serverevent = 'my_resource:openLocker'
        }
    }
})
```

</details>

<details>
<summary><strong>LocalBonesTarget(parm) / RemoveLocalBonesTarget(entity, name, label, bones)</strong></summary>

Short description: Register or remove bone-specific target options on an entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `parm` | `table` | Bone target payload with `entity`, `bones`, and `options` |
| `entity` | `number` | Target entity |
| `name` | `string|table` | Option name or names |
| `label` | `string|table` | Option label or labels |
| `bones` | `table` | Bone list used during registration |

Returns:

- provider-specific handle table for `LocalBonesTarget(parm)`
- provider-specific removal result for `RemoveLocalBonesTarget(...)`

How to write it as function:

```lua
local result = FWB.LocalBonesTarget(parm)
FWB.RemoveLocalBonesTarget(entity, name, label, bones)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local result = FWB.LocalBonesTarget({
    entity = vehicle,
    bones = { 'door_dside_f', 'door_pside_f' },
    options = {
        {
            label = 'Inspect Door',
            icon = 'fas fa-car-side',
            clientevent = 'my_resource:inspectDoor'
        }
    }
})
```

</details>

<details>
<summary><strong>LocalEntityTarget(parm) / RemoveLocalEntityTarget(param)</strong></summary>

Short description: Register or remove local target options on one entity.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `parm` | `table` | Entity target payload with `entity`, `options`, and optional `distance` |
| `param` | `table` | Removal payload with the returned entity name and option names |

Returns:

- provider-specific handle table for `LocalEntityTarget(parm)`
- provider-specific removal result for `RemoveLocalEntityTarget(param)`

How to write it as function:

```lua
local result = FWB.LocalEntityTarget(parm)
FWB.RemoveLocalEntityTarget(param)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local result = FWB.LocalEntityTarget({
    entity = vehicle,
    options = {
        {
            label = 'Inspect Vehicle',
            icon = 'fas fa-car',
            clientevent = 'my_resource:inspectVehicle'
        }
    }
})
```

</details>

<details>
<summary><strong>LocalSphereZone(param) / RemoveSphereZone(id)</strong></summary>

Short description: Register or remove a local sphere zone target.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `param` | `table` | Sphere payload with `coords`, `radius`, and `options` |
| `id` | `string|number` | Returned zone id |

Returns:

- provider-specific id or handle for `LocalSphereZone(param)`
- provider-specific removal result for `RemoveSphereZone(id)`

How to write it as function:

```lua
local id = FWB.LocalSphereZone(param)
FWB.RemoveSphereZone(id)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local id = FWB.LocalSphereZone({
    coords = vec3(441.2, -981.9, 30.7),
    radius = 1.5,
    options = {
        {
            label = 'Clock In',
            icon = 'fas fa-user-check',
            serverevent = 'my_resource:clockIn'
        }
    }
})
```

</details>

<details>
<summary><strong>GlobalPlayerTarget(arguments) / RemoveGlobalPlayerTarget(optionNames, optionLabels)</strong></summary>

Short description: Register or remove global player target options that apply to every player ped.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `arguments` | `table` | Payload with one or more target options |
| `optionNames` | `table` | Returned option names used for removal |
| `optionLabels` | `table` | Returned option labels used for removal |

Returns:

- provider-specific handle table for `GlobalPlayerTarget(arguments)`
- provider-specific removal result for `RemoveGlobalPlayerTarget(...)`

How to write it as function:

```lua
local result = FWB.GlobalPlayerTarget(arguments)
FWB.RemoveGlobalPlayerTarget(optionNames, optionLabels)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local result = FWB.GlobalPlayerTarget({
    options = {
        {
            label = 'Search Player',
            icon = 'fas fa-user-secret',
            serverevent = 'my_resource:searchPlayer'
        }
    }
})
```

</details>

<details>
<summary><strong>GlobalModelTarget(arguments) / RemoveGlobalModelTarget(model, optionNames, optionLabels)</strong></summary>

Short description: Register or remove global model target options for a specific model.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `arguments` | `table` | Payload with `model` and `options` |
| `model` | `string|number|table` | Model or model list used during registration |
| `optionNames` | `table` | Returned option names used for removal |
| `optionLabels` | `table` | Returned option labels used for removal |

Returns:

- provider-specific handle table for `GlobalModelTarget(arguments)`
- provider-specific removal result for `RemoveGlobalModelTarget(...)`

How to write it as function:

```lua
local result = FWB.GlobalModelTarget(arguments)
FWB.RemoveGlobalModelTarget(model, optionNames, optionLabels)
```

How to write it as export:

- No direct export is provided for these helpers.

Example as function:

```lua
local result = FWB.GlobalModelTarget({
    model = 'prop_atm_01',
    options = {
        {
            label = 'Use ATM',
            icon = 'fas fa-money-check',
            clientevent = 'banking:openAtm'
        }
    }
})
```

</details>

<details>
<summary><strong>GetTargetResourceName()</strong></summary>

Short description: Read the currently detected target resource name.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string` target resource name
- `nil` when unavailable

How to write it as function:

```lua
local targetResource = FWB.GetTargetResourceName()
```

How to write it as export:

- No direct export is provided for this helper.

Example as function:

```lua
local targetResource = FWB.GetTargetResourceName()
print(targetResource)
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

Short description: Read numeric or raw version values from a resource `fxmanifest` version field on client side.

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
