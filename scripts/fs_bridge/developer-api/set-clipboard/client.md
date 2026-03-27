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

This page documents the public client-side clipboard helper.

## FWB.SetClipBoard

### Clipboard

<details>
<summary><strong>Set Clipboard</strong></summary>

Short description: Copy a string to the client clipboard through the active Bridge clipboard integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `text` | `string` | Text to copy to the clipboard |

Returns:

- integration-specific result
- `nil`

How to write it as function:

```lua
FWB.SetClipBoard(text)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
FWB.SetClipBoard('ABC123')
```

Example as export:

```lua
-- Use FWB.SetClipBoard(...) through import.lua.
```

</details>
