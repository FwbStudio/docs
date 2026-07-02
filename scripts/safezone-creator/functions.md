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

Safezone Creator includes built-in client and server hook functions for safezone events.

## Client Functions

These functions are used when the local player enters, leaves, or stays inside a safezone:

* `OnEnterZone(zone)`
* `OnLeaveZone(zone)`
* `InsideZone(zone)`

### What They Do

* `OnEnterZone(zone)` runs when the player enters a safezone
* `OnLeaveZone(zone)` runs when the player leaves a safezone
* `InsideZone(zone)` runs while the player stays inside a safezone

The `zone` data includes the safezone id, name, settings, and polygon data.

## Server Functions

Safezone Creator also triggers server-side hook handling for player zone state:

* `OnPlayerEnterZone(playerId, safezone)`
* `OnPlayerLeaveZone(playerId, safezone)`
* `PlayerInsideZone(playerId, safezone)`

### What They Do

* `OnPlayerEnterZone(playerId, safezone)` runs when a player enters a safezone
* `OnPlayerLeaveZone(playerId, safezone)` runs when a player leaves a safezone
* `PlayerInsideZone(playerId, safezone)` runs while a player remains inside a safezone

These hooks are useful if you want to attach your own custom logic to safezone activity.

## Related Events

Safezone Creator also triggers these events internally:

### Client Events

* `fs_safezonecreator:client:onEnterZone`
* `fs_safezonecreator:client:onExitZone`
* `fs_safezonecreator:client:insideZone`

### Server Events

* `fs_safezonecreator:server:onEnterZone`
* `fs_safezonecreator:server:onExitZone`
* `fs_safezonecreator:server:insideZone`
