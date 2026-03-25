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

Config.Whitelistedjobs = { -- No jamming for this job
     ['police'] = true,
     ['sheriff'] = true,
}

-- Config.Shoot = true means player will shoot while unjamming and can damage to near player
-- Config.Shoot = false means player will not gonna shoot while unjamming  
Config.Shoot = true

-- player copy paste weapon row if u want to add new weapon
Config.Weapons = {
  --  [`WEAPON_PISTOL`]       = {JamChance = 40, UnjamChance = 30},
    [`WEAPON_PISTOL`] = {JamChance = 40, UnjamChance = 100},                --name should be in capital latter 
    [`WEAPON_CARBINERIFLE`] = {JamChance = 30, UnjamChance = 100},    -- name should be in capital latter
    
}
 
Config.strings = {
  ['weapon_jammed'] = 'Your weapon is jammed',
  ['weapon_jammed_help'] = 'Press ~INPUT_CONTEXT~ to do unjamm weapon!',
  ['weapon_unjammed'] = 'Your weapon is unjammed',
  
}
    


RegisterNetEvent('fs_gunjaming:notification')
AddEventHandler('fs_gunjaming:notification',function (msg)
  ESX.ShowNotification(msg)
end)
 
function ShowHelpNotification(msg, thisFrame, beep, duration)
  AddTextEntry("fwbHelpNotification", msg)

  if thisFrame then
      DisplayHelpTextThisFrame("fwbHelpNotification", false)
  else
      if beep == nil then
          beep = true
      end
      BeginTextCommandDisplayHelp("fwbHelpNotification")
      EndTextCommandDisplayHelp(0, false, beep, duration or -1)
  end
end
```

{% endcode %}
