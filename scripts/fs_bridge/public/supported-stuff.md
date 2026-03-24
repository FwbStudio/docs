# Supported Stuff

This page is the public compatibility overview for Bridge.

## Supported Frameworks

Bridge currently documents and focuses on these FiveM frameworks:

| Framework | Status | Notes |
|---|---|---|
| `ESX` | Supported | Uses `es_extended` in config |
| `QBCore` | Supported | Uses `qb-core` in config |
| `Qbox` | Supported | Uses `qbx_core` in config |

## Supported Integration Groups

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
| Notification | `ox_lib`, `esx_notify`, `es_extended`, `qb-core` |
| Text UI | `ox_lib`, `esx_textui`, `es_extended`, `qb-core` |
| Progressbar | `ox_lib`, `esx_progressbar`, `qb-core`, `mythic_progbar` |

## Built-In Public Modules

| Module | Purpose |
|---|---|
| `FWB.Blip` | Static and moving blips |
| `FWB.Ped` | Handle-based ped runtime |
| `FWB.Vehicle` | Vehicle creation, updates, props, and ownership helpers |
| `FWB.Entity` | Nearby entity helpers and front-coords helpers |

## Notes

- auto-detect is the normal starting point for supported integrations
- custom unsupported systems should use unlocked overrides
