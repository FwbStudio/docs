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
# \[QBCore] ALL Config Files

{% code title="QBCore Config" lineNumbers="true" fullWidth="true" %}

```lua

Config = {}

Config.Sharedobj = 'qb-core'

Config.Preset = {} -- Don't touch
-- add items inside preset folder

Config.SkinMenu = {
	['qb-clothing'] = false,			-- default qb script
    ['illenium-appearance'] = true,	-- https://github.com/iLLeniumStudios/illenium-appearance
    ['onex-creation'] = false,			-- https://onexscripts.tebex.io/package/6057678

	--if you don't see your menu name here you can open ticket to let us know which menu your using
}

Config.RobChain = { 
    command = { enable = false, command = 'robchain' },
    key = { enable = false, key = 'j' },
    needed = {				-- following stuff is needed if u make them true 
        target_handsup = true, -- target must have to handsup?
		can_rob_dead_target = true, 
        minigame = true
	}
}
```

{% endcode %}

{% code fullWidth="true" %}

```lua
 -- all preset files are also unlocked to setup clothing id and texture against each item you want to create
```

{% endcode %}
