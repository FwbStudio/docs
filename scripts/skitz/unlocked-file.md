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
# Unlocked FIle

{% code title="Client Side Unlocked File" lineNumbers="true" fullWidth="true" %}

```lua

function CanCraftItem(item)
    -- uncommment both bottom lines if you want to use minigame in crafting
    -- local success = lib.skillCheck('easy', {'e'})
    -- if not success then return false end

    return true
end

function Draw2DText(text)
    SetTextScale(0.4, 0.4)
    SetTextColour(255, 255, 255, 255)
    SetTextFont(4)
    SetTextDropShadow(0, 0, 0, 0, 255)
    SetTextProportional(1)
    SetTextCentre(true)
    BeginTextCommandWidth("STRING")
    AddTextComponentString(text)
    local height = GetTextScaleHeight(0.4, 4)
    local width = EndTextCommandGetWidth(4)
    SetTextEntry("STRING")
    AddTextComponentString(text)
    EndTextCommandDisplayText(0.50, 0.95)
    DrawText(0.50, 0.95)

    local factor = (string.len(text)) / 370
    DrawRect(0.50, 0.95 + 0.0130, 0.015 + factor, height + 0.011, 35, 35, 35, 200)
end

```

{% endcode %}
