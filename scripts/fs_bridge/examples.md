# Examples

These examples use the clean public API.

## Create A Public Garage Blip

```lua
FWB.Blip.Create({
    source = -1,
    coords = vec3(-267.0, -959.0, 31.2),
    title = 'Public Garage',
    id = 357,
    scale = 0.8,
    color = 2
})
```

## Create A Guard Ped

```lua
FWB.Ped.Create({
    model = 's_m_m_security_01',
    coords = vec4(441.2, -981.9, 30.7, 90.0),
    freeze = true,
    invincible = true,
    blip = {
        title = 'Guard',
        id = 1,
        scale = 0.7,
        color = 2
    }
})
```

## Create A Vehicle With Keys And Fuel

```lua
local created = FWB.Vehicle.Create(source, 'adder', {
    source = source,
    warp = true,
    keys = true,
    fuel = 90.0,
    plate = FWB.Vehicle.GeneratePlate()
})
```

## Find The Closest Vehicle

```lua
local vehicle = FWB.Entity.Vehicle.Closest({
    maxDistance = 8.0,
    includePlayerVehicle = false
})

if vehicle then
    print(vehicle.plate)
end
```

## Custom Hunger Override

Paste into `unlocked/client.lua`:

```lua
function Override.AddHunger(value)
    TriggerEvent('my_status:add', 'hunger', value)
end

function Override.RemoveHunger(value)
    TriggerEvent('my_status:remove', 'hunger', value)
end
```
