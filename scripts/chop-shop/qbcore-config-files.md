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
# \[QBCore] Config Files

{% code title="QBCore Config" lineNumbers="true" fullWidth="true" %}

```lua
Config = Config or {}

Config.framework_core = { esx = 'es_extended', qb = 'qb-core'}

Config.Debug = false -- to enable extra information help in fixing errors

Config.DeletePermanent = false -- on choping player owned vehicle it will be permanently removed from player data

Config.AnimTime = 5 --in seconds -- animation time of removing parts in seconds

Config.Price = {
    door = 20,  --price for each door part
    bonnet = 10,    -- price for each bonnet part
    boot = 15,  --price for boot part
    vehicle = 1500  --price for vehicle purchased by alan
}

Config.items = {
    door = 'fs_door',
    bonnet = 'fs_bonnet',
    boot = 'fs_boot'
}

-- true means blacklist and cannot be scrapped
Config.blacklistmodels = {
    ['t20'] = false,
    ['blista'] = false,
    ['bifta'] = false,
    
}

Config.DispatchJobs = {
    ['police'] = true,
    ['sheriff'] = true,
    ['statepolice'] = true,
}

-- true means blacklist and cannot be scrapped
Config.blacklistClasses = {
    [0] = false,               --Compacts  
    [1] = false,               --Sedans  
    [2] = false,               --SUVs  
    [3] = false,               --Coupes  
    [4] = false,               --Muscle  
    [5] = false,               --Sports Classics  
    [6] = false,               --Sports  
    [7] = false,               --Super  
    [8] = false,               --Motorcycles  
    [9] = false,               --Off-road  
    [10] = false,               --Industrial  
    [11] = false,               --Utility  
    [12] = false,               --Vans  
    [13] = false,               --Cycles  
    [14] = false,               --Boats  
    [15] = false,               --Helicopters  
    [16] = false,               --Planes  
    [17] = false,               --Service  
    [18] = false,               --Emergency  
    [19] = false,               --Military  
    [20] = false,               --Commercial  
    [21] = false,               --Trains  
    [22] = false,               --Open Wheel
        
}
-- true means blacklist and cannot be scrapped
Config.blacklistplates = {
    ['police'] = true,
    ['admincar'] = false,
    ['ambulance'] = true,
}
 

Config.Stations = {
    [1] = {
        Blip = { enable = true, coords = vector3(-425.2820, -1688.6230, 19.0219 ), title = 'Scaper Chop Shop', id = 527, color = 31, scale = 0.7 },
        Allowed = { npcvehicles = true, playervehicles = true, alert_police = true },
        need_job = {
            enable = true, -- to disbale this option u can false it
            jobname = { -- any of sitation meet will allow player to start choping
                ['police'] = 1, -- ['jobname'] = active_player_count_needed
                ['sheriff'] = 1,
            },
            }, --if mininum number of this job  member needed to scrap
        ScapPoints = {  -- configuration points
            startpoint = vector3(-425.2820, -1688.6230, 19.0219 ) , --starting process on vehicle at this point 
            doordrop = vector3(-416.4831, -1677.1935, 19.0291 ),   --store door
            bootdrop = vector3(-419.5987, -1676.0206, 19.0291 ),   --store boot
            bonnetdrop = vector3(-423.6266, -1674.7255, 19.0292 ),  --store bonnets
            SellScap = vector3(-413.2837, -1679.3021, 19.0291 ),     -- collect or sell scap that store in door boot or bonnets
            
            sellSiemon = vector3(-429.2665, -1686.2042, 19.0291 ), -- point where to call Ped to take vehicle
            SiemonSpawn = vector3(-433.3221, -1673.4714, 19.0291 ),  --ped spawn location that will take vehicle and run away
        },
        --if only job player can do then uncomment bottom
        Job = {enable = false, name = 'scraper', boss = vector3(-426.3301, -1670.7089, 19.0291 )} ---this is optional
    }
}
 

-- exports['fs_chopshop']:addplateblacklist(GetVehiclePlateType(vehicle))
```

{% endcode %}
