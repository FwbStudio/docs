# Beta Docs

Public documentation for current and upcoming Beta scripts.

This space starts with `fs_bridge`, but the structure is intentionally ready for more scripts later.

## What You Will Find Here

- clean user-facing docs
- public namespace references
- config-first setup guides
- paste-ready override examples
- framework and resource compatibility notes

## Current Script Coverage

| Script | Status | Focus |
|---|---|---|
| `fs_bridge` | Live | Public bridge API, configuration, overrides, and runtime helpers |

## `fs_bridge` At A Glance

### Supported Frameworks

| Framework | Status | Notes |
|---|---|---|
| `ESX` | Supported | FiveM |
| `QBCore` | Supported | FiveM |
| `VORP` | Supported | RedM |

### Supported Resource Groups

| Group | Examples |
|---|---|
| Ambulance | `esx_ambulancejob`, `wasabi_ambulance`, `qb-ambulancejob` |
| Banking | `okokBanking`, `qb-banking`, `Renewed-Banking`, `qs_banking` |
| Clothing | `fivem-appearance`, `illenium-appearance`, `qb-clothing`, `skinchanger` |
| Dispatch | `cd_dispatch`, `ps-dispatch`, `qs-dispatch`, `wasabi_mdt` |
| Inventory | `ox_inventory`, `qs-inventory`, `qb-inventory`, `ps-inventory` |
| Phone | `okokPhone`, `qb-phone`, `lb-phone`, `gksphone` |
| Sounds | `xsound`, `mx-surround` |
| Target | `ox_target`, `qb-target`, `qtarget` |
| Vehicle Fuel | `ox_fuel`, `LegacyFuel`, `cdn-fuel`, `rcore_fuel` |
| Vehicle Keys | `wasabi_carlock`, `qbx_vehiclekeys`, `qb-vehiclekeys`, `qs-vehiclekeys` |

### Built-In Bridge Modules

| Module | Purpose |
|---|---|
| `FWB.Blip` | Static and moving blips |
| `FWB.Ped` | Handle-based ped runtime |
| `FWB.Vehicle` | Vehicle creation, updates, props, ownership helpers |
| `FWB.Entity` | Nearby entity lookups and front-coords helpers |

## How This Docs Space Is Structured

- `Home` gives the big picture.
- `Scripts` is the multi-script entry point.
- Each script gets its own setup, config, overrides, API reference, and support pages.

## Start Here

- [Scripts](scripts/README.md)
- [fs_bridge](scripts/fs_bridge/README.md)
