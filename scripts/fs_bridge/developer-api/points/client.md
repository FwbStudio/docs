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

This page documents client-side FWB.Points helpers.

`lua
FWB.Points.new(data)
FWB.Points.new(coords, distance, data)
FWB.Points.getAllPoints()
FWB.Points.getNearbyPoints()
FWB.Points.getClosestPoint()
` 

Point data commonly includes coords, distance, onEnter(self), onExit(self), and 
earby(self).

