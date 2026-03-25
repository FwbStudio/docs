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

# Client

This page groups the main client-side developer docs for Bridge.

## Main Docs

| Page | What It Covers |
|---|---|
| [FWB.Blip](../api-reference/fwb-blip.md) | Client blip helpers and runtime usage |
| [FWB.Ped](../api-reference/fwb-ped.md) | Client ped runtime and helper methods |
| [FWB.Entity](../api-reference/fwb-entity.md) | Nearby search and front-coord helpers |
| [FWB.Vehicle](../api-reference/fwb-vehicle.md) | Vehicle runtime methods used by client scripts |
| [Examples](../examples.md) | General developer usage examples |
| [Client Overrides](../guides/manual-compatibility/client-overrides.md) | Client-side manual compatibility snippets |

## Notes

- use public `FWB.*` names only
- prefer built-in support before manual compatibility
- paste client override code into `fs_bridge/unlocked/client.lua`
