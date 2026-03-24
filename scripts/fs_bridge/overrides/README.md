# Overrides

Overrides are for custom integrations that are not already covered by the built-in compatibility layer.

## Where Overrides Go

Paste client overrides into:

```lua
unlocked/client.lua
```

Paste server overrides into:

```lua
unlocked/server.lua
```

## Override Rules

- keep your edits inside the unlocked files
- use the public function names documented here
- only override what you need
- prefer supported integrations first

## How These Pages Are Organized

The override docs are grouped by public namespace or public feature area.

| Section | Covers |
|---|---|
| [Player Overrides](player-overrides/README.md) | Player state, job helpers, and player vehicle key flows |
| [Integration Overrides](integration-overrides/README.md) | Banking, clothes, dispatch, phone, sounds, and fuel customizations |

## Typical Override Shape

Most paste-in blocks follow this pattern:

```lua
function Override.SomeFunction(...)
    -- your custom integration here
end
```

If a supported resource already handles the job, you usually do not need an override at all.
