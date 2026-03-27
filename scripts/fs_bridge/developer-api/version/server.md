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
# Server

This page documents the public server-side version helpers.

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

<details>
<summary><strong>Get Resource GitHub Version</strong></summary>

Short description: Read the latest GitHub release version number for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Resource name |

Returns:

- `number`

How to write it as function:

```lua
local version = FWB.GetResourceGithubVersion(resource)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local version = FWB.GetResourceGithubVersion('fs_bridge')
print(version)
```

Example as export:

```lua
-- Use FWB.GetResourceGithubVersion(...) through import.lua.
```

</details>

<details>
<summary><strong>Get Resource GitHub Version String</strong></summary>

Short description: Read the latest GitHub release version string for a resource.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Resource name |

Returns:

- `string`

How to write it as function:

```lua
local version = FWB.GetResourceGithubVersionString(resource)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local version = FWB.GetResourceGithubVersionString('fs_bridge')
print(version)
```

Example as export:

```lua
-- Use FWB.GetResourceGithubVersionString(...) through import.lua.
```

</details>

<details>
<summary><strong>Has Latest Version</strong></summary>

Short description: Compare the installed resource version against the latest GitHub release version.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `resource` | `string` | Resource name |

Returns:

- `boolean`

How to write it as function:

```lua
local isLatest = FWB.HasLatestVersion(resource)
```

How to write it as export:

```lua
-- This helper does not have a direct Bridge export.
```

Example as function:

```lua
local isLatest = FWB.HasLatestVersion('fs_bridge')
print(isLatest)
```

Example as export:

```lua
-- Use FWB.HasLatestVersion(...) through import.lua.
```

</details>

