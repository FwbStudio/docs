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

This page documents the player-related client namespaces currently available in Bridge.

## FWB.Player

`FWB.Player` is the main client-side namespace for local player state, basic player data, status helpers, nearby lookups, and front-coord helpers.

### Player

<details>
<summary><strong>IsLoaded()</strong></summary>

Short description: Check whether the local player has fully loaded inside the active framework.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `boolean`

How to write it:

```lua
local loaded = FWB.Player.IsLoaded()
```

Example:

```lua
if not FWB.Player.IsLoaded() then return end

print('Player is loaded')
```

</details>

<details>
<summary><strong>Data()</strong></summary>

Short description: Get the current framework player data table for the local player.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- framework player data table
- `false` when player data is not ready yet

How to write it:

```lua
local playerData = FWB.Player.Data()
```

Example:

```lua
local playerData = FWB.Player.Data()

if playerData then
    print(playerData.job and playerData.job.name)
end
```

</details>

<details>
<summary><strong>CharacterId()</strong></summary>

Short description: Get the local player's current character id or framework identifier.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `string`
- `nil`

How to write it:

```lua
local characterId = FWB.Player.CharacterId()
```

Example:

```lua
local characterId = FWB.Player.CharacterId()
print(characterId)
```

</details>

<details>
<summary><strong>Name(source)</strong></summary>

Short description: Get the local player's full name, or another player's name when a source is provided.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Optional player source when you want another player's name |

Returns:

- `string`
- player source fallback
- `nil`

How to write it:

```lua
local myName = FWB.Player.Name()
local otherName = FWB.Player.Name(source)
```

Example:

```lua
local myName = FWB.Player.Name()
print(myName)
```

</details>

<details>
<summary><strong>Salary()</strong></summary>

Short description: Get the current salary or payment value from the local player's active job.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `number`
- `nil`

How to write it:

```lua
local salary = FWB.Player.Salary()
```

Example:

```lua
local salary = FWB.Player.Salary()
print(salary)
```

</details>

<details>
<summary><strong>IsBoss()</strong></summary>

Short description: Check whether the local player is currently the boss grade for the active job.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- `boolean`

How to write it:

```lua
local isBoss = FWB.Player.IsBoss()
```

Example:

```lua
if FWB.Player.IsBoss() then
    print('Open boss features')
end
```

</details>

<details>
<summary><strong>IsDown()</strong></summary>

Short description: Check whether the local player is currently downed through the active ambulance integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This shortcut is for the local player |

Returns:

- `boolean`
- `false`

How to write it:

```lua
local isDown = FWB.Player.IsDown()
```

Example:

```lua
if FWB.Player.IsDown() then
    print('Player is downed')
end
```

</details>

<details>
<summary><strong>IsDead()</strong></summary>

Short description: Check whether the local player is currently dead through the active ambulance integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This shortcut is for the local player |

Returns:

- `boolean`
- `false`

How to write it:

```lua
local isDead = FWB.Player.IsDead()
```

Example:

```lua
if FWB.Player.IsDead() then
    print('Player is dead')
end
```

</details>

<details>
<summary><strong>Hunger.Add(value)</strong></summary>

Short description: Add hunger status value through the active bridge-compatible status system.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Hunger amount to add |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Hunger.Add(value)
```

Example:

```lua
FWB.Player.Hunger.Add(10)
```

</details>

<details>
<summary><strong>Hunger.Remove(value)</strong></summary>

Short description: Remove hunger status value through the active bridge-compatible status system.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Hunger amount to remove |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Hunger.Remove(value)
```

Example:

```lua
FWB.Player.Hunger.Remove(15)
```

</details>

<details>
<summary><strong>Thirst.Add(value)</strong></summary>

Short description: Add thirst status value through the active bridge-compatible status system.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Thirst amount to add |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Thirst.Add(value)
```

Example:

```lua
FWB.Player.Thirst.Add(10)
```

</details>

<details>
<summary><strong>Thirst.Remove(value)</strong></summary>

Short description: Remove thirst status value through the active bridge-compatible status system.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Thirst amount to remove |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Thirst.Remove(value)
```

Example:

