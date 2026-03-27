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
# Table

This page documents the shared table helpers.

## FWB.Table

### Table Helpers

<details>
<summary><strong>Contains Value</strong></summary>

Short description: Check whether a table contains a value. `FWB.Table.TableContains(tbl, value)` is the compatibility alias.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |
| `value` | `any` | Value to look for |
| `deep` | `boolean` | Search nested tables too |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.Table.Contains(tbl, value, deep)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:TableContains(tbl, value)
```

Example as function:

```lua
local ok = FWB.Table.Contains({ a = 1, b = { c = 2 } }, 2, true)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:TableContains({ a = 1, b = 2 }, 2)
print(ok)
```

</details>

<details>
<summary><strong>Dump Table</strong></summary>

Short description: Convert a value into a readable debug string.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `any` | Value to dump |
| `depth` | `number` | Optional starting depth |

Returns:

- `string`

How to write it as function:

```lua
local text = FWB.Table.Dump(value, depth)
```

How to write it as export:

```lua
local text = exports['fs_bridge']:DumpTable(value)
```

Example as function:

```lua
local text = FWB.Table.Dump({ name = 'fwb', version = 1 })
print(text)
```

Example as export:

```lua
local text = exports['fs_bridge']:DumpTable({ name = 'fwb', version = 1 })
print(text)
```

</details>

<details>
<summary><strong>Count Table</strong></summary>

Short description: Count table entries. `FWB.Table.SizeOf(tbl)` and `FWB.Table.Length(tbl)` are public aliases.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |

Returns:

- `number`

How to write it as function:

```lua
local count = FWB.Table.Count(tbl)
```

How to write it as export:

```lua
local count = exports['fs_bridge']:TableCount(tbl)
```

Example as function:

```lua
local count = FWB.Table.Count({ a = 1, b = 2, c = 3 })
print(count)
```

Example as export:

```lua
local count = exports['fs_bridge']:TableCount({ a = 1, b = 2, c = 3 })
print(count)
```

</details>

<details>
<summary><strong>Find In Table</strong></summary>

Short description: Find the first value that matches a predicate.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |
| `predicate` | `function` | Called as `predicate(value, key)` |

Returns:

- `any, any` value and key
- `nil, nil` when nothing matches

How to write it as function:

```lua
local value, key = FWB.Table.Find(tbl, predicate)
```

How to write it as export:

```lua
local value, key = exports['fs_bridge']:FindInTable(tbl, predicate)
```

Example as function:

```lua
local value, key = FWB.Table.Find({ a = 5, b = 10 }, function(v)
    return v == 10
end)
print(key, value)
```

Example as export:

```lua
local value, key = exports['fs_bridge']:FindInTable({ a = 5, b = 10 }, function(v)
    return v == 10
end)
print(key, value)
```

</details>

<details>
<summary><strong>Get Table Keys</strong></summary>

Short description: Return the table keys as an array.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |

Returns:

- `table[]`

How to write it as function:

```lua
local keys = FWB.Table.Keys(tbl)
```

How to write it as export:

```lua
local keys = exports['fs_bridge']:GetTableKeys(tbl)
```

Example as function:

```lua
local keys = FWB.Table.Keys({ a = 1, b = 2 })
print(keys[1], keys[2])
```

Example as export:

```lua
local keys = exports['fs_bridge']:GetTableKeys({ a = 1, b = 2 })
print(keys[1], keys[2])
```

</details>

<details>
<summary><strong>Get Table Values</strong></summary>

Short description: Return the table values as an array.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |

Returns:

- `table[]`

How to write it as function:

```lua
local values = FWB.Table.Values(tbl)
```

How to write it as export:

```lua
local values = exports['fs_bridge']:GetTableValues(tbl)
```

Example as function:

```lua
local values = FWB.Table.Values({ a = 1, b = 2 })
print(values[1], values[2])
```

Example as export:

```lua
local values = exports['fs_bridge']:GetTableValues({ a = 1, b = 2 })
print(values[1], values[2])
```

</details>

<details>
<summary><strong>Copy Table</strong></summary>

Short description: Create a shallow copy of a table. `FWB.Table.ShallowCopy(tbl)` is the public alias.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |

Returns:

- `table`
- original value when the input is not a table

How to write it as function:

```lua
local copy = FWB.Table.Copy(tbl)
```

How to write it as export:

```lua
local copy = exports['fs_bridge']:CopyTable(tbl)
```

Example as function:

```lua
local copy = FWB.Table.Copy({ a = 1, b = 2 })
print(copy.a, copy.b)
```

Example as export:

```lua
local copy = exports['fs_bridge']:CopyTable({ a = 1, b = 2 })
print(copy.a, copy.b)
```

</details>

<details>
<summary><strong>Deep Copy Table</strong></summary>

Short description: Create a deep copy of a table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |

Returns:

- `table`
- original value when the input is not a table

How to write it as function:

```lua
local copy = FWB.Table.DeepCopy(tbl)
```

How to write it as export:

```lua
local copy = exports['fs_bridge']:DeepCopyTable(tbl)
```

Example as function:

```lua
local copy = FWB.Table.DeepCopy({ a = { b = 2 } })
print(copy.a.b)
```

Example as export:

```lua
local copy = exports['fs_bridge']:DeepCopyTable({ a = { b = 2 } })
print(copy.a.b)
```

</details>

<details>
<summary><strong>Merge Tables</strong></summary>

Short description: Merge one table into another.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `target` | `table` | Base table |
| `source` | `table` | Table to merge into the target |
| `deep` | `boolean` | Deep merge nested tables |

Returns:

- `table`

How to write it as function:

```lua
local merged = FWB.Table.Merge(target, source, deep)
```

How to write it as export:

```lua
local merged = exports['fs_bridge']:MergeTables(target, source, deep)
```

Example as function:

```lua
local merged = FWB.Table.Merge({ a = 1 }, { b = 2 }, true)
print(merged.a, merged.b)
```

Example as export:

```lua
local merged = exports['fs_bridge']:MergeTables({ a = 1 }, { b = 2 }, true)
print(merged.a, merged.b)
```

</details>

<details>
<summary><strong>Is Array</strong></summary>

Short description: Check whether a table is a continuous array.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.Table.IsArray(tbl)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:TableIsArray(tbl)
```

