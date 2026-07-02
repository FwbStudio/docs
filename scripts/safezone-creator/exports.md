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
# Exports

Safezone Creator provides client and server exports for reading safezone state.

## Client Exports

<details>
<summary><strong>1. IsInsideSafezone()</strong></summary>

Returns whether the local player is currently inside a safezone.

Returns:

* `true` if inside a safezone
* `false` if not inside a safezone

Example:

```lua
local inside = exports['fs_safezonecreator']:IsInsideSafezone()

if inside then
    print('Player is inside a safezone')
end
```

</details>

<details>
<summary><strong>2. GetCurrentSafezone()</strong></summary>

Returns the current safezone data for the local player.

Returns:

* safezone table when the player is inside a safezone
* `nil` when the player is not inside a safezone

Returned safezone data can include:

* `id`
* `name`
* `settings`
* `polyzone`

Example:

```lua
local safezone = exports['fs_safezonecreator']:GetCurrentSafezone()

if safezone then
    print(('Current safezone: %s'):format(safezone.name))
end
```

</details>

<details>
<summary><strong>3. GetCurrentSafezoneId()</strong></summary>

Returns the current safezone id for the local player.

Returns:

* safezone id when the player is inside a safezone
* `nil` when the player is not inside a safezone

Example:

```lua
local safezoneId = exports['fs_safezonecreator']:GetCurrentSafezoneId()

if safezoneId then
    print(('Current safezone id: %s'):format(safezoneId))
end
```

</details>

## Server Exports

<details>
<summary><strong>4. IsPlayerInsideSafezone(playerId)</strong></summary>

Checks whether a specific player is currently inside a safezone.

Arguments:

* `playerId` - server id of the player

Returns:

* `true` if the player is inside a safezone
* `false` if the player is not inside a safezone

Example:

```lua
local inside = exports['fs_safezonecreator']:IsPlayerInsideSafezone(source)

if inside then
    print('This player is inside a safezone')
end
```

</details>

<details>
<summary><strong>5. GetPlayerSafezone(playerId)</strong></summary>

Returns the current safezone data for a specific player.

Arguments:

* `playerId` - server id of the player

Returns:

* safezone table when the player is inside a safezone
* `nil` when the player is not inside a safezone

Example:

```lua
local safezone = exports['fs_safezonecreator']:GetPlayerSafezone(source)

if safezone then
    print(('Player is inside safezone: %s'):format(safezone.name))
end
```

</details>