```lua
FWB.Player.Thirst.Remove(10)
```

</details>

<details>
<summary><strong>Stress.Add(value)</strong></summary>

Short description: Add stress status value through the active bridge-compatible status system.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Stress amount to add |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Stress.Add(value)
```

Example:

```lua
FWB.Player.Stress.Add(5)
```

</details>

<details>
<summary><strong>Stress.Remove(value)</strong></summary>

Short description: Remove stress status value through the active bridge-compatible status system.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Stress amount to remove |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Stress.Remove(value)
```

Example:

```lua
FWB.Player.Stress.Remove(5)
```

</details>

<details>
<summary><strong>Health.Add(value)</strong></summary>

Short description: Add health value to the local player through the active bridge-compatible health handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Health amount to add |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Health.Add(value)
```

Example:

```lua
FWB.Player.Health.Add(25)
```

</details>

<details>
<summary><strong>Health.Remove(value)</strong></summary>

Short description: Remove health value from the local player through the active bridge-compatible health handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Health amount to remove |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Health.Remove(value)
```

Example:

```lua
FWB.Player.Health.Remove(10)
```

</details>

<details>
<summary><strong>Armour.Add(value)</strong></summary>

Short description: Add armour value to the local player through the active bridge-compatible armour handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Armour amount to add |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Armour.Add(value)
```

Example:

```lua
FWB.Player.Armour.Add(20)
```

</details>

<details>
<summary><strong>Armour.Remove(value)</strong></summary>

Short description: Remove armour value from the local player through the active bridge-compatible armour handler.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `number` | Armour amount to remove |

Returns:

- compatibility-specific result
- `nil`

How to write it:

```lua
FWB.Player.Armour.Remove(value)
```

Example:

```lua
FWB.Player.Armour.Remove(10)
```

</details>

<details>
<summary><strong>GetNearbyObjects(extras)</strong></summary>

Short description: Get nearby world objects around the local player, or around custom coords when provided.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Limit the number of returned entries |
| `sortedByDistance` | `boolean` | Default `true` |
| `model` | `number|string` | Optional single model filter |
| `models` | `table` | Optional allow-list of models |
| `excludeModels` | `table` | Optional block-list of models |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- table of nearby object entries

How to write it:

```lua
local objects = FWB.Player.GetNearbyObjects(extras)
```

Example:

```lua
local objects = FWB.Player.GetNearbyObjects({
    maxDistance = 3.0,
    model = `prop_atm_01`
})

if objects[1] then
    print(objects[1].object, objects[1].distance)
end
```

</details>

<details>
<summary><strong>GetClosestObject(extras)</strong></summary>

Short description: Get the closest object entry around the local player or provided coords.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `model` | `number|string` | Optional single model filter |
| `models` | `table` | Optional allow-list of models |
| `excludeModels` | `table` | Optional block-list of models |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- one object entry
- `nil`

How to write it:

```lua
local closestObject = FWB.Player.GetClosestObject(extras)
```

Example:

```lua
local closestObject = FWB.Player.GetClosestObject({
    maxDistance = 2.5,
    model = `prop_atm_01`
})

if closestObject then
    print(closestObject.object)
end
```

</details>

<details>
<summary><strong>GetNearbyPlayers(extras)</strong></summary>

Short description: Get nearby player entries around the local player or provided coords.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Limit the number of returned entries |
| `sortedByDistance` | `boolean` | Default `true` |
| `selfInclude` | `boolean` | Include the local player in results |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- table of nearby player entries

How to write it:

```lua
local players = FWB.Player.GetNearbyPlayers(extras)
```

Example:

```lua
local players = FWB.Player.GetNearbyPlayers({
    maxDistance = 5.0,
    selfInclude = false
})

if players[1] then
    print(players[1].source, players[1].distance)
end
```

</details>

<details>
<summary><strong>GetClosestPlayer(extras)</strong></summary>

Short description: Get the closest player entry around the local player or provided coords.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `selfInclude` | `boolean` | Include the local player in results |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- one player entry
- `nil`

How to write it:

```lua
local closestPlayer = FWB.Player.GetClosestPlayer(extras)
```

Example:

```lua
local closestPlayer = FWB.Player.GetClosestPlayer({
    maxDistance = 2.5,
    selfInclude = false
})

