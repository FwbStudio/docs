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

This page documents the shared `FWB.String` helpers.

## Public Calls

```lua
FWB.String.Trim(value)
FWB.String.Plate(value)
FWB.String.Capitalize(value)
FWB.String.Upper(value)
FWB.String.Lower(value)
FWB.String.StartsWith(str, prefix, caseSensitive)
FWB.String.EndsWith(str, suffix, caseSensitive)
FWB.String.Contains(str, search, caseSensitive, plain)
FWB.String.IsNullOrEmpty(str, trim)
FWB.String.IsNullOrWhitespace(str)
FWB.String.Split(str, separator, plain)
FWB.String.Replace(str, search, replacement, plain)
```

## Export Calls

```lua
exports['fs_bridge']:TrimString(value)
exports['fs_bridge']:CapitalizeString(value)
exports['fs_bridge']:UpperString(value)
exports['fs_bridge']:LowerString(value)
exports['fs_bridge']:StringStartsWith(str, prefix, caseSensitive)
exports['fs_bridge']:StringEndsWith(str, suffix, caseSensitive)
exports['fs_bridge']:StringContains(str, search, caseSensitive, plain)
exports['fs_bridge']:StringIsNullOrEmpty(str, trim)
exports['fs_bridge']:StringIsNullOrWhitespace(str)
exports['fs_bridge']:SplitString(str, separator, plain)
exports['fs_bridge']:ReplaceString(str, search, replacement, plain)
```

## Notes

- `FWB.String.Plate(value)` is the plate-safe alias of `Trim`.
- String check helpers return boolean values.
- Transform helpers return the original non-string value when the input type is wrong.

## Example

```lua
local plate = FWB.String.Plate('   ABC123   ')
local ok = FWB.String.Contains('Hello World', 'world', false, true)
print(plate, ok)
```

