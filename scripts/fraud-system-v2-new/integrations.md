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

### <mark style="color:red;">PATH :</mark> <mark style="color:yellow;">fs\_fraud/client/unlocked.lua</mark>

This file contain all functions you can edit like&#x20;

{% code fullWidth="true" %}

```lua

-- This function should return true if player can successfully place then item
-- this functions should return false if player cannot place the item

function CanPlaceItem()
    -- you can code here if your housing provide function that if player inside house then return false else return true

    --[[
    -- qs housing
    if GetResourceState == 'started' then
        if exports['qs-housing']:getCurrentHouse() then --if player in house then player will not be able to place item
            return false
        end
    end
    ]]



    return true
end



function Draw3DText(position, text)
    SetTextScale(0.35, 0.35)
    SetTextFont(4)
    SetTextProportional(1)
    SetTextColour(255, 255, 255, 215)
    SetTextEntry("STRING")
    SetTextCentre(true)
    AddTextComponentString(text)
    SetDrawOrigin(position.x, position.y, position.z, 0)
    DrawText(0.0, 0.0)
    local factor = (string.len(text)) / 370
    DrawRect(0.0, 0.0 + 0.0125, 0.017 + factor, 0.03, 0, 0, 0, 75) --comment this out to remove background on 3dtext
    ClearDrawOrigin()
end

function ShowHelpNotification(msg)
    BeginTextCommandDisplayHelp('STRING')
    AddTextComponentSubstringPlayerName(msg)
    EndTextCommandDisplayHelp(0, false, true, -1)
end

-----------------------------------------------------------------------------
--- Devices Minigames
--- minigames which used on clonning devices at thetime of clonning items
----------------------------------------------------------------------------
function ClonnedCard()
    if GetResourceState('magni-cardswipe') == 'started' then
        local promise = promise.new()
        exports["magni-cardswipe"]:cardswipe(
            function() -- success callback
                promise:resolve(true)
            end,
            function()         -- failure callback
                promise:resolve(false) -- or promise:reject("Swipe failed") if you want to reject instead
            end
        )
        local success = Citizen.Await(promise)
        return success
    end

    local success = StartDataCrack(3) -- 3 is the difficulty level (1-5)
    if not success then
        FWB.Notification("Failed to pass secureity check.")
        return false
    end
    return true
end

function ForgedCheque()
    local success = StartDataCrack(3) -- 3 is the difficulty level (1-5)
    if not success then
        FWB.Notification("Failed to pass secureity check.")
        return false
    end
    return true
end

function ClonnedGiftCard()
    local success = StartDataCrack(3) -- 3 is the difficulty level (1-5)
    if not success then
        FWB.Notification("Failed to pass secureity check.")
        return false
    end
    return true
end

function ClonnedLotteryTicket()
    local success = StartDataCrack(3) -- 3 is the difficulty level (1-5)
    if not success then
        FWB.Notification("Failed to pass secureity check.")
        return false
    end
    return true
end

function ClonnedSocialCard()
    if GetResourceState('magni-cardswipe') == 'started' then
        local promise = promise.new()
        exports["magni-cardswipe"]:cardswipe(
            function() -- success callback
                promise:resolve(true)
            end,
            function()         -- failure callback
                promise:resolve(false) -- or promise:reject("Swipe failed") if you want to reject instead
            end
        )
        local success = Citizen.Await(promise)
        return success
    end
    local success = StartDataCrack(3) -- 3 is the difficulty level (1-5)
    if not success then
        FWB.Notification("Failed to pass secureity check.")
        return false
    end
    return true
end

-----------------------------------------------------------------------------
--- Selling Minigames
--- minigames which used on selling points
----------------------------------------------------------------------------
function AtmMiniGame_clonnedcard()
    local success = StartDataCrack(3) -- 3 is the difficulty level (1-5)
    if not success then
        FWB.Notification("Failed to pass secureity check.")
        return false
    end
    return true
end

function AtmMiniGame_clonnedcheque()
    local success = StartDataCrack(3) -- 3 is the difficulty level (1-5)
    if not success then
        FWB.Notification("Failed to pass secureity check.")
        return false
    end
    return true
end

function BankerMiniGame_clonnedcheque()
    return true
end

function GiftMinigame_clonnedGiftcard()
    return true
end

function LotteryMinigame_clonnedGiftcard()
    return true
end

function SocialMinigame_clonnedSocialCard()
    return true
end

------------------------------------------------------------------------------------

--!disable controls when shop open
local disable = false
function DisableControls(bool)
    disable = bool
    CreateThread(function()
        local acounts = { 44, 1, 2, 25, 36, 63, 64, 71, 72, 75, 106, 200 }
        while disable do
            for i = 1, #acounts do
                DisablePlayerFiring(Cache.Ped, true)
                DisableControlAction(0, acounts[i], true)
            end
            Wait(0)
        end
    end)
end

--!disable controls when tablet open
local disabletablecontrol = false
function DisableTabletControls(bool)
    disabletablecontrol = bool
    CreateThread(function()
        local acounts = { 44, 25, 36, 63, 64, 71, 72, 75, 106, 200 }
        while disabletablecontrol do
            for i = 1, #acounts do
                DisablePlayerFiring(Cache.Ped, true)
                DisableControlAction(0, acounts[i], true)
            end
            Wait(0)
        end
    end)
end

--[[*
*
* Dispatch Function
*
]]

function Dispatch(argument, item_name)
    -- dispatch default called by fs_bridge incase if u you want edit your on ur own to edit here
    FWB.AddCustomDispatch(argument)
end

```

{% endcode %}

<br>
