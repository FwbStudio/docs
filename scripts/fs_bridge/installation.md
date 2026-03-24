# Installation

This page covers the recommended Bridge installation flow for FiveM servers.

## Quick Summary

- 🔴 **Start Order Rule:** Ensure `fs_bridge` as the last resource in your `server.cfg`.
- 🟢 **Recommended Layout:** Keep `fs_bridge` and your related FS scripts inside the same `[fs]` folder.
- 🔵 **Default Config:** Keep supported selectors on `1` for auto-detect unless support tells you to change them.
- 🟣 **After Setup:** Restart the server and verify Bridge output in both `F8` and the server console.
- ⚪ **Need Help Checking?** Use `/fs_bridge_c` in-game and `fs_bridge_s` in the server console to check detected modules.

## 📦 Required Base Resources

Make sure these are already installed before Bridge:

| Type | Required |
|---|---|
| Database library | `oxmysql` |
| Framework | `es_extended`, `qb-core`, or `qbx_core` |
| Bridge resource | `fs_bridge` |

## ⏱️ Start Order Rules

Bridge should start after everything it needs to detect.

- start your framework before Bridge
- start supported resources before Bridge
- start all other required resources before Bridge
- ensure `fs_bridge` last

Example order:

```text
oxmysql
framework
supported resources
other required resources
fs_bridge
```

## 📁 Keep Everything In The Same `[fs]` Folder

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

## ⚙️ ESX, QBCore, And Qbox Setup

The setup flow is the same for ESX, QBCore, and Qbox.

1. drag and drop the resource into your server
2. make sure `oxmysql` and your framework are already working
3. keep all supported selectors on `1` for auto detect
4. only use manual selection if a support team member tells you to

Example:

```lua
selected_key = 1
```

## 🧪 Restart And Verify

After installation:

1. restart your server
2. check Bridge debug prints in `F8`
3. check Bridge debug prints in the server console

You can also use these commands to check detected modules:

| Command | Where To Use It | Purpose |
|---|---|---|
| `/fs_bridge_c` | In-game chat | Check client-side detected modules |
| `fs_bridge_s` | Server console | Check server-side detected modules |

## ✅ Quick Checklist

- `oxmysql` is installed
- `es_extended`, `qb-core`, or `qbx_core` is installed
- `fs_bridge` is inside `[fs]`
- supported resources start before Bridge
- `fs_bridge` is ensured last
- selectors stay on `1` unless support tells you otherwise
- debug output looks correct in `F8` and the server console

## ➡️ Next Pages

- [Compatibility](compatibility.md)
- [Common Errors](common-errors.md)
- [Configuration Files](configuration-files/README.md)
