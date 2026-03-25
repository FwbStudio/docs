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
# \[ESX] Config Files

{% code title="ESX Config" lineNumbers="true" fullWidth="true" %}

```lua
Config = {};

local seconds = 1000

Config.Switch = {
	removecommand = "r_switch",
	swap = {
		dict = "missmic4",
		anim = "michael_tux_fidget",
		duration = 5 * seconds
	}
}

Config.Switches = {
	['fs_switch'] 		= 	{ limitedUse = { enable = false	, count = 1 } },
    ['fs_redswitch'] 	= 	{ limitedUse = { enable = false	, count = 1 } },
	['fs_blueswitch'] 	= 	{ limitedUse = { enable = true	, count = 2 } },
	['fs_greenswitch'] 	= 	{ limitedUse = { enable = true	, count = 3 } },
	
	-- add more custom switch here
}

Config.Weapons = {
	{
		['without_switch'] 	= "WEAPON_COMBATPISTOL",
		['with_switch'] 	= "WEAPON_APPISTOL"
	},
	{
		['without_switch'] 	= "WEAPON_CARBINERIFLE",
		['with_switch'] 	= "WEAPON_SPECIALCARBINE"
    	},
	
	-- add more custom weapons here
};
 
```

{% endcode %}
