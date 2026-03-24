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

# Installation

This page covers the recommended Bridge installation flow for FiveM servers.

## Before You Start

1. Ensure `fs_bridge` as the last resource in your <mark style="color:#f0fdf4;background-color:#166534;">server.cfg</mark>.
2. Keep `fs_bridge` and your related FS scripts inside the same <mark style="color:#f0fdf4;background-color:#166534;">[fs]</mark> folder.
3. Keep supported selectors on <mark style="color:#f0fdf4;background-color:#166534;">1</mark> for auto-detect unless support tells you to change them.

After setup, restart the server, review Bridge output in `F8` and the server console, and use `/fs_bridge_c` or `fs_bridge_s` if you want to confirm detected modules.

## Required Base Resources

Make sure these are already installed before Bridge:

| Type | Required |
|---|---|
| Database library | `oxmysql` |
| Framework | `es_extended`, `qb-core`, or `qbx_core` |
| Bridge resource | `fs_bridge` |

## Start Order Rules

Ensure your <mark style="color:#f0fdf4;background-color:#166534;">[fs]</mark> folder, including Bridge and your other FS resources, is placed near the bottom of your <mark style="color:#f0fdf4;background-color:#166534;">server.cfg</mark>, with `fs_bridge` ensured last.

Example order:

```text
ensure [framework]
ensure [standalone]
ensure [fs]
ensure fs_bridge
```

## Keep Everything In The Same `[fs]` Folder

Recommended layout:

```text
resources/
`-- [fs]/
    |-- fs_bridge
    |-- your_fs_script_1
    |-- your_fs_script_2
    `-- your_fs_script_3
```

Keeping Bridge and your related scripts in the same `[fs]` folder makes the setup easier to manage, and your scripts can wait for Bridge to start properly.

## ESX, QBCore, And Qbox Setup

The setup flow is the same for ESX, QBCore, and Qbox.

1. drag and drop the resource into your server
2. make sure `oxmysql` and your framework are already working
3. keep all supported selectors on `1` for auto detect
4. only use manual selection if a support team member tells you to

Example:

```lua
selected_key = 1
```

## Restart And Verify

After installation:

1. restart your server
2. check Bridge debug prints in `F8`
3. check Bridge debug prints in the server console

You can also use these commands to check detected modules:

| Command | Where To Use It | Purpose |
|---|---|---|
| `/fs_bridge_c` | In-game chat | Check client-side detected modules |
| `fs_bridge_s` | Server console | Check server-side detected modules |

## Quick Checklist

- `oxmysql` is installed
- `es_extended`, `qb-core`, or `qbx_core` is installed
- `fs_bridge` is inside `[fs]`
- supported resources start before Bridge
- `fs_bridge` is ensured last
- selectors stay on `1` unless support tells you otherwise
- debug output looks correct in `F8` and the server console

## Next Pages

- [Compatibility](compatibility.md)
- [Common Errors](common-errors.md)
- [Configuration Files](configuration-files/)
