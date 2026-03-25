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

<mark style="color:yellow;">fs\_trapphone/client/unlocked.lua</mark>

### Notification:

Notification can be changed in this function

```lua
--bydefault we add ox_lib notification you can edit according to your need
function notification(title, text, duration, type, icon)    
        lib.notify({
            title = title,
            description = text,
            type = type,
            duration = duration,
            icon = icon,
            position = 'top'
        })
end
```

### TextUi:

Textui can be changed in these functions

```lua
--by default we add ox lib textui

function TextUi(text)
    if text then
    --for show textui comment bottom line and add ur own
        lib.showTextUI(text)
    else
    --for remove tesxtui comment bottom line and add ur own
        lib.hideTextUI()
    end
end
```

### Police Dispatch:

for police dispatch calls you can change modify this function&#x20;

```lua
--by default we already setup qs-dispatch,cd_dispatch,op-dispatch
--if you want to use any of your own then modify this function

function dispach(coords)
     -- change only if you know what you are doing
    if GetResourceState('qs-dispatch') == 'started' then
        exports['qs-dispatch']:DrugSale()
    elseif GetResourceState('cd_dispatch') == 'started' then
        local data = exports['cd_dispatch']:GetPlayerInfo()
        TriggerServerEvent('cd_dispatch:AddNotification', {
            job_table = {'police', }, 
            coords = data.coords,
            title = '10-15 - Drug Selling',
            message = 'A '..data.sex..' selling drug at '..data.street, 
            flash = 0,
            unique_id = data.unique_id,
            sound = 1,
            blip = {
                sprite = 431, 
                scale = 1.2, 
                colour = 3,
                flashes = false, 
                text = '911 - Drug Sale',
                time = 5,
                radius = 0,
            }
        })
    elseif GetResourceState('op-dispatch') == 'started' then
        local job = "police" -- Jobs that will recive the alert
        local text = "A drug deal progress at"..GetStreetNameAtCoord(coords.x, coords.y, coords.z) -- Main text alert
        local coordinates = coords -- Alert coords
        local id = cache.serverId -- Player that triggered the alert
        local title = "Drug Deal" -- Main title alert
        local panic = false -- Allow/Disable panic effect
        TriggerServerEvent('Opto_dispatch:Server:SendAlert', job, title, text, coordinates, panic, id)
    else
        TriggerServerEvent('fs_trapphone:dispach', coords)
    end
end
```

### Third Eye Target System

by default we added ox target as target system but if you want to add any other target system then you can modify this&#x20;

```lua
function RegisterTarget(entity)
    local options = {
        label = 'Sell Drugs',
        name = 'selldrug',
        icon = 'fa-solid fa-capsules',
        canInteract = function (entity, distance)
            if distance <= 2.0 then
                return true
            end
        end,
        onSelect = function ()
            RemoveTarget(entity)
            SellDrugTarget()
        end
    }
    exports.ox_target:addLocalEntity(entity, options)
end

function RemoveTarget(entity)
    exports.ox_target:removeLocalEntity(entity, {'selldrug'})
end
```

## <mark style="color:green;">Server Side:</mark>

### Unlocked File Path:

<mark style="color:yellow;">fs\_trapphone/server/unlocked.lua</mark>

### Active Jobs needed

if you want to change logic of active jobs you can modify this functions according to ur need

```lua
lib.callback.register('fs_trapphone:joblogic', function(source)
    local _source = source
    local xPlayer = xPlayer(_source)
    local callback = false

    if Config.jobsNeeded.enable then 
      for name, count in pairs(Config.jobsNeeded.jobs) do
          local xPlayers = ESX.GetExtendedPlayers("job", name)

          if #xPlayers >= count then
              callback = true
              break
          else
              callback = false
          end
      end
      return callback
    else
      return true
    end
end)

```

### XP System/ Give Something on specific item sell

modify this function if you want to apply ur xp system or want to give something or item on each item sell

```lua
--
--only trigger on successfully sell of drug for xp system etc
AddEventHandler('fs_trapphone:onDrugSell',function (serverId,itemname,quantity)
  
  -- code something if u want otherwise don't touch it if you dont know what its mean
end)

```
