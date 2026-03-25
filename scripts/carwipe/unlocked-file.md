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

{% code title="Server Side Unlocked File" lineNumbers="true" fullWidth="true" %}

```lua
function WipeStartNotification()
    -- don't touch if you don't know what u are doing
    GenerateGlobalNotification('A car wipe is coming in 2 minutes.  \n If you don\'t want your car to disappear, sit in it')
    Wait(60000)
    GenerateGlobalNotification('A car wipe is coming in 1 minutes.  \n If you don\'t want your car to disappear, sit in it')
    Wait(15000)
    GenerateGlobalNotification('A car wipe is coming in 45 seconds.  \n If you don\'t want your car to disappear, sit in it')
    Wait(15000)
    GenerateGlobalNotification('A car wipe is coming in 30 seconds.  \n If you don\'t want your car to disappear, sit in it')
    Wait(15000)
    GenerateGlobalNotification('A car wipe is coming in 15 seconds.  \n If you don\'t want your car to disappear, sit in it')
    Wait(5000)
    GenerateGlobalNotification('A car wipe is coming in 10 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 9 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 8 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 7 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 6 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 5 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 4 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 3 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 2 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
    Wait(1000)
    GenerateGlobalNotification('A car wipe is coming in 1 seconds.  \n If you don\'t want your car to disappear, sit in it', 1000)
end


-----------------------------Bottom functions can be used if you are dev and knows lua and want to eidt some thing in script-----------------------------


function CarWipeStarted() --this function run just once when car wipe starts
     
end


--Note:
-- No Help will be provded by us to implement any other script in these function
-- these functions are for help to implement your parking script or your garages incase if u want after wipe that plate should go to garage directly


-- this function run for each vehicle if can wipe certain vehicle or plate
function CanWipeVehicle(vehicle, plate , owned) -- before wiping vehicle must return true or false else will break script
    -- you can run any code here if you need make sure to return true or false
    

    
    --return true means vehicle will be wiped if has no ped in it and not in any zone and not in blacklist {default checks will always applied on vehicle}
    --return false will simply just not wiped vehicle in any sitation and even script will not gonna check any thing else on false
    return true
end


-- this function run for each vehicle before wipe
function BeforeSuccessfullyWiped(vehicle, plate, owned) 
    -- this function wil on before successfully wiping vehicle after this function it will Delete that vehicle then this function will run AfterSuccessfullyWiped
     
end


-- this function run for each vehicle after wipe successfully done
function AfterSuccessfullyWiped(plate, owned) -- this function will only run on after successfully wiping vehicle


end


function CarWipeFinished() -- this function run just once on car wipe finished
   
end

function Notifcation(src, msg, time)
    FWB.Notification(src, {
        description = msg,
        duration = time or 5000,
        icon = 'fa-solid fa-car-burst',
        type = 'error',
        position = 'top',
        style = {
            width = '500px',
            color = 'green',
            ['.description'] = {
                ['font-weight'] = 'bold',
                ['font-size'] = '18px',
                color = 'red',
            }
        },
    })
end
```

{% endcode %}
