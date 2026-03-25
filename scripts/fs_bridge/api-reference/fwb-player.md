# FWB.Player

`FWB.Player` is the main client-side namespace for local player state, player info, status updates, nearby helpers, and front-coord helpers.

## Public Calls

```lua
FWB.Player.IsLoaded()
FWB.Player.Data()
FWB.Player.CharacterId()
FWB.Player.Name(source)
FWB.Player.Salary()
FWB.Player.IsBoss()

FWB.Player.Hunger.Add(value)
FWB.Player.Hunger.Remove(value)
FWB.Player.Thirst.Add(value)
FWB.Player.Thirst.Remove(value)
FWB.Player.Stress.Add(value)
FWB.Player.Stress.Remove(value)
FWB.Player.Health.Add(value)
FWB.Player.Health.Remove(value)
FWB.Player.Armour.Add(value)
FWB.Player.Armour.Remove(value)

FWB.Player.GetNearbyObjects(extras)
FWB.Player.GetClosestObject(extras)
FWB.Player.GetNearbyPlayers(extras)
FWB.Player.GetClosestPlayer(extras)
FWB.Player.GetNearbyPeds(extras)
FWB.Player.GetClosestPed(extras)
FWB.Player.GetNearbyVehicles(extras)
FWB.Player.GetClosestVehicle(extras)
FWB.Player.GetFrontCoords(extras)
```

<details>
<summary><strong>Player State And Identity</strong></summary>

Short description: Read the current client player load state and basic player information.

Signature:

```lua
FWB.Player.IsLoaded()
FWB.Player.Data()
FWB.Player.CharacterId()
FWB.Player.Name(source)
FWB.Player.Salary()
FWB.Player.IsBoss()

exports.fs_bridge:IsPlayerLoaded()
exports.fs_bridge:GetPlayerData()
exports.fs_bridge:GetPlayerIdentifier()
exports.fs_bridge:GetPlayerName(source)
exports.fs_bridge:GetPlayerSalary()
exports.fs_bridge:IsPlayerBoss()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.IsLoaded()` | none | Checks whether the local player has fully loaded |
| `FWB.Player.Data()` | none | Returns the active framework player data table |
| `FWB.Player.CharacterId()` | none | Returns the framework character id or identifier |
| `FWB.Player.Name(source)` | `source?` | Without `source`, returns the local player full name |
| `FWB.Player.Salary()` | none | Returns current job salary or payment |
| `FWB.Player.IsBoss()` | none | Returns whether the local player is boss grade |

Returns:

- `FWB.Player.IsLoaded()` -> `boolean`
- `FWB.Player.Data()` -> framework player table or `false`
- `FWB.Player.CharacterId()` -> `string` or `nil`
- `FWB.Player.Name(source)` -> `string`, player source fallback, or `nil`
- `FWB.Player.Salary()` -> `number` or `nil`
- `FWB.Player.IsBoss()` -> `boolean`

Example usage:

```lua
if FWB.Player.IsLoaded() then
    local playerData = FWB.Player.Data()
    local name = FWB.Player.Name()
    local characterId = FWB.Player.CharacterId()

    print(name, characterId, playerData and playerData.job and playerData.job.name)
end
```

Notes:

- `FWB.Player.Data()` returns the native ESX, QBCore, or Qbox player data table
- `FWB.Player.Name(source)` can be used when you need another player's name on the client

</details>

<details>
<summary><strong>Player Status Helpers</strong></summary>

Short description: Add or remove common player status values through the active bridge integration.

Signature:

```lua
FWB.Player.Hunger.Add(value)
FWB.Player.Hunger.Remove(value)
FWB.Player.Thirst.Add(value)
FWB.Player.Thirst.Remove(value)
FWB.Player.Stress.Add(value)
FWB.Player.Stress.Remove(value)
FWB.Player.Health.Add(value)
FWB.Player.Health.Remove(value)
FWB.Player.Armour.Add(value)
FWB.Player.Armour.Remove(value)

exports.fs_bridge:AddHunger(value)
exports.fs_bridge:RemoveHunger(value)
exports.fs_bridge:AddThirst(value)
exports.fs_bridge:RemoveThirst(value)
exports.fs_bridge:AddStress(value)
exports.fs_bridge:RemoveStress(value)
exports.fs_bridge:AddHealth(value)
exports.fs_bridge:RemoveHealth(value)
exports.fs_bridge:AddArmour(value)
exports.fs_bridge:RemoveArmour(value)
```

Arguments:

| Call Family | Arguments | Notes |
|---|---|---|
| `Hunger`, `Thirst`, `Stress`, `Health`, `Armour` | `value` | Number to add or remove |

Returns:

- framework-specific status update result
- `nil` if the active status resource does not return a value

Example usage:

