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

# Server

This page groups the main server-side developer docs for Bridge.

## Main Docs

| Page | What It Covers |
|---|---|
| [FWB.Vehicle](../api-reference/fwb-vehicle.md) | Vehicle runtime, ownership helpers, and server-managed flows |
| [FWB.Ped](../api-reference/fwb-ped.md) | Server-managed ped runtime where applicable |
| [FWB.Entity](../api-reference/fwb-entity.md) | Server-side nearby and entity helper methods where available |
| [Examples](../examples.md) | General developer usage examples |
| [Server Overrides](../guides/manual-compatibility/server-overrides.md) | Server-side manual compatibility snippets |

## Notes

- use public `FWB.*` names only
- prefer built-in support before manual compatibility
- paste server override code into `fs_bridge/unlocked/server.lua`
