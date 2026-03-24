# fs_bridge

`fs_bridge` is the shared compatibility layer for framework helpers, runtime modules, and resource integrations.

These docs focus on the parts users actually work with:

- public `FWB.*` namespaces
- exports
- config keys
- unlocked override snippets

They do not focus on internal folder layout, locked files, or deprecated wrappers.

## Quick Links

| Need | Go To |
|---|---|
| First-time setup | [Getting Started](getting-started/README.md) |
| Config keys and selectors | [Configuration](configuration/README.md) |
| Paste-in custom overrides | [Overrides](overrides/README.md) |
| Runtime module usage | [API Reference](api-reference/README.md) |
| Compatibility matrix | [Framework Support](framework-support.md) and [Resource Support](resource-support.md) |

## Main Public Namespaces

| Namespace | Use Case |
|---|---|
| `FWB.Player` | Player state, status helpers, access helpers |
| `FWB.Player.Job` | Job data, labels, grades, duty helpers |
| `FWB.Player.Vehicle` | Player-facing vehicle key helpers |
| `FWB.Banking` | Boss menu and society money helpers |
| `FWB.Clothes` | Clothing resource integration and skin helpers |
| `FWB.Blip` | Static and moving blips |
| `FWB.Ped` | Handle-based ped runtime |
| `FWB.Vehicle` | Vehicle runtime, props, plates, owner updates |
| `FWB.Entity` | Nearby entity and front-coords helpers |

## Built-In Runtime Modules

| Module | Summary |
|---|---|
| `FWB.Blip` | Create, update, remove, toggle, and sync blips |
| `FWB.Ped` | Spawn and manage local or server-managed peds |
| `FWB.Vehicle` | Spawn and manage vehicles, props, and owner workflows |
| `FWB.Entity` | Search nearby objects, players, peds, and vehicles |

## Editing Surface

Most users only need these three touchpoints:

- `config/sh_config.lua`
- `unlocked/client.lua`
- `unlocked/server.lua`

That is the approach these docs are built around.
