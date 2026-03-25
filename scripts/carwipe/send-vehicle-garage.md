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
# Send Vehicle Garage

### JG Garage :

{% code fullWidth="true" %}

```lua
-- Replace this function with same empty function in fs_carwipe/server/unlocked.lua
-- this function run for each vehicle after wipe successfully done
function AfterSuccessfullyWiped(plate, owned) -- this function will only run on after successfully wiping vehicle
    if owned then
        MySQL.update.await('UPDATE owned_vehicle SET in_garage = 1 WHERE plate = ?', {plate})
    end
end
```

{% endcode %}
