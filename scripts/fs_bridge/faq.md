# FAQ

## Do I need to edit locked bridge files?

No. Normal users should work through:

- public `FWB.*` APIs
- `config/sh_config.lua`
- `unlocked/client.lua`
- `unlocked/server.lua`

## Should I document deprecated wrappers in new resources?

No. Deprecated wrappers may still exist for compatibility, but new docs and new code should use the clean public namespaces.

## When should I write an override?

Write an override when:

- your resource is unsupported
- auto-detect cannot resolve your setup
- you need a custom integration behavior

## When should I not write an override?

Do not write one when:

- your resource is already supported
- the public API already does what you need
- the change belongs to normal config selection instead

## Where do I paste override snippets?

Client snippets go in `unlocked/client.lua`.

Server snippets go in `unlocked/server.lua`.

## What should new scripts call?

Use public names such as:

- `FWB.Player.Job.Name()`
- `FWB.Blip.Create(options)`
- `FWB.Ped.Create(options)`
- `FWB.Vehicle.Create(...)`
- `FWB.Entity.Vehicle.Closest(extras)`
