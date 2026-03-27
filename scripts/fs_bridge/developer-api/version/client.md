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

This page documents the public client-side version helpers.

## FWB

### Resource Version

<details>
<summary><strong>Get Resource Server Version</strong></summary>

Short description: Read the installed numeric version of a resource from its manifest metadata.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Resource name |

Returns:

- `number`
- `0` when the resource version metadata is invalid

How to write it as function:

```lua
local version = FWB.GetResourceServerVersion(resource)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local version = FWB.GetResourceServerVersion('fs_bridge')
print(version)
```

Example as export:

```lua
-- Use FWB.GetResourceServerVersion(...) through import.lua.
```

</details>

<details>
<summary><strong>Get Resource Server Version String</strong></summary>

Short description: Read the installed version string of a resource from its manifest metadata.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Resource name |

Returns:

- `string`
- `0` when the resource version metadata is invalid

How to write it as function:

```lua
local version = FWB.GetResourceServerVersionString(resource)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local version = FWB.GetResourceServerVersionString('fs_bridge')
print(version)
```

Example as export:

```lua
-- Use FWB.GetResourceServerVersionString(...) through import.lua.
```

</details>

