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
Config = {}

local seconds = 1000

Config.Target = false -- by default we support ox target else u can configure your own in unlocked.lua

Config.Drugs = {
    -- { name = 'drugname', quantity = max quantity can sell, price = price of single drug}
    -- for random make sure to add {min = minvalue, max = maxvalue} like i put in first example
    
    { -- example if you want quantity and price both randomly choosed
        name = 'water',
        quantity = { min = 10, max = 15, },
        price = { min = 10, max = 15 },
        prop = {model = "prop_cs_script_bottle_01", rot = vec3(0.13, 0.02, 0.0), pos = vec3(-90.0, 0, 0)},
        
    },
    {-- example if you want quantity and price both fixed choosed
        name = 'bread',
        quantity = 2,
        price = 10,
        prop = {model = "prop_weed_bottle", rot = vec3(0.13, 0.02, 0.0), pos = vec3(-90.0, 0, 0)},
    },                    
    { -- example if you want quantity fixed and price random
        name = 'lockpick',
        quantity = 2,
        price = { min = 10, max = 15 },
        prop = {model = "prop_weed_bottle", rot = vec3(0.13, 0.02, 0.0), pos = vec3(-90.0, 0, 0)},
    }, 

}

Config.Dispatch = {
    enable = true,-- if u want to use it then put your export into /client/unlocked.lua   --its a client side function
    --any dispach call work only if you configure it 
    notifyOnMakingCall = false, -- this notify when player will choose any option to sell
    --in case of custom edit in client/utils.lua
    jobs = {
        ['police'] = true,
        ['sheriff'] = true,
        ['statepolice'] = true,
    }
}

Config.TrapPhone = {
    item = {
        enable = true,
        itemname = 'fs_trapphone',
        removeOnUse = false,
    },
    command = {
        enable = false,
        commandname = 'trapphone',
    }
}

--limit number of drugs turn can make with clients on each restart 
Config.LimitedCalls = {
    enable = false,          --enable to disable this feature
    limit = 50,     --player can only sell drugs on this limit on each restart it will be reset automatically
    command = 'checklimit', --command to check how many calls you made out of total limit
}

Config.Account = 'money' -- money,bank,black_money any custom currency can be

--can ped reject
Config.Reject = {
    enable = true,
    perentage = 25,
    notifyOnReject = true, -- if your want to enable it please configure dispach function first put your export into /shared/utils.lua line 21 --its a client side function
}

-- if job needed to sell --
-- ['jobname'] = required job persons
-- ['police'] = 2
Config.jobsNeeded = {
    enable = false,
    jobs = {
        --this example shows script either needed 2 poilice active or 4 state police active
        ['police'] = 2,
        ['statepolice'] = 4,

    }
}

Config.buyer = {
    walkspeed = 1.2,         -- walk speed of buyers
    nextped = 1 * seconds,  --after how many seconds player will recieve next call from clients
    sendtext = 3 * seconds, -- how many seconds player will be in text animations
    makecall = 5 * seconds, -- how many seconds player will be in call animations
    cooldown = 10 * seconds, -- if player didnot respawn to ped in betweeen cooldown then ped will be removed automatic to match either player is afk
}

Config.seller = {
    cangofar = 10, -- player can go far from destination coordinates untill ped is coming if player go far from this buyer will be deleted automatically   
}


-- for developers only!!!

Config.ProgressBar = {
    text = {       
        position = 'bottom',    -- 'middle' , 'bottom'
        anim = {
            dict = 'anim@amb@nightclub@peds@',
            clip = 'amb_world_human_stand_mobile_male_text_idle_b',
        },
        prop = {
            bone = 28422,
            model = `prop_npc_phone_02`,
            pos = vec3(0.0, 0.0, 0.0),
            rot = vec3(0.0, 0.0, 0.0)
        }
    },
    call = {
        position = 'bottom',-- 'middle' , 'bottom'
        anim = {
            dict = 'cellphone@',
            clip = 'cellphone_call_listen_base',
        },
        prop = {
            bone = 28422,
            model = `prop_npc_phone_02`,
            pos = vec3(0.0, 0.0, 0.0),
            rot = vec3(0.0, 0.0, 0.0)
        }
    }
}
 
Config.argueAnim = {
    enable = true,  --argue anim before selling anims
    argueTime = 6 * seconds, --time for argue anim
}


Config.ClientBlip = {
    enable = true,
    title = 'Client',
    sprite = 286,
    color = 5,
    scale = 0.7,
    shortrange = true,
}

Config.SellingArea = {  
    enable = false, --if enable = true then player will only able to sell drug in these zones radius
    Zones = {
        [1] = {
            allowed = { 'lockpick'},   -- allowed multiple drugs to zone
            center_coords = vector3(407.8312, -1022.5469, 29.3633),
            radius = 50,
        },
        [2] = {
            allowed = {'all'}, -- allowed all drugs in this zone
            center_coords = vector3(296.5193, -1066.2914, 29.3210),
            radius = 50,
        },
        [3] = {
            allowed = {'water'}, -- allowed only 1 drug in this zone
            center_coords = vector3(242.9077, -1021.8730, 29.1140),
            radius = 50,
        },
    }
}


--write peds here mainly its for anticheat whitelist
Config.PedList = {
    'g_m_y_ballaeast_01',
    'g_m_y_ballaorig_01',
    'g_m_y_ballasout_01',
    'g_f_y_families_01',
    'g_m_y_famca_01',
    'g_m_y_famdnf_01',
    'g_f_y_vagos_01',
    'g_m_y_mexgoon_01',
    'g_m_y_mexgoon_02',
    'g_f_y_lost_01',
    'g_m_y_lost_01',
    'g_m_y_lost_02',
    'u_m_y_baygor',
    'u_m_y_burgerdrug_01',
    'u_m_y_chip',

}

--ped spawn offsets
Config.Offsets = {
    [1] = { x = 0.0, y = 15.0 },
    [2] = { x = 0.0, y = -15.0 },
    [3] = { x = 15.0, y = 0.0 },
    [4] = { x = -15.0, y = 0.0 },
    [5] = { x = 15.0, y = 15.0 },
    [6] = { x = -15.0, y = 15.0 },
    [7] = { x = 15.0, y = -15.0 },
    [8] = { x = -15.0, y = -15.0 },
    [9] = { x = 0.0, y = 25.0 },
    [10] = { x = 0.0, y = -25.0 },
    [11] = { x = 25.0, y = 0.0 },
    [12] = { x = -25.0, y = 0.0 },
    [13] = { x = 25.0, y = 25.0 },
    [14] = { x = -25.0, y = 25.0 },
    [15] = { x = 25.0, y = -25.0 },
    [16] = { x = -25.0, y = -25.0 },
    [17] = { x = 0.0, y = 20.0 },
    [18] = { x = 0.0, y = -20.0 },
    [19] = { x = 20.0, y = 0.0 },
    [20] = { x = -20.0, y = 0.0 },
    [21] = { x = 20.0, y = 20.0 },
    [22] = { x = -20.0, y = 20.0 },
    [23] = { x = 20.0, y = -20.0 },
    [24] = { x = -20.0, y = -20.0 }
}
```

{% endcode %}
