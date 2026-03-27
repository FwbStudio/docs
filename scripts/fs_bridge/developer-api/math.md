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

This page documents the shared math helpers.

## FWB.Math

### Math Helpers

<details>
<summary><strong>Round Number</strong></summary>

Short description: Round a number with optional decimal precision.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `num` | `number` | Number to round |
| `decimalPlaces` | `number` | Optional decimal precision |

Returns:

- `number`

How to write it as function:

```lua
local rounded = FWB.Math.Round(num, decimalPlaces)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local rounded = FWB.Math.Round(12.3456, 2)
print(rounded)
```

Example as export:

```lua
-- Use FWB.Math.Round(...) through import.lua.
```

</details>

<details>
<summary><strong>Random Number</strong></summary>

Short description: Generate a random number inside the requested range.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `minRange` | `number` | Minimum range. Defaults to `1` |
| `maxRange` | `number` | Maximum range. Defaults to `10` |

Returns:

- `number`

How to write it as function:

```lua
local value = FWB.Math.Random(minRange, maxRange)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local value = FWB.Math.Random(1, 10)
print(value)
```

Example as export:

```lua
-- Use FWB.Math.Random(...) through import.lua.
```

</details>