if closestPlayer then
    print(closestPlayer.source)
end
```

</details>

<details>
<summary><strong>GetNearbyPeds(extras)</strong></summary>

Short description: Get nearby ped entries around the local player or provided coords.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Limit the number of returned entries |
| `sortedByDistance` | `boolean` | Default `true` |
| `includeMissionPeds` | `boolean` | Include mission peds in the result |
| `aliveOnly` | `boolean` | Default `true` |
| `model` | `number|string` | Optional single model filter |
| `models` | `table` | Optional allow-list of models |
| `excludeModels` | `table` | Optional block-list of models |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- table of nearby ped entries

How to write it:

```lua
local peds = FWB.Player.GetNearbyPeds(extras)
```

Example:

```lua
local peds = FWB.Player.GetNearbyPeds({
    maxDistance = 10.0,
    includeMissionPeds = false,
    aliveOnly = true
})

if peds[1] then
    print(peds[1].ped, peds[1].distance)
end
```

</details>

<details>
<summary><strong>GetClosestPed(extras)</strong></summary>

Short description: Get the closest ped entry around the local player or provided coords.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `includeMissionPeds` | `boolean` | Include mission peds in the result |
| `aliveOnly` | `boolean` | Default `true` |
| `model` | `number|string` | Optional single model filter |
| `models` | `table` | Optional allow-list of models |
| `excludeModels` | `table` | Optional block-list of models |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- one ped entry
- `nil`

How to write it:

```lua
local closestPed = FWB.Player.GetClosestPed(extras)
```

Example:

```lua
local closestPed = FWB.Player.GetClosestPed({
    maxDistance = 3.0,
    aliveOnly = true
})

if closestPed then
    print(closestPed.ped)
end
```

</details>

<details>
<summary><strong>GetNearbyVehicles(extras)</strong></summary>

Short description: Get nearby vehicle entries around the local player or provided coords.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Limit the number of returned entries |
| `sortedByDistance` | `boolean` | Default `true` |
| `includePlayerVehicle` | `boolean` | Include the current player vehicle |
| `model` | `number|string` | Optional single model filter |
| `models` | `table` | Optional allow-list of models |
| `excludeModels` | `table` | Optional block-list of models |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- table of nearby vehicle entries

How to write it:

```lua
local vehicles = FWB.Player.GetNearbyVehicles(extras)
```

Example:

```lua
local vehicles = FWB.Player.GetNearbyVehicles({
    maxDistance = 8.0,
    includePlayerVehicle = false
})

if vehicles[1] then
    print(vehicles[1].plate)
end
```

</details>

<details>
<summary><strong>GetClosestVehicle(extras)</strong></summary>

Short description: Get the closest vehicle entry around the local player or provided coords.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `includePlayerVehicle` | `boolean` | Include the current player vehicle |
| `model` | `number|string` | Optional single model filter |
| `models` | `table` | Optional allow-list of models |
| `excludeModels` | `table` | Optional block-list of models |
| `requireClearLos` | `boolean` | Optional line-of-sight check |

Returns:

- one vehicle entry
- `nil`

How to write it:

```lua
local closestVehicle = FWB.Player.GetClosestVehicle(extras)
```

Example:

```lua
local closestVehicle = FWB.Player.GetClosestVehicle({
    maxDistance = 5.0,
    includePlayerVehicle = false
})

if closestVehicle then
    print(closestVehicle.vehicle, closestVehicle.plate)
end
```

</details>

<details>
<summary><strong>GetFrontCoords(extras)</strong></summary>

Short description: Get a point directly in front of the local player or in front of custom coords and heading.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `distance` | `number` | Optional distance, default `1.0` |
| `verticalOffset` | `number` | Optional vertical offset, default `-0.7` |
| `ped` | `number` | Optional ped to calculate from |
| `coords` | `vector3` | Optional base coords |
| `heading` | `number` | Optional base heading |

Returns:

- `vector3`

How to write it:

```lua
local frontCoords = FWB.Player.GetFrontCoords(extras)
```

Example:

```lua
local frontCoords = FWB.Player.GetFrontCoords({
    distance = 2.0,
    verticalOffset = -0.7
})

