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
# Exports / Functions

### Client Export:

If you want to add your function.&#x20;

<mark style="color:yellow;">fs\_whitewidow/client/unlocked.lua</mark>

```lua
-- you can change boss menu function here 
RegisterNetEvent(Settings.Prefix..':openbossaction')
AddEventHandler(Settings.Prefix..':openbossaction', function(job)
    TriggerEvent('esx_society:openBossMenu', job, function(data, menu)
        ESX.CloseContext()
    end, {wash = false})
end)
```
