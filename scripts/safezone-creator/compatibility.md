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

# Compatibility

This page lists the framework, inventory, and zone engine resources currently supported by Safezone Creator.

## Framework

| # | Framework | Resource Name | Status |
| --- | --- | --- | --- |
| 1 | `ESX` | `es_extended` | :white_check_mark: Supported |
| 2 | `QBCore` | `qb-core` | :white_check_mark: Supported |
| 3 | `Qbox` | `qbx_core` | :white_check_mark: Supported |

## Inventory

| # | Inventory | Resource Name | Status |
| --- | --- | --- | --- |
| 1 | Ox Inventory | `ox_inventory` | :white_check_mark: Supported |
| 2 | AK47 Inventory | `ak47_inventory` | :white_check_mark: Supported |
| 3 | QS Inventory | `qs-inventory` | :white_check_mark: Supported |
| 4 | Tgiann Inventory | `tgiann-inventory` | :white_check_mark: Supported |
| 5 | Origen Inventory | `origen_inventory` | :white_check_mark: Supported |
| 6 | QB Inventory | `qb-inventory` | :white_check_mark: Supported |
| 7 | PS Inventory | `ps-inventory` | :white_check_mark: Supported |
| 8 | LJ Inventory | `lj-inventory` | :white_check_mark: Supported |
| 9 | Codem Inventory | `codem-inventory` | :white_check_mark: Supported |
| 10 | Core Inventory | `core_inventory` | :white_check_mark: Supported |

## Zone Engine Resources

| # | Zone Engine | Resource Name | Status |
| --- | --- | --- | --- |
| 1 | ox\_lib Zones | `ox_lib` | :white_check_mark: Supported |
| 2 | PolyZone | `PolyZone` | :white_check_mark: Supported |

## Notes

* Auto mode prefers the built-in `ox_lib` zone flow when available.
* PolyZone is supported as a fallback zone engine.
* Safezone Creator includes its own internal bridge layer for frameworks, inventories, notifications, and zone handling.
* Check installation order before setup so dependencies are already started.
