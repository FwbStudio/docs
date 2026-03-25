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

<mark style="color:yellow;">fs\_whitewidow/client/unlocked.lua</mark>

{% code title="unlocked.lua" lineNumbers="true" fullWidth="true" %}

```lua
function Textui(msg)
    if msg then
        lib.showTextUI(msg)
    else
        lib.hideTextUI()
    end
end

function DrawText3D(coords, text, size, font)
    local onScreen, x, y = World3dToScreen2d(coords.x, coords.y, coords.z)
    local camCoords      = GetGameplayCamCoords()
    local dist           = GetDistanceBetweenCoords(camCoords, coords.x, coords.y, coords.z, true)
    local size           = size

    if size == nil then
        size = 1
    end

    local scale = (size / dist) * 2
    local fov   = (1 / GetGameplayCamFov()) * 100
    local scale = scale * fov

    if onScreen then
        SetTextScale(0.0 * scale, 0.55 * scale)
        SetTextFont(font)
        SetTextColour(255, 255, 255, 255)
        SetTextDropshadow(0, 0, 0, 0, 255)
        SetTextEdge(2, 0, 0, 0, 150)
        SetTextDropShadow()
        SetTextOutline()
        SetTextEntry('STRING')
        SetTextCentre(1)
        AddTextComponentString(text)
        DrawText(x, y)
    end
end

CreateThread(function()
    if Config.Shop.blip.enable then
        local coords = Config.Shop.blip.pos
        local radius = Config.Shop.blip.radius + 0.00
        local blipRd = AddBlipForRadius(coords, radius)
        SetBlipHighDetail(blipRd, true)
        SetBlipColour(blipRd, Config.Shop.blip.radius_color)
        SetBlipAlpha(blipRd, 128)
        SetBlipAsShortRange(blipRd, true)
        local blip = AddBlipForCoord(coords)
        SetBlipHighDetail(blip, true)
        SetBlipSprite(blip, Config.Shop.blip.sprite)
        SetBlipScale(blip, Config.Shop.blip.size)
        SetBlipColour(blip, Config.Shop.blip.color)
        SetBlipAsShortRange(blip, true)
        BeginTextCommandSetBlipName("STRING")
        AddTextComponentString(Config.Shop.blip.name)
        EndTextCommandSetBlipName(blip)
    end
end)
    
RegisterNetEvent(Settings.Prefix..':openbossaction')
AddEventHandler(Settings.Prefix..':openbossaction', function(job)
    TriggerEvent('esx_society:openBossMenu', job, function(data, menu)
        ESX.CloseContext()
    end, {wash = false})
end)

RegisterNetEvent(Settings.Prefix..':notify')
AddEventHandler(Settings.Prefix..':notify', function(msg)
    lib.notify({
        title = Settings.Label,
        description = msg,
        icon = "fa-solid fa-cannabis",
        type = 'inform',
        position = 'top',
        iconColor = '#8ba189',
        iconAnimation = 'beat'
    })
end)
```

{% endcode %}
