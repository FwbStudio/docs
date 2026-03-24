# Getting Started

This guide is for the normal `fs_bridge` setup flow.

## 1. Set Your Base Framework

Open `config/sh_config.lua` and confirm the framework event settings match the framework you actually run.

Supported base frameworks:

- `ESX`
- `QBCore`
- `VORP`

## 2. Review Auto-Detected Integrations

Most integration groups default to:

```lua
selected_key = 1
```

That means auto-detect.

Only change the key when you want to force a specific supported resource.

## 3. Decide How You Will Use The Bridge

Normal resource usage should call the public surface:

```lua
FWB.Player.Job.Name()
FWB.Vehicle.Create(...)
FWB.Blip.Create(...)
exports.fs_bridge:CreateVehicle(...)
```

Do not build new code around deprecated flat wrappers.

## 4. Only Override What You Actually Need

If your server uses a custom status, banking, dispatch, phone, sound, fuel, or vehicle key system, paste the override code from these docs into:

- `unlocked/client.lua`
- `unlocked/server.lua`

Do not edit locked bridge files for normal custom integrations.

## 5. Start With The Pages That Match Your Use Case

| If you need to... | Read |
|---|---|
| Configure supported integrations | [Configuration](../configuration/README.md) |
| Add custom hunger, thirst, or stress logic | [FWB.Player](../overrides/player-overrides/fwb-player.md) |
| Add custom keys or fuel logic | [FWB.Player.Vehicle](../overrides/player-overrides/fwb-player-vehicle.md) and [FWB.Vehicle.Fuel](../overrides/integration-overrides/fwb-vehicle-fuel.md) |
| Use runtime modules in scripts | [API Reference](../api-reference/README.md) |

## Recommended Workflow

1. Keep auto-detect on where possible.
2. Confirm the right framework and supported resource are active.
3. Use public `FWB.*` or export calls in your own scripts.
4. Add overrides only when your custom system is not already supported.
