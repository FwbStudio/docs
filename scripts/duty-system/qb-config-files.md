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
# \[QB] Config Files

{% code title="ESX Config" lineNumbers="true" fullWidth="true" %}

```lua
Config = {}

Config.framework_core = { esx = 'es_extended', qb = 'qb-core' }

Config.core_functions = {
    player_loaded = { esx = 'esx:playerLoaded', qb = 'QBCore:Client:OnPlayerLoaded' },
    player_unloaded = { esx = 'esx:onPlayerLogout', qb = 'QBCore:Client:OnPlayerUnload' },
    player_updatejob = { esx = 'esx:setJob', qb = 'QBCore:Client:OnJobUpdate' }
}

Config.target = true --false will use textui and true will use ox target/qb-target

Config.Admin = {
    enable = true,
    command = 'dutymenu',
    Groups = {
        ['admin'] = true,
		['god'] = true,
    },
    Identifier = {
        ['discord:628640109897711636'] = true,     -- discord id u can get from txadmin from players
        ['license:1c17a180cdad995771fea75248f0ed95569b9e6a'] = true, --any lic id u can get from txadmin
        ['AJK40853'] = true,                                         --qbcore citizen id from players table
        ['char1:1c17a180cdad995771fea75248f0ed95569b9e6a'] = true,   -- esx identifier from users table
		-- you add more 
	
    },
	--add this in server cfg
	--add_ace license:1c17a180cdad995771fea75248f0ed95569b9e6a "fs_dutysystem" allow #Capy
    
	Ace = 'fs_dutysystem'
}
 
Config.DutyPoints = {
    [1] = {
        department = 'LSPD',
        jobs = {
            onduty = 'police',
            offduty = 'offpolice', -- off duty job only needed for esx
        },
        ped = { enable = true, coords = vector4(-72.5268, -1820.8704, 26.9421, 230.5248), model = 's_m_m_ciasec_01'}
    },
    [2] = {
        department = 'EMS',
        jobs = {
            onduty = 'ambulance',
            offduty = 'offambulance', -- off duty job only needed for esx
        },
        ped = { enable = true, coords = vector4(-81.5411, -1832.2010, 27.0970, 226.0478), model = 's_m_m_doctor_01'}
    },



}

```

{% endcode %}

{% code fullWidth="true" %}

```
 Webhook lua also unlocked where you can put your webhook to get logs for each job seprately
```

{% endcode %}
