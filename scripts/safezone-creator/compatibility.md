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

| Framework | Resource Name | Status |
| --- | --- | --- |
| `ESX` | `es_extended` | Supported |
| `Qbox` | `qbx_core` | Supported |
| `QBCore` | `qb-core` | Supported |

## Inventory

| Inventory | Resource Name | Status |
| --- | --- | --- |
| Ox Inventory | `ox_inventory` | Supported |
| AK47 Inventory | `ak47_inventory` | Supported |
| QS Inventory | `qs-inventory` | Supported |
| Tgiann Inventory | `tgiann-inventory` | Supported |
| Origen Inventory | `origen_inventory` | Supported |
| QB Inventory | `qb-inventory` | Supported |
| PS Inventory | `ps-inventory` | Supported |
| LJ Inventory | `lj-inventory` | Supported |
| Codem Inventory | `codem-inventory` | Supported |
| Core Inventory | `core_inventory` | Supported |

## Zone Engine Resources

| Zone Engine | Resource Name | Status |
| --- | --- | --- |
| ox\_lib Zones | `ox_lib` | Supported |
| PolyZone | `PolyZone` | Supported |
| PolyZone | `polyzone` | Supported |

## Notes

* Auto mode prefers the built-in `ox_lib` zone flow when available.
* PolyZone is supported as a fallback zone engine.
* Check installation order before setup so dependencies are already started.
