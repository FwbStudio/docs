# Server Config (`sv_config.lua`)

`config/sv_config.lua` contains server-side settings used by Bridge for framework-related database handling and generated vehicle plates.

## Top-Level Sections

| Key | Purpose |
|---|---|
| `framework` | Framework database identifier rules |
| `vehicle_plate` | Generated plate format |

## Framework Database Settings

The current file exposes these server-side framework blocks:

| Framework | Main Settings |
|---|---|
| `ESX` | `char_prefix`, `table_size`, `identifier_columns` |
| `QBCore` | `table_size`, `identifier_columns` |

### What These Values Control

- `char_prefix` defines the character prefix used by ESX-style identifiers
- `table_size` is used by Bridge for database table handling
- `identifier_columns` lists the DB columns Bridge should check for ownership and character identifiers

## Vehicle Plate Pattern

The current file also defines:

```lua
vehicle_plate = {
    pattern = "AAA 9999"
}
```

The current comments in the file show examples such as:

- `AAAA9999`
- `9999AAAA`
- `AA999AA`
- `AAA-9999`
- `AAA 9999`

This setting controls how Bridge-generated vehicle plates are formatted.

## Important Note

Only change `sv_config.lua` if you understand how your framework database and vehicle plate rules are expected to behave.