```lua
FWB.Player.Hunger.Remove(15)
FWB.Player.Thirst.Remove(10)
FWB.Player.Stress.Add(5)
```

Notes:

- keep `value` numeric
- if a status system is not supported in normal setup, use the manual compatibility page

</details>

<details>
<summary><strong>Nearby Objects And Players</strong></summary>

Short description: Search for nearby objects or players from the local player position by default.

Signature:

```lua
FWB.Player.GetNearbyObjects(extras)
FWB.Player.GetClosestObject(extras)
FWB.Player.GetNearbyPlayers(extras)
FWB.Player.GetClosestPlayer(extras)

exports.fs_bridge:GetNearbyObjects(extras)
exports.fs_bridge:GetClosestObject(extras)
exports.fs_bridge:GetNearbyPlayers(extras)
exports.fs_bridge:GetClosestPlayer(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Trim result list |
| `sortedByDistance` | `boolean` | Default `true` |
| `model` | `number|string` | Object model filter |
| `models` | `table` | Allow-list models |
| `excludeModels` | `table` | Block-list models |
| `requireClearLos` | `boolean` | Useful for line-of-sight interaction checks |
| `selfInclude` | `boolean` | For player search only |

Returns:

- `GetNearbyObjects(extras)` -> table of object entries
- `GetClosestObject(extras)` -> one object entry or `nil`
- `GetNearbyPlayers(extras)` -> table of player entries
- `GetClosestPlayer(extras)` -> one player entry or `nil`

Example usage:

```lua
local closestPlayer = FWB.Player.GetClosestPlayer({
    maxDistance = 2.5,
    selfInclude = false
})

if closestPlayer then
    print(closestPlayer.source, closestPlayer.distance)
end
```

Notes:

- player entries include `id`, `source`, `serverId`, `ped`, `coords`, and `distance`
- object entries include `object`, `entity`, `coords`, `distance`, and `model`

</details>

<details>
<summary><strong>Nearby Peds And Vehicles</strong></summary>

Short description: Search for nearby peds or nearby vehicles from the local player position.

Signature:

```lua
FWB.Player.GetNearbyPeds(extras)
FWB.Player.GetClosestPed(extras)
FWB.Player.GetNearbyVehicles(extras)
FWB.Player.GetClosestVehicle(extras)

exports.fs_bridge:GetNearbyPeds(extras)
exports.fs_bridge:GetClosestPed(extras)
exports.fs_bridge:GetNearbyVehicles(extras)
exports.fs_bridge:GetClosestVehicle(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `coords` | `vector3` | Optional override coords |
| `maxDistance` | `number` | Search radius, default `2.0` |
| `maxCount` | `number` | Trim result list |
| `sortedByDistance` | `boolean` | Default `true` |
| `requireClearLos` | `boolean` | Useful for interaction checks |
| `includeMissionPeds` | `boolean` | Ped search only |
| `aliveOnly` | `boolean` | Ped search only, default `true` |
| `includePlayerVehicle` | `boolean` | Vehicle search only |
| `model` | `number|string` | Optional model filter |
| `models` | `table` | Allow-list models |
| `excludeModels` | `table` | Block-list models |

Returns:

- `GetNearbyPeds(extras)` -> table of ped entries
- `GetClosestPed(extras)` -> one ped entry or `nil`
- `GetNearbyVehicles(extras)` -> table of vehicle entries
- `GetClosestVehicle(extras)` -> one vehicle entry or `nil`

Example usage:

```lua
local closestVehicle = FWB.Player.GetClosestVehicle({
    maxDistance = 5.0,
    includePlayerVehicle = false
})

if closestVehicle then
    print(closestVehicle.vehicle, closestVehicle.plate)
end
```

Notes:

- ped entries include `ped`, `entity`, `coords`, `distance`, and `model`
- vehicle entries include `vehicle`, `entity`, `coords`, `distance`, `model`, and `plate`

</details>

<details>
<summary><strong>Front Coords</strong></summary>

Short description: Get a point directly in front of the local player or a provided ped/heading.

Signature:

```lua
FWB.Player.GetFrontCoords(extras)
exports.fs_bridge:GetFrontCoords(extras)
```

Arguments:

| Key | Type | Notes |
|---|---|---|
| `distance` | `number` | Default `1.0` |
| `verticalOffset` | `number` | Default `-0.7` |
| `ped` | `number` | Optional ped to calculate from |
| `coords` | `vector3` | Optional base coords |
| `heading` | `number` | Optional base heading |

Returns:

- `vector3`

Example usage:

```lua
local frontCoords = FWB.Player.GetFrontCoords({
    distance = 2.0,
    verticalOffset = -0.7
})

print(frontCoords)
```

Notes:

- useful for placing props, markers, and interaction checks in front of the player

</details>