Example as function:

```lua
local ok = FWB.Table.IsArray({ 'a', 'b', 'c' })
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:TableIsArray({ 'a', 'b', 'c' })
print(ok)
```

</details>

<details>
<summary><strong>Map Table</strong></summary>

Short description: Map each table entry through a callback.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |
| `mapper` | `function` | Called as `mapper(value, key)` |

Returns:

- `table`

How to write it as function:

```lua
local mapped = FWB.Table.Map(tbl, mapper)
```

How to write it as export:

```lua
local mapped = exports['fs_bridge']:MapTable(tbl, mapper)
```

Example as function:

```lua
local mapped = FWB.Table.Map({ 1, 2, 3 }, function(value)
    return value * 2
end)
print(mapped[1], mapped[2], mapped[3])
```

Example as export:

```lua
local mapped = exports['fs_bridge']:MapTable({ 1, 2, 3 }, function(value)
    return value * 2
end)
print(mapped[1], mapped[2], mapped[3])
```

</details>

<details>
<summary><strong>Filter Table</strong></summary>

Short description: Filter a table through a predicate callback.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source table |
| `predicate` | `function` | Called as `predicate(value, key)` |

Returns:

- `table`

How to write it as function:

```lua
local filtered = FWB.Table.Filter(tbl, predicate)
```

How to write it as export:

```lua
local filtered = exports['fs_bridge']:FilterTable(tbl, predicate)
```

Example as function:

```lua
local filtered = FWB.Table.Filter({ 1, 2, 3, 4 }, function(value)
    return value % 2 == 0
end)
print(filtered[1], filtered[2])
```

Example as export:

```lua
local filtered = exports['fs_bridge']:FilterTable({ 1, 2, 3, 4 }, function(value)
    return value % 2 == 0
end)
print(filtered[1], filtered[2])
```

</details>

<details>
<summary><strong>Join Table</strong></summary>

Short description: Join array values into one string.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source array table |
| `separator` | `string` | Separator. Defaults to `, ` |

Returns:

- `string`

How to write it as function:

```lua
local text = FWB.Table.Join(tbl, separator)
```

How to write it as export:

```lua
local text = exports['fs_bridge']:JoinTable(tbl, separator)
```

Example as function:

```lua
local text = FWB.Table.Join({ 'police', 'ambulance', 'mechanic' }, ', ')
print(text)
```

Example as export:

```lua
local text = exports['fs_bridge']:JoinTable({ 'police', 'ambulance', 'mechanic' }, ', ')
print(text)
```

</details>

<details>
<summary><strong>Sort Table</strong></summary>

Short description: Return a sorted shallow copy of an array table.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `tbl` | `table` | Source array table |
| `comparer` | `function` | Optional comparer callback |

Returns:

- `table`

How to write it as function:

```lua
local sorted = FWB.Table.Sort(tbl, comparer)
```

How to write it as export:

```lua
local sorted = exports['fs_bridge']:SortTable(tbl, comparer)
```

Example as function:

```lua
local sorted = FWB.Table.Sort({ 4, 1, 3, 2 })
print(sorted[1], sorted[2], sorted[3], sorted[4])
```

Example as export:

```lua
local sorted = exports['fs_bridge']:SortTable({ 4, 1, 3, 2 })
print(sorted[1], sorted[2], sorted[3], sorted[4])
```

</details>
