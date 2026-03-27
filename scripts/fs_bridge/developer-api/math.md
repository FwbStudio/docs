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
# Math

This page documents the shared `FWB.Math` helpers.

## Public Calls

```lua
FWB.Math.Round(num, decimalPlaces)
FWB.Math.Random(minRange, maxRange)
```

## Round

```lua
local rounded = FWB.Math.Round(12.3456, 2)
print(rounded)
```

- Without `decimalPlaces`, it returns a rounded integer.
- With `decimalPlaces`, it returns a rounded number.

## Random

```lua
local number = FWB.Math.Random(1, 10)
print(number)
```

- `minRange` defaults to `1`
- `maxRange` defaults to `10`