print(frontCoords)
```

</details>
## FWB.Player.Job

`FWB.Player.Job` is the client-side job namespace for reading the local player's current job name, labels, grade details, and normalized job data.

### Job

<details>
<summary><strong>Read Job Name And Labels</strong></summary>

Short description: Read the current local player job name and display labels.

Signature:

```lua
FWB.Player.Job.Name()
FWB.Player.Job.Label()
FWB.Player.Job.GradeLabel()

exports.fs_bridge:GetPlayerJob()
exports.fs_bridge:GetPlayerJobLabel()
exports.fs_bridge:GetPlayerJobGradeLabel()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Job.Name()` | none | Internal job name such as `police` |
| `FWB.Player.Job.Label()` | none | Display label such as `Police` |
| `FWB.Player.Job.GradeLabel()` | none | Current grade label or grade name |

Returns:

- `string` or `nil`

Example usage:

```lua
local jobName = FWB.Player.Job.Name()
local jobLabel = FWB.Player.Job.Label()
local gradeLabel = FWB.Player.Job.GradeLabel()

print(jobName, jobLabel, gradeLabel)
```

Notes:

- values come from the active framework player data
- `GradeLabel()` reflects ESX or QBCore/Qbox naming for the active framework

</details>

<details>
<summary><strong>Read Job Grade Level</strong></summary>

Short description: Read the numeric grade level of the local player's current job.

Signature:

```lua
FWB.Player.Job.GradeLevel()
exports.fs_bridge:GetPlayerJobGradeLevel()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Job.GradeLevel()` | none | Returns the current grade level |

Returns:

- `number` or `nil`

Example usage:

```lua
local gradeLevel = FWB.Player.Job.GradeLevel()

if gradeLevel and gradeLevel >= 3 then
    print('High enough grade')
end
```

Notes:

- QBCore and Qbox return the grade level from the nested job grade structure

</details>

<details>
<summary><strong>Read Normalized Job Data</strong></summary>

Short description: Read the Bridge-normalized job data table for the local player.

Signature:

```lua
FWB.Player.Job.Data()
exports.fs_bridge:GetPlayerJobData()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Job.Data()` | none | Returns a normalized job table |

Returns:

- job data table

Example usage:

```lua
local job = FWB.Player.Job.Data()

if job then
    print(job.name, job.label, job.gradeLevel)
end
```

Notes:

- use this when you want one normalized job object instead of reading individual fields

</details>

## FWB.Player.Clothes

`FWB.Player.Clothes` provides current-player clothing shortcuts for reading native skin data, applying native skin data, resetting the saved outfit, and saving the current outfit.

### Clothes

<details>
<summary><strong>Get Native Clothes</strong></summary>

Short description: Read the current local player's native clothing state.

Signature:

```lua
FWB.Player.Clothes.GetNative()
exports.fs_bridge:GetPedCurrentNativeSkin()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Clothes.GetNative()` | none | Reads the current local player skin only |

Returns:

- clothes table keyed by component and prop names

Example usage:

```lua
local clothes = FWB.Player.Clothes.GetNative()

if clothes then
    print(clothes.torso_1 and clothes.torso_1.drawable)
