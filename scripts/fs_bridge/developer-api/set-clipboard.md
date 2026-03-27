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
# Set Clipboard

This page documents the public clipboard helper.

## Public Call

```lua
FWB.SetClipBoard(text)
```

## Notes

- This helper is client-side.
- It currently uses `ox_lib` clipboard support when available.
- If the value is not a string, nothing is done.
- If you override clipboard behavior in the unlocked files, that override is used first.

## Example

```lua
FWB.SetClipBoard('ABC123')
```

