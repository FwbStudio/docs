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


function OnEnterZone(self)
    local safezoneid = self.myid -- this is the id of the safezone
    local safezonesettings = self.settings 

end


function OnLeaveZone(self)
    local safezoneid = self.myid -- this is the id of the safezone
    local safezonesettings = self.settings 


end

function InsideZone(self)
    local safezoneid = self.myid -- this is the id of the safezone
    local safezonesettings = self.settings 


end


function DisarmWeapons() --disarm weapon function for safezone if u don't add this for ur inventory don't worry player not be able to shoot or aim
    
    --ox_inventory example
    --TriggerEvent('ox_inventory:disarm', true)
end
```

{% endcode %}