end
```

Notes:

- use this client shortcut for the current player only
- for direct ped-oriented calls, use the `FWB.Clothes` namespace

</details>

<details>
<summary><strong>Set Native Clothes</strong></summary>

Short description: Apply a native clothes table to the current local player.

Signature:

```lua
FWB.Player.Clothes.SetNative(clothes)
exports.fs_bridge:SetPedCurrentNativeSkin(clothes)
```

Arguments:

| Name | Type | Notes |
|---|---|---|
| `clothes` | `table` | Native skin table keyed by component and prop names |

Returns:

- framework-specific apply result
- `false` when the provided clothes data is invalid

Example usage:

```lua
FWB.Player.Clothes.SetNative({
    tshirt_1 = { drawable = 15, texture = 0, palette = 0 },
    torso_1 = { drawable = 65, texture = 0, palette = 0 },
    pants_1 = { drawable = 24, texture = 0, palette = 0 }
})
```

Notes:

- this helper targets the local player only
- the clothes table can include component keys such as `torso_1`, `pants_1`, and props such as `helmet_1`

</details>

<details>
<summary><strong>Reset Saved Clothes</strong></summary>

Short description: Reset the local player to the last saved clothing state through the active clothing resource.

Signature:

```lua
FWB.Player.Clothes.Reset()
exports.fs_bridge:ResetPedCurrentScriptSkin()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Clothes.Reset()` | none | Resets the local player only |

Returns:

- compatibility-specific reset result

Example usage:

```lua
FWB.Player.Clothes.Reset()
```

Notes:

- this uses the active clothing integration rather than only natives

</details>

<details>
<summary><strong>Save Current Clothes</strong></summary>

Short description: Save the current local player outfit through the active clothing resource.

Signature:

```lua
FWB.Player.Clothes.Save()
exports.fs_bridge:SavePedCurrentScriptSkin()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Clothes.Save()` | none | Saves the local player only |

Returns:

- compatibility-specific save result

Example usage:

```lua
FWB.Player.Clothes.Save()
```

Notes:

- use this after changing outfit data when your clothing resource supports saving through Bridge

</details>

## FWB.Player.Request

`FWB.Player.Request` groups the client-side asset request helpers for animation dictionaries, models, animation sets, clip sets, particle assets, and weapon assets.

### Request

### Common Rules

- all request helpers return `true` on success and `false` on failure
- all helpers support the `extras` table style
- default `timeout` is `10000`
- `silent = true` disables failure prints
- `keepLoaded = false` releases the asset after a successful load

<details>
<summary><strong>Request Anim Dict</strong></summary>

Short description: Load an animation dictionary before playing an animation.

Signature:

```lua
FWB.Player.Request.AnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000,
    silent = false,
    keepLoaded = true
})

