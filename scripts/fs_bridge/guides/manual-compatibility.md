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

# Manual Compatibility

Use manual compatibility when your setup needs custom behavior that is not already covered by supported integrations.

## Where Manual Compatibility Code Goes

Client side:

```lua
unlocked/client.lua
```

Server side:

```lua
unlocked/server.lua
```

## When To Use Manual Compatibility

Use it when:

* your resource is unsupported
* auto-detect cannot resolve your setup
* your setup needs custom integration behavior

## When Not To Use Manual Compatibility

Do not use it when:

* your supported resource already works
* the issue is only config selection
* the problem is installation order, not missing functionality

## Next Step

Use the namespace pages in [Developer API](../developer-api/) to pick the correct override surface.
