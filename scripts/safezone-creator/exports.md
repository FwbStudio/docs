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

### `IsInsideSafezone`

Returns whether the local player is currently inside a safezone.

### `GetCurrentSafezone`

Returns the current safezone data for the local player.

### `GetCurrentSafezoneId`

Returns the current safezone id for the local player.

## Server Exports

### `IsPlayerInsideSafezone`

Checks whether a specific player is currently inside a safezone.

### `GetPlayerSafezone`

Returns the current safezone data for a specific player.

## Returned Safezone Data

Safezone data can include:

* `id`
* `name`
* `settings`
* `polyzone`
