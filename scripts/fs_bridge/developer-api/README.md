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

The pages below focus on the clean public API only. Deprecated calls and internal bridge structure are intentionally skipped.