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
# Developer API

This section documents the public Bridge API that your own scripts can call through `fs_bridge`.

Use these pages in order:

| Page | What it covers |
|---|---|
| `How To Call` | Export access, `GetObject()`, and `import.lua` usage |
| `Cache` | Public cache access, updates, and listeners |
| `Callbacks` | Client and server callback registration and await helpers |
| `Player` | Player, job, status, and request helpers |
| `Vehicle` | Vehicle search, keys, fuel, props, runtime entries, and ownership helpers |
| `Clothing` | Client clothing helpers and clothing resource detection |
| `Blip` | Runtime blip creation, moving blips, and registry helpers |
| `Ped` | Runtime ped creation, updates, and registry helpers |
| `Entity` | Nearby and closest object, player, ped, and vehicle helpers |
| `Math` | Shared math helpers |
| `String` | Shared string helpers |
| `Table` | Shared table helpers |
| `Notify` | Client and server notify helpers |
| `Text UI` | Show and hide text UI helpers |
| `Set Clipboard` | Client clipboard helper |
| `Logger` | Server log creation helper |
| `Hacker` | Server kick and ban helper |
| `Points` | Client point helpers from `import.lua` |
| `Zones` | Client zone helpers from `import.lua` |
| `Version` | Version and latest-version helpers |

The pages below focus on the clean public API only. Deprecated calls and internal bridge structure are intentionally skipped unless they are important for compatibility notes.
