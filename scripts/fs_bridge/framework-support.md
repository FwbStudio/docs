# Framework Support

`fs_bridge` currently supports these base frameworks.

## Supported Frameworks

| Framework | Platform | Notes |
|---|---|---|
| `ESX` | FiveM | Uses `es_extended` config keys |
| `QBCore` | FiveM | Includes dirty money and society bank config branches |
| `VORP` | RedM | Uses `vorp_core` config keys |

## What This Support Includes

- player loaded and unloaded state
- job updates
- player data reads
- money and bank helpers
- job and boss checks
- vehicle property handling

## Recommended Approach

1. Use one of the supported frameworks where possible.
2. Keep the framework event config accurate in `sh_config`.
3. Use the public `FWB.Player.*` and `FWB.Vehicle.*` APIs in your own resources.

If your framework is fully custom, normal unlocked-file overrides are usually not enough for the whole framework layer.
