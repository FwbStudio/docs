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
# \[ESX/QB] Config Files

{% code title="ESX/QB Config" lineNumbers="true" fullWidth="true" %}

```lua
config = {}

config.WhitelistedWeapons = {
    [`weapon_pistol`] = true,
    --[`weapon_combatpistol`] = true,
}

config.WhitelistedJobWeapons = {
    police = {
    --    [`weapon_stungun`] = true,
    },
    ambulance = {
    --    [`weapon_carbinerifle`] = true,
    },
}

config.AdminCommand = {
    command = 'safezonemenu', -- manage safezones
    permission = {
        admingroups = {
            ['admin'] = true
        },
        jobgroups = {
            ['police'] = 0
        },
        aces = {
            ['safezonemenu'] = true,
        },
        identifiers = {
            ['lic:asasasa'] = true,
            ['discord:asasas'] = true,
        },
        characters = {
            ['char1:asasasasas'] = true,
            ['char2:asasasasas'] = true,
        }
    }
}

config.SafeZoneAdminWhitelist = { -- any player with these permissions can enter safezone as admin
    admingroups = {
        ['admin'] = true
    },
    jobgroups = {
        ['police'] = 0
    },
    aces = {
        ['safezonemenu'] = true,
    },
    identifiers = {
        ['lic:asasasa'] = true,
        ['discord:asasas'] = true,
    },
    characters = {
        ['char1:asasasasas'] = true,
        ['char2:asasasasas'] = true,
    }
}

config.Creation = {
    CamSettings = {
        MoveSpeed = {
            default = 0.15,
            shift = 1.0
        },
        Zone_min_thickness = 50
    },
    Controls = {
        forward = {
            label = "Forward +/-",
            -- S, W
            codes = { 33, 32 },
        },
        right = {
            label = "Right +/-",
            -- D , A
            codes = { 35, 34 },
        },
        up = {
            label = "Up +/-",
            --- Q , E
            codes = { 52, 51 },
        },
        shift = {
            label = "Shift",
            -- LEFT SHIFT
            codes = { 21 },
        },
        add_point = {
            label = "Add Point",
            -- LEFT MOUSE BUTTON
            codes = { 69 },
        },
        undo_point = {
            label = "Undo Last",
            -- RIGHT MOUSE BUTTON
            codes = { 70 },
        },
        heigh_point = {
            label = "Height +/-",
            -- SCROLL UP, SCROLL DOWN
            codes = { 335, 334 },
        },
        save = {
            label = "Save",
            -- ENTER
            codes = { 191 },
        },
        cancel = {
            label = "Cancel",
            -- BACKSPACE
            codes = { 194 },
        }
    }
}


config.Notification = {
    title = 'SafeZone',
    duration = 5000,
    icon = 'fa-solid fa-hand',
    iconColor = 'blue'
}
```

{% endcode %}
