# FWB.Player

`FWB.Player` is the main client-side namespace for local player state, basic player data, status helpers, nearby lookups, and front-coord helpers.

Related player namespaces:

- [FWB.Player.Job](fwb-player-job.md)
- [FWB.Player.Clothes](fwb-player-clothes.md)
- [FWB.Player.Request](fwb-player-request.md)
- [FWB.Player.Vehicle](fwb-player-vehicle.md)

## Player

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