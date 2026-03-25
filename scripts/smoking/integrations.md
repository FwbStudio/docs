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

<mark style="color:yellow;">fs\_smoking/client/unlocked.lua</mark>

```lua
function TextUi(text)
    if text then
        lib.showTextUI(text)
    else
        lib.hideTextUI()
    end
end
function notification(title, text, duration, type, icon)    
        lib.notify({
            title = title,
            description = text,
            type = type,
            duration = duration,
            icon = icon,
            position = 'top',
            iconColor = '#008000',
            iconAnimation = 'bounce'
        })
end

local disable = false
function DisableControls(bool)
    disable = bool
    CreateThread(function()
        while disable do
            DisablePlayerFiring(cache.ped, true)
            DisableControlAction(0, 44, true) --Q Cover
            DisableControlAction(0, 25, true) -- aim
            DisableControlAction(0, 36, true) -- input duck
            DisableControlAction(0, 106, true) -- vehicle mouse controls
            DisableControlAction(0, 223, true) -- l mouse button
            DisableControlAction(0, 229, true) -- r mouse button4
            DisableControlAction(0, 347, true) -- r mouse button
            DisableControlAction(0, 140, true)
	    DisableControlAction(0, 141, true)
	    DisableControlAction(0, 142, true)
	    DisableControlAction(0, 263, true)
	    DisableControlAction(0, 264, true)
            Wait(0)
        end
    end)
end
```
