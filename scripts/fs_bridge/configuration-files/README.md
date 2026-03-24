# &#128196; Configuration Files

This section documents the current user-facing Bridge files that can be changed safely in normal setups.

These pages were synced against the current Bridge build, but they intentionally summarize the editable options instead of republishing the full private source files.

## Main Files

| File | Purpose |
|---|---|
| `config/sh_config.lua` | Main shared Bridge configuration |
| `config/cl_config.lua` | Client-side setup for zone creation helpers |
| `config/sv_config.lua` | Server-side framework database settings and plate generation |
| `unlocked/client.lua` | Client-side manual compatibility code |
| `unlocked/server.lua` | Server-side manual compatibility code |

## In This Section

| Page | What It Covers |
|---|---|
| [Shared Config (`sh_config.lua`)](shared-config.md) | Framework, debug, runtime, and integration selector settings |
| [Client Config (`cl_config.lua`)](client-config.md) | Zone creation controls, hints, markers, and placement speeds |
| [Server Config (`sv_config.lua`)](server-config.md) | Framework DB settings and generated vehicle plate rules |
| [Unlocked Client (`client.lua`)](unlocked-client.md) | Where client-side manual compatibility code should go |
| [Unlocked Server (`server.lua`)](unlocked-server.md) | Where server-side manual compatibility code should go |

## Notes

- most users mainly work in `sh_config.lua`
- `cl_config.lua` and `sv_config.lua` should only be changed when you understand the effect
- unlocked files are for manual compatibility, not normal setup
- locked Bridge files should not be your first edit point
