# Installation

This page covers the normal Bridge installation flow for FiveM servers.

## Required Dependencies

Make sure these are installed before Bridge:

| Type | Required |
|---|---|
| Database library | `oxmysql` |
| Framework | `es_extended` or `qb-core` |
| Bridge resource | `fs_bridge` |

## Recommended Resource Placement

Place Bridge inside your resources folder in your project script group, for example:

```text
resources/[fs]/fs_bridge
```

Keeping Bridge inside your `[fs]` group makes it easier to keep your own script order clean.

## Start Order Rules

- start your framework before Bridge
- start supported resources that Bridge needs to detect before Bridge
- start Bridge before your own scripts that directly depend on Bridge on startup

## ESX Setup

1. Make sure `es_extended` and `oxmysql` are working first.
2. Start any supported target, inventory, phone, dispatch, fuel, or keys resources you want Bridge to detect.
3. Start `fs_bridge`.
4. Start your own resources that use `FWB.*` or `exports.fs_bridge:*`.

## QBCore Setup

1. Make sure `qb-core` and `oxmysql` are working first.
2. Start any supported target, inventory, phone, dispatch, fuel, or keys resources you want Bridge to detect.
3. Start `fs_bridge`.
4. Start your own resources that use `FWB.*` or `exports.fs_bridge:*`.

## Configure Bridge

After the resource is in place:

1. Open `config/sh_config.lua`
2. Keep `selected_key = 1` for auto-detect unless you want to force a supported resource
3. Confirm the framework section matches your server
4. Restart the server

## Basic Checks After Install

- Bridge starts without errors
- the correct framework is detected
- the supported resources you use are detected
- your own scripts can call Bridge after startup

## Next Pages

- [Compatibility](compatibility.md)
- [Common Errors](common-errors.md)
- [Configuration Files](configuration-files/README.md)
