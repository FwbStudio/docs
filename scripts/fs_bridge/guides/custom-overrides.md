# Custom Overrides

Use overrides when your setup needs custom behavior that is not already covered by supported integrations.

## Where Override Code Goes

Client side:

```lua
unlocked/client.lua
```

Server side:

```lua
unlocked/server.lua
```

## When To Use Overrides

Use overrides when:

- your script is unsupported
- your setup needs custom status behavior
- your banking, phone, sound, dispatch, fuel, or keys flow is custom

## When Not To Use Overrides

Do not use overrides when:

- your supported resource already works
- the issue is only config selection
- the problem is start order, not missing functionality

## Next Step

Use the namespace pages in [Developer API](../developer-api/README.md) to pick the correct override surface.
