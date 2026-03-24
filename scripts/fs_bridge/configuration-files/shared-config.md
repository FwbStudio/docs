# Shared Config (`sh_config.lua`)

`fs_bridge` is primarily configured through `config/sh_config.lua`.

This page is synced against the current Bridge config file and documents the public settings users are expected to change.

## Public Scope

The current public docs focus on FiveM usage.

Important note:

- the current `sh_config.lua` has explicit framework branches for `ESX` and `QBCore`
- there is not currently a separate public `Qbox` block exposed in this config file
- if your server uses a Qbox-based setup, only change framework values if support tells you to

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

If the requested locale is missing, Bridge falls back to English.

## Debug

| Key | What It Does |
|---|---|
| `show_detected_resources` | Prints detected integrations |
| `show_stopped_resources` | Prints resources stopped after Bridge shutdown |
| `show_info_prints` | Prints framework and runtime info |
| `show_important_prints` | Prints warnings and errors |

## Framework

These are the current public FiveM branches exposed in `sh_config.lua`:

| Framework | Main Config Keys |
|---|---|
| `ESX` | `core_script`, `update_player_job`, `load_player`, `unload_player` |
| `QBCore` | `core_script`, `update_player_job`, `load_player`, `unload_player`, `dirtymoney`, `bank` |

### QBCore Special Settings

The current QBCore branch also includes:

- `dirtymoney.item`
- `dirtymoney.metadata`
- `dirtymoney.bag_max_worth`
- `bank.societymoney_in_bank`

These settings control marked-bills handling and whether society money is handled through bank-based or boss-menu-based flows.

## Runtime Creation Modes

### Vehicle

```lua
Vehicle = {
    create_vehicle_serverside = false
}
```

- `true` creates vehicles server-side
- `false` creates vehicles client-side

### Ped

```lua
Ped = {
    create_ped_serverside = false
}
```

- `true` creates peds server-side
- `false` creates peds client-side

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
- do not add your own unsupported resources into `supported_keys`
- use Manual Compatibility and unlocked files for unsupported systems

## Integration Groups

| Group | Notes |
|---|---|
| `Ambulance` | Standard selector list only |
| `Bank` | Standard selector list only |
| `Clothing` | Standard selector list only |
| `Dispatch` | Includes `lb-tablet` with an `awake` option |
| `Inventory` | Supported entries also define item `image_path` values |
| `Target` | Standard selector list only |
| `VehicleKeys` | Includes `cd_garage` with an `awake` option |
| `VehicleFuel` | Standard selector list only |
| `Sounds` | Standard selector list only |
| `Phone` | Standard selector list only |
| `Notification` | Includes Bridge, framework, and library-based notify options |
| `TextUi` | Includes Bridge, framework, and library-based text UI options |
| `Progressbar` | Standard selector list only |

## Important Configuration Rule

If your supported resource is already listed, keep `selected_key = 1` unless support tells you to force a manual selection.
