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

This section lists the active override functions currently used by the local Bridge build.

Use these pages when your setup needs custom compatibility that is not already covered by normal public support.

## Where Manual Compatibility Code Goes

Client side:

```lua
fs_bridge/unlocked/client.lua
```

Server side:

```lua
fs_bridge/unlocked/server.lua
```

## Pages

| Page | What It Covers |
|---|---|
| [Client Overrides](client-overrides.md) | All client-side manual compatibility overrides |
| [Server Overrides](server-overrides.md) | All server-side manual compatibility overrides |
