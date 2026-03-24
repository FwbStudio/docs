# Installation

This page covers the normal Bridge installation flow for FiveM servers.

## Required Base Scripts

You should have these in place before setting up Bridge:

| Type | Required |
|---|---|
| Database library | `oxmysql` |
| Framework | `es_extended` or `qb-core` |
| Bridge resource | `fs_bridge` |

## Optional Supported Scripts

You only need these if you want Bridge to connect to them:

- inventory
- target
- dispatch
- clothing
- banking
- vehicle keys
- fuel
- phone
- progressbar
- notification
- text UI

## Recommended Setup Flow

1. Install and start `oxmysql`.
2. Make sure your framework is already working: `es_extended` or `qb-core`.
3. Add `fs_bridge` to your server resources.
4. Start Bridge after your framework and the supported scripts you want it to detect.
5. Open `config/sh_config.lua`.
6. Keep `selected_key = 1` for auto-detect unless you want to force a specific supported resource.
7. Restart the server and check the Bridge debug output.

## Basic Checks After Install

- Bridge starts without errors
- your framework is detected correctly
- the integrations you use are detected correctly
- public functions like `FWB.Player.Job.Name()` work in your scripts

## If You Use A Custom Unsupported Script

Do not edit locked Bridge files for a normal setup.

Use:

- `unlocked/client.lua`
- `unlocked/server.lua`

The override examples are in the [Developers](../developers/README.md) section.
