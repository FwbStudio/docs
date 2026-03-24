# Compatibility

This page shows the frameworks, integrations, and built-in modules that currently have public Bridge support.

> ✅ **Built-in support**
> Every resource listed below already has Bridge support.

> 🟢 **Recommended setup**
> Keep `selected_key = 1` unless a support team member tells you to manually force a specific resource.

> ⬜ **Resource not listed**
> If you do not see a resource below, treat it as unsupported for normal public setup and use the override docs instead.

## Supported Frameworks

| Framework | Status | Resource Name |
|---|---|---|
| `ESX` | ✅ Supported | `es_extended` |
| `QBCore` | ✅ Supported | `qb-core` |
| `Qbox` | ✅ Supported | `qbx_core` |

## Built-In Bridge Modules

| Module | Status | Purpose |
|---|---|---|
| `FWB.Blip` | ✅ Built-in | Static and moving blips |
| `FWB.Ped` | ✅ Built-in | Handle-based ped runtime |
| `FWB.Vehicle` | ✅ Built-in | Vehicle creation, updates, props, and ownership helpers |
| `FWB.Entity` | ✅ Built-in | Nearby entity helpers and front-coords helpers |

## Integration Compatibility

All integration groups below follow the same public setup rule:

- keep `selected_key = 1` for auto-detect
- only force a specific resource if support tells you to
- use overrides if your exact resource is not listed

### Ambulance

Used for downed-state and ambulance compatibility.

| Resource | Status |
|---|---|
| `esx_ambulancejob` | ✅ Supported |
| `wasabi_ambulance` | ✅ Supported |
| `qb-ambulancejob` | ✅ Supported |
| `ak47_ambulancejob` | ✅ Supported |
| `tk_ambulancejob` | ✅ Supported |
| `p_ambulancejob` | ✅ Supported |

### Banking

Used for society banking and bank-related helpers.

| Resource | Status |
|---|---|
| `okokBanking` | ✅ Supported |
| `qb-banking` | ✅ Supported |
| `Renewed-Banking` | ✅ Supported |
| `qb-management` | ✅ Supported |
| `tgg-banking` | ✅ Supported |
| `qs_banking` | ✅ Supported |
| `fd_banking` | ✅ Supported |

### Clothing

Used for clothing, appearance, and skin-related helpers.

| Resource | Status |
|---|---|
| `skinchanger` | ✅ Supported |
| `fivem-appearance` | ✅ Supported |
| `illenium-appearance` | ✅ Supported |
| `rcore_clothing` | ✅ Supported |
| `qb-clothing` | ✅ Supported |
| `crm-appearance` | ✅ Supported |
| `p_appearance` | ✅ Supported |
| `qs-appearance` | ✅ Supported |

### Dispatch

Used for alerts, police notifications, and dispatch integrations.

| Resource | Status |
|---|---|
| `cd_dispatch` | ✅ Supported |
| `ps-dispatch` | ✅ Supported |
| `qs-dispatch` | ✅ Supported |
| `tk_dispatch` | ✅ Supported |
| `rcore_dispatch` | ✅ Supported |
| `core_dispatch` | ✅ Supported |
| `wasabi_mdt` | ✅ Supported |
| `lb-tablet` | ✅ Supported |

### Inventory

Used for inventory reads, stash support, and item image helpers.

| Resource | Status |
|---|---|
| `ox_inventory` | ✅ Supported |
| `ak47_inventory` | ✅ Supported |
| `qs-inventory` | ✅ Supported |
| `qb-inventory` | ✅ Supported |
| `lj-Inventory` | ✅ Supported |
| `ps-inventory` | ✅ Supported |
| `pappu-inventorynp` | ✅ Supported |
| `codem-inventory` | ✅ Supported |

### Target

Used for target interaction support.

| Resource | Status |
|---|---|
| `ox_target` | ✅ Supported |
| `qb-target` | ✅ Supported |
| `qtarget` | ✅ Supported |

### Vehicle Keys

Used for key ownership and vehicle access support.

| Resource | Status |
|---|---|
| `wasabi_carlock` | ✅ Supported |
| `ak47_vehiclekeys` | ✅ Supported |
| `qs-vehiclekeys` | ✅ Supported |
| `vehicles_keys` | ✅ Supported |
| `msk_vehiclekeys` | ✅ Supported |
| `Renewed-Vehiclekeys` | ✅ Supported |
| `qbx_vehiclekeys` | ✅ Supported |
| `qb-vehiclekeys` | ✅ Supported |
| `cd_garage` | ✅ Supported |

### Vehicle Fuel

Used for fuel level support and refuel helpers.

| Resource | Status |
|---|---|
| `ox_fuel` | ✅ Supported |
| `msk_fuel` | ✅ Supported |
| `ti_fuel` | ✅ Supported |
| `TAM_Fuel` | ✅ Supported |
| `LegacyFuel` | ✅ Supported |
| `cdn-fuel` | ✅ Supported |
| `rcore_fuel` | ✅ Supported |
| `lyre_fuel` | ✅ Supported |
| `lc_fuel` | ✅ Supported |

### Sounds

Used for URL and positional audio support.

| Resource | Status |
|---|---|
| `xsound` | ✅ Supported |
| `mx-surround` | ✅ Supported |

### Phone

Used for phone and mail integrations.

| Resource | Status |
|---|---|
| `okokPhone` | ✅ Supported |
| `qb-phone` | ✅ Supported |
| `qs-smartphone` | ✅ Supported |
| `qs-smartphone-pro` | ✅ Supported |
| `lb-phone` | ✅ Supported |
| `gksphone` | ✅ Supported |

### Notification

Used for notify helpers.

| Resource | Status |
|---|---|
| `fs_bridge` | ✅ Supported |
| `ox_lib` | ✅ Supported |
| `esx_notify` | ✅ Supported |
| `es_extended` | ✅ Supported |
| `qb-core` | ✅ Supported |

### Text UI

Used for text UI helpers.

| Resource | Status |
|---|---|
| `fs_bridge` | ✅ Supported |
| `ox_lib` | ✅ Supported |
| `esx_textui` | ✅ Supported |
| `es_extended` | ✅ Supported |
| `qb-core` | ✅ Supported |

### Progressbar

Used for progress helper support.

| Resource | Status |
|---|---|
| `ox_lib` | ✅ Supported |
| `esx_progressbar` | ✅ Supported |
| `qb-core` | ✅ Supported |
| `mythic_progbar` | ✅ Supported |

## Need A Custom Integration?

If your resource is not listed above:

- do not edit locked Bridge files for a normal setup
- use the [Overrides](overrides/README.md) docs
- paste custom logic into your unlocked override files only
