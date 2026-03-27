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

This page documents client-side entity search helpers.

`lua
FWB.Entity.Object.Nearby(extras)
FWB.Entity.Object.Closest(extras)
FWB.Entity.Player.Nearby(extras)
FWB.Entity.Player.Closest(extras)
FWB.Entity.Ped.Nearby(extras)
FWB.Entity.Ped.Closest(extras)
FWB.Entity.Vehicle.Nearby(extras)
FWB.Entity.Vehicle.Closest(extras)
` 

Client exports also include GetNearbyObjects, GetClosestObject, GetNearbyPlayers, GetClosestPlayer, GetNearbyPeds, GetClosestPed, GetNearbyVehicles, and GetClosestVehicle, all using one extras table.

