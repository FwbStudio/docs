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
# Functions

Safezone Creator includes client and server hook functions for safezone activity.

## Client Functions

<details>
<summary><strong>1. Player Enter Zone - FSBridge.Functions.OnEnterZone(zone)</strong></summary>

Runs when the local player enters a safezone.

Source file:

* `bridge/functions/client.lua`

Arguments:

* `zone` - table containing the current safezone data

Safezone data can include:

* `id`
* `name`
* `settings`
* `polyzone`

Example:

```lua
function FSBridge.Functions.OnEnterZone(zone)
    print('Entered safezone:', zone and zone.name)

    if zone and zone.id then
        print('Safezone ID:', zone.id)
    end
end
```

</details>

<details>
<summary><strong>2. Player Leave Zone - FSBridge.Functions.OnLeaveZone(zone)</strong></summary>

Runs when the local player leaves a safezone.

Source file:

* `bridge/functions/client.lua`

Arguments:

* `zone` - table containing the last safezone data

Example:

```lua
function FSBridge.Functions.OnLeaveZone(zone)
    print('Left safezone:', zone and zone.name)
end
```

</details>

<details>
<summary><strong>3. Player Inside Zone - FSBridge.Functions.InsideZone(zone)</strong></summary>

Runs while the local player stays inside a safezone.

Source file:

* `bridge/functions/client.lua`

Arguments:

* `zone` - table containing the current safezone data

This is useful for custom checks or repeated effects while the player remains inside the zone.

Example:

```lua
function FSBridge.Functions.InsideZone(zone)
    if zone and zone.settings then
        print('Inside safezone with current settings loaded.')
    end
end
```

</details>

## Server Functions

<details>
<summary><strong>4. OnPlayerEnterZone(playerId, safezone)</strong></summary>

Runs on the server when a player enters a safezone.

Source file:

* `bridge/functions/server.lua`

Arguments:

* `playerId` - server id of the player
* `safezone` - table containing the current safezone data

Example:

```lua
FSBridge.Functions.OnPlayerEnterZone = function(playerId, safezone)
    print(('Player %s entered safezone %s'):format(playerId, safezone and safezone.name or 'unknown'))
end
```

</details>

<details>
<summary><strong>5. OnPlayerLeaveZone(playerId, safezone)</strong></summary>

Runs on the server when a player leaves a safezone.

Source file:

* `bridge/functions/server.lua`

Arguments:

* `playerId` - server id of the player
* `safezone` - table containing the last safezone data

Example:

```lua
FSBridge.Functions.OnPlayerLeaveZone = function(playerId, safezone)
    print(('Player %s left safezone %s'):format(playerId, safezone and safezone.name or 'unknown'))
end
```

</details>

<details>
<summary><strong>6. PlayerInsideZone(playerId, safezone)</strong></summary>

Runs on the server while a player remains inside a safezone.

Source file:

* `bridge/functions/server.lua`

Arguments:

* `playerId` - server id of the player
* `safezone` - table containing the current safezone data

Example:

```lua
FSBridge.Functions.PlayerInsideZone = function(playerId, safezone)
    if safezone and safezone.id then
        print(('Player %s is inside safezone #%s'):format(playerId, safezone.id))
    end
end
```

</details>

## Related Events

<details>
<summary><strong>7. Client Events</strong></summary>

Safezone Creator triggers these client events internally:

* `fs_safezonecreator:client:onEnterZone`
* `fs_safezonecreator:client:onExitZone`
* `fs_safezonecreator:client:insideZone`

Example:

```lua
AddEventHandler('fs_safezonecreator:client:onEnterZone', function(zone)
    if zone then
        print(('Client entered safezone: %s'):format(zone.name or 'unknown'))
    end
end)

AddEventHandler('fs_safezonecreator:client:onExitZone', function(zone)
    if zone then
        print(('Client left safezone: %s'):format(zone.name or 'unknown'))
    end
end)

AddEventHandler('fs_safezonecreator:client:insideZone', function(zone)
    if zone and zone.id then
        print(('Client is inside safezone #%s'):format(zone.id))
    end
end)
```

</details>

<details>
<summary><strong>8. Server Events</strong></summary>

Safezone Creator triggers these server events internally:

* `fs_safezonecreator:server:onEnterZone`
* `fs_safezonecreator:server:onExitZone`
* `fs_safezonecreator:server:insideZone`

Example:

```lua
AddEventHandler('fs_safezonecreator:server:onEnterZone', function(playerId, zone)
    print(('Player %s entered safezone %s'):format(playerId, zone and zone.name or 'unknown'))
end)

AddEventHandler('fs_safezonecreator:server:onExitZone', function(playerId, zone)
    print(('Player %s left safezone %s'):format(playerId, zone and zone.name or 'unknown'))
end)

AddEventHandler('fs_safezonecreator:server:insideZone', function(playerId, zone)
    if zone and zone.id then
        print(('Player %s is inside safezone #%s'):format(playerId, zone.id))
    end
end)
```

</details>
