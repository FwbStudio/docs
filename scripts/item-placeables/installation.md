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
# Installation

### **Framework**

* [ESX](https://github.com/esx-framework/esx_core)
* [QBCore](https://github.com/qbcore-framework/qb-core)

### Dependencies

| Resource                                                               | Install  | Description                     |
| ---------------------------------------------------------------------- | -------- | ------------------------------- |
| [fs\_bridge](../fs_bridge/installation.md) | Required | for major important functions   |
| [ox\_lib](https://github.com/overextended/ox_lib)                      | Required | callbacks,notifications         |
| [ox\_target](https://github.com/overextended/ox_target)                | optional | can be changed in unlocked file |

### 1 - Start

```
1. Download your resource from FiveM's Keymaster.
2. Unzip fs_placeables.zip folder and place it into your resource folder.
```

### 2 - Items

{% tabs %}
{% tab title="Ox\_Inventory -template" %}
{% code fullWidth="true" %}

```lua
-- incase u want to use button on item using right click on item
-- button we only supported with ox_inventory currently soon we will 
-- add support for more inventories
 lockpick = {
		label = "Lockpick",
		weight = 10,
		stack = true,
		close = true,
		description = "This is description.",
		buttons = {
			{
				label = "Place on Ground",
				action = function(slot)
					exports.ox_inventory:closeInventory();
					TriggerServerEvent("fs_placeables:placeonground", "lockpick");
				end
			}
		}
	},
```

{% endcode %}
{% endtab %}

{% tab title="Other all inventories" %}
if you are using any other inventory then simply enable menu in config and use that menu to place item on ground anywhere even on vehicles back etc
{% endtab %}
{% endtabs %}

### 3 - Configuration

{% code overflow="wrap" fullWidth="false" %}

```
* You must go through all configuration options & settings in shared/config.lua

* For Multiple Items like if a item need multiple placeable prop in bundles then you can configure config like this.

Config.Items = {
     ['water'] = {
         [number of items] = 'prop that will be used to place these items'
         [1] = `h4_prop_battle_lights_floor_l_b`,
         [2] = `h3_prop_battle_lights_floor_l_b`,
     },
    -- add more items here 
}

you can add as many as props you want with numbeer of certain items 
```

{% endcode %}

### 4 - Is Items stay after restart?

```
No Items don't stay after restrat due to better performance or player spam we currently don't provide persitent items placeable option
```

### 5 - Ready

Congratulations, you've successfully installed the resource. Restart the server and you will be all set.
