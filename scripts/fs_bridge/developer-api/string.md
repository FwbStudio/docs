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
# String

This page documents the shared string helpers.

## FWB.String

### String Helpers

<details>
<summary><strong>Trim String</strong></summary>

Short description: Trim leading and trailing spaces. `FWB.String.Plate(value)` is the public plate-safe alias.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `string` | Source string |

Returns:

- `string`
- original non-string value when the input type is wrong

How to write it as function:

```lua
local text = FWB.String.Trim(value)
```

How to write it as export:

```lua
local text = exports['fs_bridge']:TrimString(value)
```

Example as function:

```lua
local plate = FWB.String.Plate('   ABC123   ')
print(plate)
```

Example as export:

```lua
local text = exports['fs_bridge']:TrimString('   hello   ')
print(text)
```

</details>

<details>
<summary><strong>Capitalize String</strong></summary>

Short description: Capitalize the first letter of a string.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `string` | Source string |

Returns:

- `string`
- original non-string value when the input type is wrong

How to write it as function:

```lua
local text = FWB.String.Capitalize(value)
```

How to write it as export:

```lua
local text = exports['fs_bridge']:CapitalizeString(value)
```

Example as function:

```lua
local text = FWB.String.Capitalize('hello world')
print(text)
```

Example as export:

```lua
local text = exports['fs_bridge']:CapitalizeString('hello world')
print(text)
```

</details>

<details>
<summary><strong>Upper String</strong></summary>

Short description: Convert a string to uppercase.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `string` | Source string |

Returns:

- `string`
- original non-string value when the input type is wrong

How to write it as function:

```lua
local text = FWB.String.Upper(value)
```

How to write it as export:

```lua
local text = exports['fs_bridge']:UpperString(value)
```

Example as function:

```lua
local text = FWB.String.Upper('hello')
print(text)
```

Example as export:

```lua
local text = exports['fs_bridge']:UpperString('hello')
print(text)
```

</details>

<details>
<summary><strong>Lower String</strong></summary>

Short description: Convert a string to lowercase.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `value` | `string` | Source string |

Returns:

- `string`
- original non-string value when the input type is wrong

How to write it as function:

```lua
local text = FWB.String.Lower(value)
```

How to write it as export:

```lua
local text = exports['fs_bridge']:LowerString(value)
```

Example as function:

```lua
local text = FWB.String.Lower('HELLO')
print(text)
```

Example as export:

```lua
local text = exports['fs_bridge']:LowerString('HELLO')
print(text)
```

</details>

<details>
<summary><strong>Starts With</strong></summary>

Short description: Check whether a string starts with the requested prefix.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Source string |
| `prefix` | `string` | Prefix to match |
| `caseSensitive` | `boolean` | Defaults to `true` |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.String.StartsWith(str, prefix, caseSensitive)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:StringStartsWith(str, prefix, caseSensitive)
```

Example as function:

```lua
local ok = FWB.String.StartsWith('police_chief', 'police', true)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:StringStartsWith('police_chief', 'police', true)
print(ok)
```

</details>

<details>
<summary><strong>Ends With</strong></summary>

Short description: Check whether a string ends with the requested suffix.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Source string |
| `suffix` | `string` | Suffix to match |
| `caseSensitive` | `boolean` | Defaults to `true` |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.String.EndsWith(str, suffix, caseSensitive)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:StringEndsWith(str, suffix, caseSensitive)
```

Example as function:

```lua
local ok = FWB.String.EndsWith('report.json', '.json', true)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:StringEndsWith('report.json', '.json', true)
print(ok)
```

</details>

<details>
<summary><strong>Contains</strong></summary>

Short description: Check whether a string contains a search value.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Source string |
| `search` | `string` | Search value |
| `caseSensitive` | `boolean` | Defaults to `true` |
| `plain` | `boolean` | Plain string match. Defaults to `true` |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.String.Contains(str, search, caseSensitive, plain)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:StringContains(str, search, caseSensitive, plain)
```

Example as function:

```lua
local ok = FWB.String.Contains('Hello World', 'world', false, true)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:StringContains('Hello World', 'world', false, true)
print(ok)
```

</details>

<details>
<summary><strong>Is Null Or Empty</strong></summary>

Short description: Check whether a string is `nil` or empty.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Source string or `nil` |
| `trim` | `boolean` | Trim before checking |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.String.IsNullOrEmpty(str, trim)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:StringIsNullOrEmpty(str, trim)
```

Example as function:

```lua
local ok = FWB.String.IsNullOrEmpty('   ', true)
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:StringIsNullOrEmpty('   ', true)
print(ok)
```

</details>

<details>
<summary><strong>Is Null Or Whitespace</strong></summary>

Short description: Check whether a string is `nil`, empty, or only whitespace.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Source string or `nil` |

Returns:

- `boolean`

How to write it as function:

```lua
local ok = FWB.String.IsNullOrWhitespace(str)
```

How to write it as export:

```lua
local ok = exports['fs_bridge']:StringIsNullOrWhitespace(str)
```

Example as function:

```lua
local ok = FWB.String.IsNullOrWhitespace('   ')
print(ok)
```

Example as export:

```lua
local ok = exports['fs_bridge']:StringIsNullOrWhitespace('   ')
print(ok)
```

</details>

<details>
<summary><strong>Split String</strong></summary>

Short description: Split a string by a separator.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Source string |
| `separator` | `string` | Separator string |
| `plain` | `boolean` | Plain string match. Defaults to `true` |

Returns:

- `table[]`

How to write it as function:

```lua
local parts = FWB.String.Split(str, separator, plain)
```

How to write it as export:

```lua
local parts = exports['fs_bridge']:SplitString(str, separator, plain)
```

Example as function:

```lua
local parts = FWB.String.Split('a,b,c', ',', true)
print(parts[1], parts[2], parts[3])
```

Example as export:

```lua
local parts = exports['fs_bridge']:SplitString('a,b,c', ',', true)
print(parts[1], parts[2], parts[3])
```

</details>

<details>
<summary><strong>Replace String</strong></summary>

Short description: Replace a value inside a string.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `str` | `string` | Source string |
| `search` | `string` | Value to replace |
| `replacement` | `string` | Replacement value |
| `plain` | `boolean` | Plain string match. Defaults to `true` |

Returns:

- `string`
- original non-string value when the input type is wrong

How to write it as function:

```lua
local text = FWB.String.Replace(str, search, replacement, plain)
```

How to write it as export:

```lua
local text = exports['fs_bridge']:ReplaceString(str, search, replacement, plain)
```

Example as function:

```lua
local text = FWB.String.Replace('hello world', 'world', 'server', true)
print(text)
```

Example as export:

```lua
local text = exports['fs_bridge']:ReplaceString('hello world', 'world', 'server', true)
print(text)
```

</details>
