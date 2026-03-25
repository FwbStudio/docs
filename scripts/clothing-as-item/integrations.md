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
# Integrations

## <mark style="color:green;">Client Side:</mark>

### Unlocked File Path:

<mark style="color:yellow;">fs\_clothingitem/client/unlocked.lua</mark>

{% code title="unlocked.lua" lineNumbers="true" fullWidth="true" %}

```lua
RegisterNetEvent('fs_clothingitem:notify')
AddEventHandler('fs_clothingitem:notify', function(msg)
    lib.notify({
        title = 'Cloting Item',
        description = msg,
        type = 'info',
        icon = "fa-solid fa-shirt",
        duration = 5000,
    })
end)
 
function IsPlayerhandsup(ped)
    return IsPedCuffed(ped)
    or IsEntityPlayingAnim(ped, 'missminuteman_1ig_2', 'handsup_base', 3)
    or IsEntityPlayingAnim(ped, 'missminuteman_1ig_2', 'handsup_enter', 3)
    or IsEntityPlayingAnim(ped, 'random@mugging3', 'handsup_standing_base', 3)
end

function minigame()
    local success = lib.skillCheck({ 'easy', 'easy', 'easy' }, { 'a', 's', 'd', 'w' })
    return success
end

function isPlayerDead(ped, playerserverid)
    return IsPedDeadOrDying(ped, true)
end

function PlayAnim(ped, anim, dict, time)
    if Config.UseProgressbar then
        lib.progressCircle({
            duration = time,
            position = 'bottom',
            useWhileDead = false,
            canCancel = false,
            disable = {
                car = true,
            },
            anim = {
                dict = anim,
                clip = dict
            },
        })
    else
        RequestAnimDict(anim)
        while (not HasAnimDictLoaded(anim)) do Wait(0) end
        TaskPlayAnim(ped, anim, dict, 9.0, 10.0, time, 0, 1, true, true, true)
    end
end
```

{% endcode %}