exports.fs_bridge:RequestAnimDict(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `dict` | `string` | Required animation dictionary |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

Example usage:

```lua
local ok = FWB.Player.Request.AnimDict({
    dict = 'amb@world_human_stand_mobile@male@text@enter',
    timeout = 5000
})

if ok then
    print('Anim dict loaded')
end
```

Notes:

- use this before `TaskPlayAnim`

</details>

<details>
<summary><strong>Request Model</strong></summary>

Short description: Load a model before creating a ped, prop, or vehicle.

Signature:

```lua
FWB.Player.Request.Model({
    model = `adder`,
    timeout = 5000,
    silent = false,
    keepLoaded = true,
    requireValid = true
})

exports.fs_bridge:RequestModel(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `model` | `string|number` | Required model name or hash |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |
| `requireValid` | `boolean` | Default `true` |

Returns:

- `boolean`

Example usage:

```lua
local ok = FWB.Player.Request.Model({
    model = `adder`,
    timeout = 5000
})

if ok then
    print('Model loaded')
end
```

Notes:

- this helper is also used internally by other runtime helpers that need a loaded model

</details>

<details>
<summary><strong>Request Anim Set Or Clip Set</strong></summary>

Short description: Load movement sets and clip sets before applying them to a ped.

Signature:

```lua
FWB.Player.Request.AnimSet({
    animSet = 'move_m@drunk@slightlydrunk',
    timeout = 5000,
    keepLoaded = true
})

FWB.Player.Request.ClipSet({
    clipSet = 'move_ped_crouched',
    timeout = 5000,
    keepLoaded = true
})

exports.fs_bridge:RequestAnimSet(extras)
exports.fs_bridge:RequestClipSet(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `animSet` | `string` | Required for `AnimSet` |
| `clipSet` | `string` | Required for `ClipSet` |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

Example usage:

```lua
FWB.Player.Request.AnimSet({
    animSet = 'move_m@drunk@slightlydrunk'
})

FWB.Player.Request.ClipSet({
    clipSet = 'move_ped_crouched'
})
```

Notes:

- `AnimSet` and `ClipSet` share the same loading rules and return pattern

</details>

<details>
<summary><strong>Request Named Ptfx Asset</strong></summary>

Short description: Load a named particle asset before using particle effects.

Signature:

```lua
FWB.Player.Request.NamedPtfxAsset({
    asset = 'core',
    timeout = 5000,
    keepLoaded = true
})

exports.fs_bridge:RequestNamedPtfxAsset(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `asset` | `string` | Required particle asset name |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |

Returns:

- `boolean`

Example usage:

```lua
FWB.Player.Request.NamedPtfxAsset({
    asset = 'core'
})
```

Notes:

- use this before starting named particle effects

</details>

<details>
<summary><strong>Request Weapon Asset</strong></summary>

Short description: Load a weapon asset before using weapon-based effects or previews.

Signature:

```lua
FWB.Player.Request.WeaponAsset({
    weapon = `WEAPON_PISTOL`,
    timeout = 5000,
    keepLoaded = true,
    weaponRequestFlags = 31,
    ammoType = 0
})

exports.fs_bridge:RequestWeaponAsset(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `weapon` | `string|number` | Required weapon name or hash |
| `timeout` | `number` | Optional timeout in milliseconds |
| `silent` | `boolean` | Disable failure prints |
| `keepLoaded` | `boolean` | Keep asset loaded after success |
| `weaponRequestFlags` | `number` | Default `31` |
| `ammoType` | `number` | Default `0` |

Returns:

- `boolean`

Example usage:

```lua
FWB.Player.Request.WeaponAsset({
    weapon = `WEAPON_PISTOL`
})
```

Notes:

- useful when your script works with weapon previews, effects, or weapon-specific assets

</details>

## FWB.Player.Vehicle

`FWB.Player.Vehicle` groups the player-focused client vehicle helpers for nearby search, closest vehicle lookup, and vehicle key actions.

### Vehicle

<details>
<summary><strong>Nearby And Closest Vehicle</strong></summary>

Short description: Search nearby vehicles from the local player position without needing to pass the player coords yourself.

Signature:

```lua
FWB.Player.Vehicle.NearBy(extras)
FWB.Player.Vehicle.Closest(extras)

exports.fs_bridge:GetPlayerNearbyVehicles(extras)
exports.fs_bridge:GetPlayerClosestVehicle(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Trim result list for `NearBy` |
| `sortedByDistance` | `boolean` | Default `true` |
| `includePlayerVehicle` | `boolean` | Include the current player vehicle |
| `model` | `number|string` | Optional model filter |

Returns:

- `FWB.Player.Vehicle.NearBy(extras)` -> table of nearby vehicle entries
- `FWB.Player.Vehicle.Closest(extras)` -> vehicle entity id or `nil`

Example usage:

```lua
local nearby = FWB.Player.Vehicle.NearBy({
    maxDistance = 8.0,
    includePlayerVehicle = false
})

local closestVehicle = FWB.Player.Vehicle.Closest({
    maxDistance = 5.0
})

print(nearby[1] and nearby[1].plate, closestVehicle)
```

Notes:

- the public function name is `NearBy` with the current Bridge casing
- nearby entries include `vehicle`, `coords`, `distance`, `model`, and `plate`

</details>

<details>
<summary><strong>Give And Remove Vehicle Keys</strong></summary>

Short description: Give or remove keys for a vehicle through the active vehicle keys integration.

Signature:

```lua
FWB.Player.Vehicle.Keys.Give(vehicle)
FWB.Player.Vehicle.Keys.Remove(vehicle)

exports.fs_bridge:GiveCarKeyPlayer(vehicle)
exports.fs_bridge:RemoveCarKeyPlayer(vehicle)
```

Arguments:

| Name | Type | Notes |
|---|---|---|
| `vehicle` | `number` | Vehicle entity id |

Returns:

- compatibility-specific key result

Example usage:

```lua
local vehicle = FWB.Player.Vehicle.Closest({
    maxDistance = 5.0
})

if vehicle then
    FWB.Player.Vehicle.Keys.Give(vehicle)
end
```

Notes:

- this uses the active vehicle keys resource selected by Bridge
- if you need the active keys resource name, use `FWB.Vehicle.Keys.ResourceName()`

</details>

