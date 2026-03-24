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

# &#10227; Compatibility

This page shows the frameworks and integrations that currently have public Bridge support.

| &#9989; Officially Supported | &#9989; Supported | &#9888;&#65039; Supported |
|---|---|---|
| Verified compatibility and public Bridge support are available for this resource. | Bridge includes support for this resource in normal public setup. | Compatibility may exist in code, but it should be checked carefully before relying on it. |

| &#9940; Not Supported | &#128339; Soon... |
|---|---|
| Resource is not supported in the normal public setup flow. Use overrides instead. | We may add public support in a future update. |

## &#9881; Supported Frameworks

| Framework | Status | Resource Name |
|---|---|---|
| `ESX` | &#9989; Officially Supported | `es_extended` |
| `QBCore` | &#9989; Officially Supported | `qb-core` |
| `Qbox` | &#9989; Officially Supported | `qbx_core` |

## &#128268; Integration Compatibility

All integration groups below follow the same public setup rule:

- keep `selected_key = 1` for auto-detect
- only force a specific resource if support tells you to
- use overrides if your exact resource is not listed

### &#128657; Ambulance

Used for downed-state and ambulance compatibility.

| Resource | Status |
|---|---|
| `esx_ambulancejob` | &#9989; Supported |
| `wasabi_ambulance` | &#9989; Supported |
| `qb-ambulancejob` | &#9989; Supported |
| `ak47_ambulancejob` | &#9989; Supported |
| `tk_ambulancejob` | &#9989; Supported |
| `p_ambulancejob` | &#9989; Supported |

### &#127974; Banking

Used for society banking and bank-related helpers.

| Resource | Status |
|---|---|
| `okokBanking` | &#9989; Supported |
| `qb-banking` | &#9989; Supported |
| `Renewed-Banking` | &#9989; Supported |
| `qb-management` | &#9989; Supported |
| `tgg-banking` | &#9989; Supported |
| `qs_banking` | &#9989; Supported |
| `fd_banking` | &#9989; Supported |

### &#128085; Clothing

Used for clothing, appearance, and skin-related helpers.

| Resource | Status |
|---|---|
| `skinchanger` | &#9989; Supported |
| `fivem-appearance` | &#9989; Supported |
| `illenium-appearance` | &#9989; Supported |
| `rcore_clothing` | &#9989; Supported |
| `qb-clothing` | &#9989; Supported |
| `crm-appearance` | &#9989; Supported |
| `p_appearance` | &#9989; Supported |
| `qs-appearance` | &#9989; Supported |

### &#128680; Dispatch

Used for alerts, police notifications, and dispatch integrations.

| Resource | Status |
|---|---|
| `cd_dispatch` | &#9989; Supported |
| `ps-dispatch` | &#9989; Supported |
| `qs-dispatch` | &#9989; Supported |
| `tk_dispatch` | &#9989; Supported |
| `rcore_dispatch` | &#9989; Supported |
| `core_dispatch` | &#9989; Supported |
| `wasabi_mdt` | &#9989; Supported |
| `lb-tablet` | &#9989; Supported |

### &#127890; Inventory

Used for inventory reads, stash support, and item image helpers.

| Resource | Status |
|---|---|
| `ox_inventory` | &#9989; Supported |
| `ak47_inventory` | &#9989; Supported |
| `qs-inventory` | &#9989; Supported |
| `qb-inventory` | &#9989; Supported |
| `lj-Inventory` | &#9989; Supported |
| `ps-inventory` | &#9989; Supported |
| `pappu-inventorynp` | &#9989; Supported |
| `codem-inventory` | &#9989; Supported |

### &#127919; Target

Used for target interaction support.

| Resource | Status |
|---|---|
| `ox_target` | &#9989; Supported |
| `qb-target` | &#9989; Supported |
| `qtarget` | &#9989; Supported |

### &#128273; Vehicle Keys

Used for key ownership and vehicle access support.

| Resource | Status |
|---|---|
| `wasabi_carlock` | &#9989; Supported |
| `ak47_vehiclekeys` | &#9989; Supported |
| `qs-vehiclekeys` | &#9989; Supported |
| `vehicles_keys` | &#9989; Supported |
| `msk_vehiclekeys` | &#9989; Supported |
| `Renewed-Vehiclekeys` | &#9989; Supported |
| `qbx_vehiclekeys` | &#9989; Supported |
| `qb-vehiclekeys` | &#9989; Supported |
| `cd_garage` | &#9989; Supported |

### &#9981; Vehicle Fuel

Used for fuel level support and refuel helpers.

| Resource | Status |
|---|---|
| `ox_fuel` | &#9989; Supported |
| `msk_fuel` | &#9989; Supported |
| `ti_fuel` | &#9989; Supported |
| `TAM_Fuel` | &#9989; Supported |
| `LegacyFuel` | &#9989; Supported |
| `cdn-fuel` | &#9989; Supported |
| `rcore_fuel` | &#9989; Supported |
| `lyre_fuel` | &#9989; Supported |
| `lc_fuel` | &#9989; Supported |

### &#128266; Sounds

Used for URL and positional audio support.

| Resource | Status |
|---|---|
| `xsound` | &#9989; Supported |
| `mx-surround` | &#9989; Supported |

### &#128241; Phone

Used for phone and mail integrations.

| Resource | Status |
|---|---|
| `okokPhone` | &#9989; Supported |
| `qb-phone` | &#9989; Supported |
| `qs-smartphone` | &#9989; Supported |
| `qs-smartphone-pro` | &#9989; Supported |
| `lb-phone` | &#9989; Supported |
| `gksphone` | &#9989; Supported |

### &#128276; Notification

Used for notify helpers.

| Resource | Status |
|---|---|
| `fs_bridge` | &#9989; Supported |
| `ox_lib` | &#9989; Supported |
| `esx_notify` | &#9989; Supported |
| `es_extended` | &#9989; Supported |
| `qb-core` | &#9989; Supported |

### &#128172; Text UI

Used for text UI helpers.

| Resource | Status |
|---|---|
| `fs_bridge` | &#9989; Supported |
| `ox_lib` | &#9989; Supported |
| `esx_textui` | &#9989; Supported |
| `es_extended` | &#9989; Supported |
| `qb-core` | &#9989; Supported |

### &#8987; Progressbar

Used for progress helper support.

| Resource | Status |
|---|---|
| `ox_lib` | &#9989; Supported |
| `esx_progressbar` | &#9989; Supported |
| `qb-core` | &#9989; Supported |
| `mythic_progbar` | &#9989; Supported |

## &#128295; Need A Custom Integration?

If your resource is not listed above:

- do not edit locked Bridge files for a normal setup
- use the [Overrides](overrides/) docs
- paste custom logic into your unlocked override files only
