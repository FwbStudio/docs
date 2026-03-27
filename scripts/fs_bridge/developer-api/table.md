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

This page documents the shared `FWB.Table` helpers.

## Public Calls

```lua
FWB.Table.Contains(tbl, value, deep)
FWB.Table.Dump(value, depth)
FWB.Table.Count(tbl)
FWB.Table.SizeOf(tbl)
FWB.Table.Length(tbl)
FWB.Table.Find(tbl, predicate)
FWB.Table.Keys(tbl)
FWB.Table.Values(tbl)
FWB.Table.Copy(tbl)
FWB.Table.ShallowCopy(tbl)
FWB.Table.DeepCopy(tbl)
FWB.Table.Merge(target, source, deep)
FWB.Table.IsArray(tbl)
FWB.Table.Map(tbl, mapper)
FWB.Table.Filter(tbl, predicate)
FWB.Table.Join(tbl, separator)
FWB.Table.Sort(tbl, comparer)
```

## Export Calls

```lua
exports['fs_bridge']:TableContains(tbl, value)
exports['fs_bridge']:DumpTable(value)
exports['fs_bridge']:TableCount(tbl)
exports['fs_bridge']:TableSizeOf(tbl)
exports['fs_bridge']:TableLength(tbl)
exports['fs_bridge']:FindInTable(tbl, predicate)
exports['fs_bridge']:GetTableKeys(tbl)
exports['fs_bridge']:GetTableValues(tbl)
exports['fs_bridge']:CopyTable(tbl)
exports['fs_bridge']:DeepCopyTable(tbl)
exports['fs_bridge']:MergeTables(target, source, deep)
exports['fs_bridge']:TableIsArray(tbl)
exports['fs_bridge']:MapTable(tbl, mapper)
exports['fs_bridge']:FilterTable(tbl, predicate)
exports['fs_bridge']:JoinTable(tbl, separator)
exports['fs_bridge']:SortTable(tbl, comparer)
```

## Notes

- Safe defaults are returned when a non-table value is passed.
- Count helpers return `0`.
- List helpers return `{}`.
- Copy helpers return the original value when the input is not a table.

## Example

```lua
local merged = FWB.Table.Merge({ a = 1 }, { b = 2 }, true)
local keys = FWB.Table.Keys(merged)
print(merged.a, merged.b, keys[1])
```

