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

# ðŸ” Compatibility

This page shows the frameworks and integrations that currently have public Bridge support.

| âœ… Officially Supported                                                            | âœ… Supported                                                       | âš ï¸ Supported                                                                              |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Verified compatibility and public Bridge support are available for this resource. | Bridge includes support for this resource in normal public setup. | Compatibility may exist in code, but it should be checked carefully before relying on it. |

| â›” Not Supported                                                                   | ðŸ•“ Soon...                                    |
| --------------------------------------------------------------------------------- | --------------------------------------------- |
| Resource is not supported in the normal public setup flow. Use overrides instead. | We may add public support in a future update. |

## âš™ Supported Frameworks

| Framework | Status                 | Resource Name |
| --------- | ---------------------- | ------------- |
| `ESX`     | âœ… Officially Supported | `es_extended` |
| `QBCore`  | âœ… Officially Supported | `qb-core`     |
| `Qbox`    | âœ… Officially Supported | `qbx_core`    |

## ðŸ”Œ Integration Compatibility

All integration groups below follow the same public setup rule:

* keep `selected_key = 1` for auto-detect
* only force a specific resource if support tells you to
* use overrides if your exact resource is not listed

### ðŸš‘ Ambulance

Used for downed-state and ambulance compatibility.

| Resource            | Status      |
| ------------------- | ----------- |
| `esx_ambulancejob`  | âœ… Supported |
| `wasabi_ambulance`  | âœ… Supported |
| `qb-ambulancejob`   | âœ… Supported |
| `ak47_ambulancejob` | âœ… Supported |
| `tk_ambulancejob`   | âœ… Supported |
| `p_ambulancejob`    | âœ… Supported |

### ðŸ¦ Banking

Used for society banking and bank-related helpers.

| Resource          | Status      |
| ----------------- | ----------- |
| `okokBanking`     | âœ… Supported |
| `qb-banking`      | âœ… Supported |
| `Renewed-Banking` | âœ… Supported |
| `qb-management`   | âœ… Supported |
| `tgg-banking`     | âœ… Supported |
| `qs_banking`      | âœ… Supported |
| `fd_banking`      | âœ… Supported |

### ðŸ‘• Clothing

Used for clothing, appearance, and skin-related helpers.

| Resource              | Status      |
| --------------------- | ----------- |
| `skinchanger`         | âœ… Supported |
| `fivem-appearance`    | âœ… Supported |
| `illenium-appearance` | âœ… Supported |
| `rcore_clothing`      | âœ… Supported |
| `qb-clothing`         | âœ… Supported |
| `crm-appearance`      | âœ… Supported |
| `p_appearance`        | âœ… Supported |
| `qs-appearance`       | âœ… Supported |

### ðŸš¨ Dispatch

Used for alerts, police notifications, and dispatch integrations.

| Resource         | Status      |
| ---------------- | ----------- |
| `cd_dispatch`    | âœ… Supported |
| `ps-dispatch`    | âœ… Supported |
| `qs-dispatch`    | âœ… Supported |
| `tk_dispatch`    | âœ… Supported |
| `rcore_dispatch` | âœ… Supported |
| `core_dispatch`  | âœ… Supported |
| `wasabi_mdt`     | âœ… Supported |
| `lb-tablet`      | âœ… Supported |

### ðŸŽ’ Inventory

Used for inventory reads, stash support, and item image helpers.

| Resource            | Status      |
| ------------------- | ----------- |
| `ox_inventory`      | âœ… Supported |
| `ak47_inventory`    | âœ… Supported |
| `qs-inventory`      | âœ… Supported |
| `qb-inventory`      | âœ… Supported |
| `lj-Inventory`      | âœ… Supported |
| `ps-inventory`      | âœ… Supported |
| `pappu-inventorynp` | âœ… Supported |
| `codem-inventory`   | âœ… Supported |

### ðŸŽ¯ Target

Used for target interaction support.

| Resource    | Status      |
| ----------- | ----------- |
| `ox_target` | âœ… Supported |
| `qb-target` | âœ… Supported |
| `qtarget`   | âœ… Supported |

### ðŸ”‘ Vehicle Keys

Used for key ownership and vehicle access support.

| Resource              | Status      |
| --------------------- | ----------- |
| `wasabi_carlock`      | âœ… Supported |
| `ak47_vehiclekeys`    | âœ… Supported |
| `qs-vehiclekeys`      | âœ… Supported |
| `vehicles_keys`       | âœ… Supported |
| `msk_vehiclekeys`     | âœ… Supported |
| `Renewed-Vehiclekeys` | âœ… Supported |
| `qbx_vehiclekeys`     | âœ… Supported |
| `qb-vehiclekeys`      | âœ… Supported |
| `cd_garage`           | âœ… Supported |

### â›½ Vehicle Fuel

Used for fuel level support and refuel helpers.

| Resource     | Status      |
| ------------ | ----------- |
| `ox_fuel`    | âœ… Supported |
| `msk_fuel`   | âœ… Supported |
| `ti_fuel`    | âœ… Supported |
| `TAM_Fuel`   | âœ… Supported |
| `LegacyFuel` | âœ… Supported |
| `cdn-fuel`   | âœ… Supported |
| `rcore_fuel` | âœ… Supported |
| `lyre_fuel`  | âœ… Supported |
| `lc_fuel`    | âœ… Supported |

### ðŸ”Š Sounds

Used for URL and positional audio support.

| Resource      | Status      |
| ------------- | ----------- |
| `xsound`      | âœ… Supported |
| `mx-surround` | âœ… Supported |

### ðŸ“± Phone

Used for phone and mail integrations.

| Resource            | Status      |
| ------------------- | ----------- |
| `okokPhone`         | âœ… Supported |
| `qb-phone`          | âœ… Supported |
| `qs-smartphone`     | âœ… Supported |
| `qs-smartphone-pro` | âœ… Supported |
| `lb-phone`          | âœ… Supported |
| `gksphone`          | âœ… Supported |

### ðŸ”” Notification

Used for notify helpers.

| Resource      | Status      |
| ------------- | ----------- |
| `fs_bridge`   | âœ… Supported |
| `ox_lib`      | âœ… Supported |
| `esx_notify`  | âœ… Supported |
| `es_extended` | âœ… Supported |
| `qb-core`     | âœ… Supported |

### ðŸ’¬ Text UI

Used for text UI helpers.

| Resource      | Status      |
| ------------- | ----------- |
| `fs_bridge`   | âœ… Supported |
| `ox_lib`      | âœ… Supported |
| `esx_textui`  | âœ… Supported |
| `es_extended` | âœ… Supported |
| `qb-core`     | âœ… Supported |

### âŒ› Progressbar

Used for progress helper support.

| Resource          | Status      |
| ----------------- | ----------- |
| `ox_lib`          | âœ… Supported |
| `esx_progressbar` | âœ… Supported |
| `qb-core`         | âœ… Supported |
| `mythic_progbar`  | âœ… Supported |

## ðŸ”§ Need A Custom Integration?

If your resource is not listed above:

* do not edit locked Bridge files for a normal setup
* use the [Manual Compatibility](guides/manual-compatibility/README.md) docs
* paste custom logic into your unlocked override files only

