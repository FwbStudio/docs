# Configuration

`fs_bridge` is primarily configured through `config/sh_config.lua`.

This page documents the keys users are expected to change.

## Current Public Focus

The current public configuration docs focus on FiveM servers using:

- `ESX`
- `QBCore`
- `Qbox`

## Top-Level Sections

| Key | Purpose |
|---|---|
| `language` | Locale fallback |
| `debug` | Console visibility for bridge status and diagnostics |
| `framework` | Base framework event names and framework-specific behavior |
| `Vehicle` | Vehicle creation mode |
| `Ped` | Ped creation mode |
| Integration groups | Resource selection for ambulance, banking, clothing, dispatch, inventory, target, keys, fuel, sounds, phone, and UI helpers |

## Language

```lua
language = 'en'
```

If the requested locale is missing, the bridge falls back to English.

## Debug

| Key | What It Does |
|---|---|
| `show_detected_resources` | Prints detected integrations |
| `show_stopped_resources` | Prints resources stopped after bridge shutdown |
| `show_info_prints` | Prints framework and runtime info |
| `show_important_prints` | Prints warnings and errors |

## Framework

These are the main framework config branches currently covered in public docs:

| Framework | Main Config Keys |
|---|---|
| `ESX` | `core_script`, `update_player_job`, `load_player`, `unload_player` |
| `QBCore` | `core_script`, `update_player_job`, `load_player`, `unload_player`, `dirtymoney`, `bank` |
| `Qbox` | `core_script`, `update_player_job`, `load_player`, `unload_player`, `bank` |

## Runtime Creation Modes

### Vehicle

```lua
Vehicle = {
    create_vehicle_serverside = false
}
```

`true` creates vehicles server-side.

`false` creates vehicles client-side.

### Ped

```lua
Ped = {
    create_ped_serverside = false
}
```

`true` creates peds server-side.

`false` creates peds client-side.

## Integration Selector Pattern

Most integration groups follow the same format:

```lua
selected_key = 1
supported_keys = {
    { key = 1, resource = 'auto' },
    { key = 2, resource = 'some_resource' }
}
```

Rules:

- `selected_key = 1` means auto-detect
- any other key forces a specific supported resource
- new unsupported systems should be handled through override docs, not by editing locked bridge files

## Integration Groups In `sh_config`

| Group | Purpose |
|---|---|
| `Ambulance` | Downed and ambulance compatibility |
| `Bank` | Society banking integration |
| `Clothing` | Clothing and appearance integration |
| `Dispatch` | Alert and dispatch integration |
| `Inventory` | Inventory, stash, and item image support |
| `Target` | Target system integration |
| `VehicleKeys` | Vehicle key support |
| `VehicleFuel` | Fuel system support |
| `Sounds` | URL and positional audio support |
| `Phone` | Mail and phone integration |
| `Notification` | Notify resource selection |
| `TextUi` | Text UI resource selection |
| `Progressbar` | Progress bar resource selection |
